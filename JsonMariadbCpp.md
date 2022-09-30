
# Simple Example of C++ with nlohmann::json and Mariadb C++ connector
In this article, nlohmann::json and mariadb C++ connector are used together with C++ to read an input json file, parse the data of the file and then insert it into a database.
## Set up the development environment
The development environment is Ubuntu 22.04.1 LTS which is installed on virtual box.
To be able to use nlohmann::json on Ubuntu, it is needed to be installed by 
```$ sudo apt-get install nlohmann-json3-dev```
To be able to use mariadb C++ connector (mariadb/conncpp.hpp) on Ubuntu, it is needed to download the C++ connector and install it following the commands from the link provided in refernces for install.
To be able to build the C++ application, you need to link it with Mariadb connector:
``` $ g++ -o example example.cpp -std=c++11 -lmariadbcpp ```

The final cooked command to build the application and run it is:
```
$ g++/ clang++ -Wall -Wextra -Werror database.cpp json.cpp main.cpp -o readJsonWithCppInsertIntoDB  -lmariadbcpp -lmysqlcppconn
$ ./readJsonWithCppInsertIntoDB
```

## Login to an already existing database named 'test' and see the table named 'person'
```
  $ sudo mysql -u root
  MariaDB [(none)]> use test;
  MariaDB [test]> SELECT * FROM person;
```
## Input file
The input of this C++ application is an already existing json file (input.json)
```
{
    "employees": [
        {
            "address": {
                "city": "Prague",
                "number": 22,
                "street": "Jeferson"
            },
            "age": 25,
            "id": 69,
            "name": "Eli",
            "salary": {
                "currency": "USD",
                "value": 1000
            },
            "title": "dev"
        },
        {
            "address": {
                "city": "Istanbul",
                "number": 33,
                "street": "Oak"
            },
            "age": 35,
            "id": 55,
            "name": "Angela",
            "salary": {
                "currency": "USD",
                "value": 2000
            },
            "title": "dev"
        },
        {
            "address": {
                "city": "Venice",
                "number": 101,
                "street": "Riverside"
            },
            "age": 45,
            "id": 101,
            "name": "Tom",
            "salary": {
                "currency": "USD",
                "value": 3000
            },
            "title": "dev"
        },
        {
            "address": {
                "city": "Athens",
                "number": 88,
                "street": "Montgomery"
            },
            "age": 55,
            "id": 77,
            "name": "Jerry",
            "salary": {
                "currency": "USD",
                "value": 4000
            },
            "title": "dev"
        }
    ]
}
```
## Class structure
The design of the application consists of 2 classes, DataBase and JsonFile dividing the representations and functionality related to file operations and database operations.
### DataBase class
```
#pragma once

#include <memory>

#include <mariadb/conncpp.hpp>
#include <mariadb/conncpp/Driver.hpp>

class DataBase
{
public:
  DataBase(const sql::SQLString& url,  sql::Properties& properties)
  {
    sql::Driver* driver = sql::mariadb::get_driver_instance();
    if(driver == nullptr)
    {
      std::cout << "driver is null" << std::endl;
      return;
    }

    auto* connection = driver->connect(url, properties);
    if(connection == nullptr)
    {
      std::cout << "connection is null" << std::endl;
      return;
    }
  
    m_connection.reset(connection);
  }

  void mysqlExecuteQuery(std::string& sqlQuery);
  bool isThereConnection();

private:
  std::unique_ptr<sql::Connection> m_connection; 
};
```
```
#include <string>
#include <memory>
#include <iostream>

#include "database.hpp"

void DataBase::mysqlExecuteQuery(std::string& sqlQuery)
{
  std::unique_ptr<sql::PreparedStatement> statement(m_connection->prepareStatement(sqlQuery));
  statement->executeQuery();
}

bool DataBase::isThereConnection()
{
  return m_connection != nullptr;
}
```
### JsonFile class
```
#pragma once

#include <vector>
#include <nlohmann/json.hpp>

#include "database.hpp"

struct Address
{
  std::string city;
  int number;
  std::string street;
};

struct Salary
{
  std::string currency;
  int value;
};

struct Employee
{
  int id;
  std::string name;
  int age;
  Address address;
  std::vector<std::string> children;
  Salary salary;
  std::string title;
};

class JsonFile
{
public:
  JsonFile(DataBase& db)
    : m_database(db)
  {
    std::cout << " ------------------- JsonFile(const DataBase& db) ------------------- " << std::endl;
  }
  
  std::vector<Employee> parseJsonFile(const std::string& inputFilePath); 
  void addJsonFileToDataBase(const std::vector<Employee>& employees);

private:
  DataBase& m_database;
  nlohmann::json m_jsonObjectFromFile;
};
```
```
#include <iostream>
#include <fstream>

#include "json.hpp"


std::vector<Employee> JsonFile::parseJsonFile(const std::string& inputFilePath)
{
  std::cout << " ------------------- JsonFile::readJsonFile(path) ------------------- " << std::endl;
  std::ifstream fileToRead(inputFilePath);
  fileToRead >> m_jsonObjectFromFile;
  
  std::vector<Employee> employees;

  for(const auto& emp : m_jsonObjectFromFile["employees"])
  {
    Employee employee;
    employee.id = emp["id"];
    employee.name = emp["name"];
    employee.title = emp["title"];
    employee.age = emp["age"];
    employee.address.city = emp["address"]["city"];
    employee.salary.value = emp["salary"]["value"];
    employee.salary.currency = emp["salary"]["currency"];
    employees.push_back(employee);
  }

  return employees;
}

void JsonFile::addJsonFileToDataBase(const std::vector<Employee>& employees)
{
  std::cout << " ------------------- JsonFile::addJsonFileToDataBase() ------------------- " << std::endl;
  if(! m_database.isThereConnection())
  {
    std::cout << "there is no connection to the database.. no command to be sent" << std::endl;
    return;
  }
 
  for(const auto& employee: employees)
  {
    std::string command = "INSERT INTO person (id, name, title, age, city, salary, currency) VALUES ('";
    command += std::to_string(employee.id) + "', '"
            + employee.name + "', '"
            + employee.title + "', '"
            + std::to_string(employee.age) + "', '"
            + employee.address.city + "', '"
            + std::to_string(employee.salary.value) + "', '"
            + employee.salary.currency + "');";


    m_database.mysqlExecuteQuery(command);
  }
}
```
### Entry point of the application
```
#include <string>
#include <iostream>
#include <fstream>

#include "database.hpp"
#include "json.hpp"

int main()
{
  std::cout << "--------------- opening conenction to database: ---------------" << std::endl;
  const sql::SQLString& url = "jdbc:mariadb://localhost:3306/test";
  sql::SQLString user = "root2";
  sql::SQLString password = "";
  sql::Properties prop  {{"user", user}, {"password", password}};
  
  DataBase testDatabase(url, prop);

  
  testDatabase.isThereConnection();

  JsonFile jsonFile(testDatabase);
  std::cout << "--------------- reading json file: ---------------" << std::endl;
  const std::string& filePath = "input.json";
  auto fileData = jsonFile.parseJsonFile(filePath);

  std::cout << "--------------- adding the content of json file to database: ---------------" << std::endl;
  jsonFile.addJsonFileToDataBase(fileData);

  std::cout << "--------------- closing conenction to database: ---------------" << std::endl;

  return 0;
}
```
### Demo!
![image](https://user-images.githubusercontent.com/17904210/193254895-859655d9-eaea-410c-83c3-ec35f70d42f2.png)

## Summary
As you see in the Demo! photo, an empty table in a database is filled with the data parsed from a json file.

# Reference:
* https://www.youtube.com/watch?v=cSZvq7Kv6_0
* https://github.com/nlohmann/json/issues/1703
* https://mariadb.com/docs/connect/programming-languages/cpp/install/
* https://mariadb.com/docs/connect/programming-languages/cpp/development/
* https://github.com/nlohmann/json/blob/develop/docs/examples/README.cpp
* https://mariadb.com/docs/connect/programming-languages/cpp/
* https://mariadb.com/downloads/connectors/
* https://stackoverflow.com/questions/3202136/using-g-to-compile-multiple-cpp-and-h-files
* https://stackoverflow.com/questions/16710047/usr-bin-ld-cannot-find-lnameofthelibrary
* https://stackoverflow.com/questions/36679189/how-to-find-mysql-ip-on-localhost 
* https://mariadb.com/resources/blog/how-to-connect-c-programs-to-mariadb/
