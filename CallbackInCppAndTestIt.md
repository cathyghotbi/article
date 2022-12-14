# Implement and test callbacks in C++ and gmock

In this article we implement the concept of callback in C++, also use gmock for a way to test our code.
Callbacks exit in real life, you call someone, they can not answer at that moment for any reason, you request for a callback so that they call you in a later time.

C++ has some Callables: functions, lambda expressions, bind expression, function objects and function pointers.
There is also a class template std::function which is a general-purpose function wrapper which can store, copy and invoke any Callable.
std:function is often used to pass callbacks.
```
void callMeBack(int x)
{
  std::cout << x << std::endl;
}

void func(std::function<void(int)> callback)
{
  int knownValueAtThisPoint = 11;
  callback(knownValueAtThisPoint);
}

int main() 
{
  std::function<void(int)> callLater = callMeBack;
  callLater(5);

  func(callLater);
  return 0;
}
```
There are two types of callbacks, blocking ones (synchronous) and deferred ones (asynchronous). 
Difference is blocking ones are called before the caller function returns so the caller actually waits for them to finish their job.
A simple example of std::fucntion below:
As an example of blocking/synchronous callback:
```
void doSomething(std::function<void()> task)
{
  task();
}
```
and as an example of deferred/ asynchronous callback:
```
class User
{
  User(std::function<void()> task)
  : m_task(task)
  {
  }
  
  void doSomething()
  {
    m_task();
  }

private:
  std::function<void()> m_task;
};
```
Now, lets look into how std::function can be tested using gmock.
To mock std::function in tests, gmock provides MockFunction.
First you need to create MockFunction object, obtain a std::fucntion proxy to Call from AsStdFucntion(), 
then setup expectation on its Call method and pass the obtained proxy to the test.  

Below there is an example of the std::funciton and MockFunction in a unit test:
```
#include <gtest/gtest.h>
#include <gmock/gmock.h>
//---------------------------------------------------------------------------------------------------------
class User
{
public:
  User(std::function<void()> futureTask)
  : m_futureTask(futureTask)
  {
  }

  void userAction()
  {
    m_futureTask();
  }

private:
  std::function<void()> m_futureTask;
};
//---------------------------------------------------------------------------------------------------------
using ::testing::_;
using ::testing::MockFunction;

class UserTest : public ::testing::Test
{
public:
  UserTest()
  {
    m_user.reset(new User(m_mockFutureTask.AsStdFunction()));
  }

protected:
  std::unique_ptr<User> m_user;
  MockFunction<std::function<void()>> m_mockFutureTask;
};

TEST_F(UserTest, testfutureTask)
{
  EXPECT_CALL(m_mockFutureTask, Call());

  m_user->userAction();
}
//---------------------------------------------------------------------------------------------------------
int main()
{
  ::testing::InitGoogleTest();
  return RUN_ALL_TESTS();
}
//---------------------------------------------------------------------------------------------------------
```
This simple example shows how MockFunction can be used in a handy way to mock std::function for testing purposes.

# References
* https://en.wikipedia.org/wiki/Callback_(computer_programming)
* https://en.cppreference.com/w/cpp/utility/functional/function
* http://google.github.io/googletest/gmock_cook_book.html#MockFunction
