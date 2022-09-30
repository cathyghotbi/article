
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





# Reference:
* https://github.com/nlohmann/json/issues/1703
* https://mariadb.com/docs/connect/programming-languages/cpp/install/
* https://mariadb.com/docs/connect/programming-languages/cpp/development/
