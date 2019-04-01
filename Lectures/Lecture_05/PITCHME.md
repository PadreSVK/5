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
| **Horrible hack**  |  **Horrible hack that I didn't write** |
| Temporary workaround |  Horrible hack that I wrote |
| **It's broken**  | **There are bugs in your code** |
| It has a few issues | There are bugs in my code |
| **Obscure** | **Someone else's code doesn't have comments** |
| Self-documenting | My code doesn't have comments |
| **Bad structure** | **Someone else's code is badly organised** |
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


---
### (Told || Wrote) about Clean Code

@snap[midpoint span-100]

*Any **fool** can write code that a computer can understand. Good programmers write code that **humans** can understand.*  
 Martin Fowler  
<br>

*Clean code **is simple and direct**. **Clean code reads like well-written prose**. Clean code never obscures the designers’ intent but rather is full of crisp abstractions and straightforward lines of control.*  
  Grady Booch  
<br>

*If you want your code to be **easy to write**, make it **easy to read**.*  
  Robert C. Martin

@snapend


---
### Eagleson's law
@snap[midpoint]  

"Any code of your own that you haven't looked at for six or more months might as well have been written by someone else."  

@snapend

---
### Clean Code Measurement
@snap[midpoint]
![](/Lectures/Lecture_05/Assets/img/clean-code-measurement.jpg)
@snapend

---
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

---
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

---
### Clean Code - Readability
  * **Create short straightforward functions**
    * Is easy to test
    * No side effects
  * **Avoid mutate value of variable too often**
  * Ration between write and read code is 1:10
  * **Avoid more (>2) return statements from method**
    * This method have lower *Maintainability index*
    * It is prerequisite for higher *Cyclomatic complexity* (consequence of more linearly independent paths through our method (too much if-else of switch-es statements))

![](/Lectures/Lecture_05/Assets/img/CodeComplexity.png)

+++
### Avoid more (>2) return statements from method
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
@[7,11-14]
@[7-10]
@[1-25]

+++
### Avoid more (>2) return statements from method
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
@[1-2]
@[3-7]
@[9-12]
@[13-14]
@[1-14]

---
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

---
## Solid principles

* 5 principles that is observed from real life development
* Is subset of principles promoted by Robert C. Martin
* These principles are heuristics
* They are common-sense solutions to common problems
* Designed for object oriented paradigm
* Principles is originally related to class design

*The SOLID principles are **not rules**. **They are not laws**. They are not perfect truths. The **are statements** on the order of “An apple a day keeps the doctor away.” This is a good principle, it is good advice, but it’s not a pure truth, nor is it a rule.*  
*source: [Robert C. Martin, Getting a SOLID start](https://sites.google.com/site/unclebobconsultingllc/getting-a-solid-start)*

---
### SOLID acronym meaning
* **S**ingle responsibility principle
* **O**pen/Closed principle
* **L**iskov substitution principle
* **I**nterface segregation
* **D**ependency inversion principle

---
### Solid - Single responsibility principle
* Talking about class, interface, method (all those will be refer as "code")
* Code should have single straightforward role with single responsibility
* Code should have one, and only one, reason to be changed
* **Big is bad, small is good**
    * Single responsibility doesn't mean single method in class!
* Related with composition over inheritance
    * It si better compose small methods/classes/interfaces like one GOD method/class/interface
 
+++
![](/Lectures/Lecture_05/Assets/img/singleResponsibility.png)

---
### sOlid - Open closed principle

* Author of term is Bertrand Meyer (*Object Oriented Software Construction 1988*)
* Open for extensions, closed for modification
* Robert C. Martin considered this principle as the “the most important principle of object-oriented design”
* It is often misunderstood, it means: *if change your code in expected ways, you don't have to make sweeping changes to all modules in system*
    * In other words: **it should be easy to change the behavior of a module without changing the source code of that module**
* Related to abstraction


+++
![](/Lectures/Lecture_05/Assets/img/openClosedPrinciple.jpg)

---
### soLid - Liskov substitution principle

* Introduced by Barbara Liskov in a 1987
* If *S* is a subtype of *T*, then objects of type *T* may be replaced with objects of type *S*
    * Object type *S* may be substituted by object type *T*
* Right use "is" and "have" relations
    * Right use inheritance and composition
* Child do not change behavior of parent
* A subclass should require nothing more and promise nothing less
* Related to polymorphism

+++
![](/Lectures/Lecture_05/Assets/img/liskovSubstitutionPrinciple.jpg)

---
### solId - Interface segregation principle

* Interface must be simply and straightforward
    * Class can implement multiple interfaces
* Interface shouldn't force client to implement non related methods/properties
* Abstraction should be simply and easy to understand


+++
![](/Lectures/Lecture_05/Assets/img/interfaceSegregationPrinciple.jpg)


---
### soliD - Dependency inversion principle

* Dependence on abstraction, not on concrete implementation
* Allows reuse code in proper way
* High-level modules should not depend on low-level modules. Both should depend on abstractions
* Abstractions should not depend upon details. Details should depend upon abstractions.
* Overleap with Open Closed principles and Liskov substitution principle, but is more general


*In this column, we discuss the structural implications of the OCP and the LSP. The structure that results from rigorous use of these principles can be generalized into a principle all by itself. I call it “The Dependency Inversion Principle” (DIP).*  
*source: [Robert C. Martin, OCP: The Open-Closed Principle](https://www.goodreads.com/book/show/26091039-ocp)*

+++
![](/Lectures/Lecture_05/Assets/img/dependencyInversionPrinciple.jpg)


+++
![](/Lectures/Lecture_05/Assets/img/dependencyInversionPrinciple2.jpg)


---
### Solid - in short

* **S** - class/method have one responsibility
* **O** - class should be open for modification and closed for modification
* **L** - right use of inheritance and composition
* **I** - create more simple interfaces
* **D** - dependence on abstraction, not on concrete implementation 
