@snap[north span-100]
# Clean Code and SOLID principles
@snapend

@snap[midpoint span-100]
## How to write maintainable code (Clean Code, SOLID), Refactorization
@snapend

@snap[south-east span-40]
[ Patrik Švikruha <patrik.svikruha@vutbr.cz> ]
@snapend

---
## What Programmers Say

|  What Programmers Say |  What Programmers Mean
|---|---|
| Horrible hack  |  Horrible hack that I didn't write |
| Temporary workaround |  Horrible hack that I wrote |
| It's broken  | There are bugs in your code |
| It has a few issues | There are bugs in my code |
| Obscure | Someone else's code doesn't have comments |
| Self-documenting | My code doesn't have comments |
| Bad structure | Someone else's code is badly organised |
| Complex structure | My code is badly organized |

---
## Clean code

* **Clean code is set advices for writing code**
* **Clean code in general is code that:**
  * *Is readable (consistent naming conventions, meaningful names of variables and functions)*
  * *Is easy to understand (straightforward flow of code)*
  * *Is easy to extend (add new functionality doesn't mean rewrite whole aplication)*
* [Clean Code Book](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
* [Clean Code .NET](https://github.com/thangchung/clean-code-dotnet)
* **Exact definition may be very subjective**

@snap[east]
@img[span-60](/Lectures/Lecture07/Assets/img/clean-code.jpg)
@snapend

+++
### (Told || Wrote) about Clean Code

@snap[midpoint span-100]

* *Any **fool** can write code that a computer can understand. Good programmers write code that **humans** can understand.*  
  — Martin Fowler
* *Clean code **is simple and direct**. **Clean code reads like well-written prose**. Clean code never obscures the designers’ intent but rather is full of crisp abstractions and straightforward lines of control.*  
  — Grady Booch
* *If you want your code to be **easy to write**, make it **easy to read**.*  
  — Robert C. Martin

@snapend**
+++
### Clean Code Measurement
@snap[midpoint]
![](/Lectures/Lecture07/Assets/img/clean-code-measurement.jpg)
@snapend

+++
### Clean Code - Readability

* **Readability means**  
  * **Meaningfully naming** - pronounceable names (function || variable)
  * *Length is not a virtue in a name; clarity of expression is.* — Rob Pike
```C#
int dafbi; // what is the meaning of this acronym?
for(var the_element_inArray_index=0; the_element_inArray_index < myArray.Length; the_element_inArray_index++) // hmmmm...
DateTime genymdhms;
public DateTime Modymdhms {get;set;}

// it is better?
int dayOfBirth;
for(var i=0; i<myArray.Length;i++)
DateTime generationTimestamp;
public DateTime ModificationTimestamp {get;set;}
```
@[1-4]
@[1,6,7]
@[2,6,8]
@[3,6,9]
@[4,6,10]
@[1-10]

+++
### Clean Code - Readability

* Avoid synonyms
* Consistent naming conventions
* **Avoid using magic constants**
* Avoid hungarian notation
* Avoid disinformation name

```C#
 // unify naming in project
string ProductInfo;
string ProductData;

// use consistent naming convetions
private DateTime date_of_birth;
private DateTime DATEOFBIRTH;

// avoid Magic constants
if(numberOfConnection <= 15)
    //....
if(numberOfConncetion <= DEFAULT_NUMBER_OF_CONNECTION)
    //...
    
//avoid hungarian notation
int nAgeOfPerson;
int ageOfPerson;

//avoid disinformation name
private void Getage() // get prefix and void return type??
private int GetAge()

```
@[1-3]
@[5-7]
@[9-13]
@[15-17]
@[19-21]
@[1-21]

+++
### Clean Code - Readability

 * **Meaningfully naming** - pronounceable names (function || variable)
    * *Length is not a virtue in a name; clarity of expression is.* — Rob Pike
  * Consistent naming conventions
  * **Avoid using magic constants**
  * Avoid synonyms
  * **Avoid mutate value of variable too often**
  * Proper use of closures
  * Create short straightforward functions

