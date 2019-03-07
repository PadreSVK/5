@snap[north span-100]
# Clean Code and SOLID principles
@snapend

@snap[midpoint span-100]
## How to write maintainable code (Clean Code, SOLID), Refactorization
@snapend

@snap[south-east span-60]
[ Patrik Švikruha <patrik.svikruha@vutbr.cz> ]
@snapend

---
## What Programmers Say

|  What Programmers Say |  What Programmers Mean |
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


<ul class="span-80">
    <li>
    **Clean code is set advices for writing code**
    </li>
    <li>
    **Clean code in general is code that:**
    </li>
    <li>
    <ul>
        <li>
        *Is readable (consistent naming conventions, meaningful names of variables and functions)*
        </li>
        <li>
        *Is easy to understand (straightforward flow of code)*
        </li>
        <li>
        *Is easy to extend (add new functionality doesn't mean rewrite whole aplication)*
        </li>
    </ul>
    <li>
    [Clean Code Book](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
    </li>
    <li>
    [Clean Code .NET](https://github.com/thangchung/clean-code-dotnet)
    </li>
    <li>
    **Exact definition may be very subjective**
    </li>
</ul>

@snap[north-east]
@img[span-35](/Lectures/Lecture_05/Assets/img/clean-code.jpg)
@snapend

+++
### (Told || Wrote) about Clean Code

@snap[midpoint span-100]

*Any **fool** can write code that a computer can understand. Good programmers write code that **humans** can understand.*  
  — Martin Fowler  


*Clean code **is simple and direct**. **Clean code reads like well-written prose**. Clean code never obscures the designers’ intent but rather is full of crisp abstractions and straightforward lines of control.*  
  — Grady Booch  


*If you want your code to be **easy to write**, make it **easy to read**.*  
  — Robert C. Martin

@snapend
+++
### Clean Code Measurement
@snap[midpoint]
![](/Lectures/Lecture_05/Assets/img/clean-code-measurement.jpg)
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

* Avoid synonyms (Info, Data, Information), be consistent
* Consistent naming conventions
* **Avoid using magic constants**
* Avoid hungarian notation
* Avoid disinformation name

```C#
 // unify naming in project
string ProductInfo; string ProductData;

// use consistent naming convetions
private DateTime date_of_birth; private DateTime DATEOFBIRTH;

// avoid Magic constants
if(numberOfConnection <= 15)
if(numberOfConncetion <= DEFAULT_NUMBER_OF_CONNECTION)
    
//avoid hungarian notation
int nAgeOfPerson; int ageOfPerson;

//avoid disinformation name
private void Getage() // get prefix and void return type??
private int GetAge()

```
@[1-2]
@[4-6]
@[7-9]
@[11-12]
@[14-16]
@[1-16]

+++
### Clean Code - Readability
  * **Create short straightforward functions**
    * Is easy to test
    * No side effects
  * **Avoid mutate value of variable too often**
  * **Avoid more (>=2) return statements from method**

![](/Lectures/Lecture_05/Assets/img/CodeComplexity.png)


+++
### Avoid more (>=2) return statements from method
```C#
public long Fibonacci(int index)
{
    if (index < 50)
    {
        if (index != 0)
        {
            if (index != 1)
            {
                return Fibonacci(index - 1) + Fibonacci(index - 2);
            }
            else
            {
                return 1;
            }
        }
        else
        {
            return 0;
        }
    }
    else
    {
        throw new System.ArgumentOutOfRangeException();
    }
}
```
@[1-2]
@[3-4]
@[20-24]
@[5-6,15-19]
@[7-14]
@[1-25]

+++
### Avoid more (>=2) return statements from method
```C#
public long Fibonacci(int index)
{
    //first check if have all arguments expected format / value
    if (index > 50)
    {
        throw new System.ArgumentOutOfRangeException();
    }

    if (index == 0 || index == 1)
    {
        return index;
    }

    return Fibonacci(index - 1) + Fibonacci(index - 2);
}
```
@[1-2,13-14]
@[3-7]
@[9-12]
@[1-14]

+++
###  Common Clean code rules

* **Meaningful naming**
    * Name (function || variable) to reflect what we want to do
* **Consistent naming conventions**
    * Use XYZcase, but consistently
* **Do not mutate value of variable too often**
    * Difficult debugging and difficult to understand
* **Create short straightforward functions**
    * Easy testing, easy debugging, easy to understand
* **Write code, that will be read like well-written prose**

@[13-14]
@[16-18]
@[1-18]

+++
### Clean Code - Readability

 * **Meaningfully naming** - pronounceable names (function || variable)    
  * Consistent naming conventions
  * **Avoid using magic constants**
  * Avoid synonyms
  * **Avoid mutate value of variable too often**
  * Proper use of closures
  * Create short straightforward functions

