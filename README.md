# Signs you should probably refactor

1.	You have a method that accepts more than 2 parameters
2.	You have public methods not implementing an interface
3.	You are using inheritance
4.	You are only using a portion of an arguments members
5.	You don't have null checks as the first line(s) in a public method
6.	You have a switch statement
7.	You are using the else keyword
8.	You have an enum
9.	You have a method with more than 5 lines of code
10.	You have a class with more than 50 lines of code
11.	You are calling a member of a member (i.e.  myObject.Property.ChildProperty)
12.	You have a class that has to implement IDisposable

## You have a method that accepts more than 2 parameters

#### Example
 ```csharp
 void AddUser(string username, string password, int age)
 ```
#### Why is this bad? 
1. Logically we should be adding a user object
2. If we add another parameter we break the interface and will be forced to change all of the calling code
3. Required number of unit tests for argument exceptions is a multiple of the number of parameters
 
#### Resolved
```csharp
void AddUser(User userToAdd)

class User
{
  public string Username { get; set; }
  public string Password { get; set; }
  public int Age { get; set; }
}
```
