
# C++ with nlohmann::json and Mariadb C++ connector
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
$ g++ database.cpp json.cpp main.cpp -o readJsonWithCppInsertIntoDB -L/usr/include/mariadb -lmariadbcpp -lmysqlcppconn
$ sudo ./readJsonWithCppInsertIntoDB
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
    "employees": {
        "employee1": {
            "address": {
                "city": "Prague",
                "number": 22,
                "street": "Jeferson"
            },
            "age": 25,
            "children": [
                "Ben",
                "Kimberly",
                "Jack"
            ],
            "id": 69,
            "name": "Eli",
            "salary": {
                "currency": "USD",
                "value": 1000
            },
            "title": "dev"
        },
        "employee2": {
            "address": {
                "city": "Istanbul",
                "number": 33,
                "street": "Oak"
            },
            "age": 35,
            "children": [
                "Robin",
                "Kevin",
                "Adrian"
            ],
            "id": 55,
            "name": "Angela",
            "salary": {
                "currency": "USD",
                "value": 2000
            },
            "title": "dev"
        },
        "employee3": {
            "address": {
                "city": "Venice",
                "number": 101,
                "street": "Riverside"
            },
            "age": 45,
            "children": [
                "Emma",
                "Eva",
                "Eli"
            ],
            "id": 101,
            "name": "Tom",
            "salary": {
                "currency": "USD",
                "value": 3000
            },
            "title": "dev"
        },
        "employee4": {
            "address": {
                "city": "Athens",
                "number": 88,
                "street": "Montgomery"
            },
            "age": 55,
            "children": [
                "Oliver",
                "Emily",
                "Olivia",
                "Sara"
            ],
            "id": 77,
            "name": "Jerry",
            "salary": {
                "currency": "USD",
                "value": 4000
            },
            "title": "dev"
        }
    }
}
```



# Reference:
* https://github.com/nlohmann/json/issues/1703
* https://mariadb.com/docs/connect/programming-languages/cpp/install/
* https://mariadb.com/docs/connect/programming-languages/cpp/development/
