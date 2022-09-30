
# C++ with nlohmann::json and Mariadb C++ connector
In this article, nlohmann::json and mariadb C++ connector are used together with C++ to read an input json file, parse the data of the file and then insert it into a database.
To set up the development environment, Ubuntu 22.04.1 LTS which is installed on virtual box.
To be able to use json on Ubuntu, it is needed to be install by 
```$ sudo apt-get install nlohmann-json3-dev```
To be able to use mariadb C++ connector () on Ubuntu, it is needed to download the connector and install it.


To be able to build the C++ application, you need to link it with Mariadb connector:
``` $ g++ -o example example.cpp -std=c++11 -lmariadbcpp ```


So the final cooked command to build the application and run it is:
```$ g++ database.cpp json.cpp main.cpp -o readJsonWithCppInsertIntoDB -L/usr/include/mariadb/mysql -L/usr/include/mariadb -lmariadbclient -lmariadbcpp -lmysqlcppconn```
```sudo ./readJsonWithCppInsertIntoDB```






# Reference:
* https://github.com/nlohmann/json/issues/1703

* https://mariadb.com/docs/connect/programming-languages/cpp/development/
