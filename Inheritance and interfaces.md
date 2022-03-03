# Inheritance and Interfaces

Lecture notes link: http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Interfaces/

# Interfaces
An Interface is a class that only contains virtual methods
Example:
```
class Item {
  public:
    virtual ~Item() {};
    virtual string Description() const = 0;
    virtual double Price() const = 0;
    virtual double Expenses() const = 0;
};
```

An interface in C++ is a restricted subset of inheritance that is not supported explicitly by the language. With an interface you define a class which will contain a bunch of subclasses. The subclasses will each implement methods that correspond to methods that the interface defines. 

You'll note, the interface implements nothing -- it merely specifies the methods that each of the subclasses will implement. 

An interface shouldn't contain variables, and it shouldn't contain code. It merely contains prototypes.

In the Etsy store example from the lecture notes, interfaces are useful for adding new items to the store.


## Interface Test Question
>Explain in your own words what an interface is, and why it is a useful concept in a language like C++ (Even though C++ doesn't formally have an interface, you can view it as a restricted subset of inheritance).

- an interface defines the prototypes of methods that a class may implement. If a class implements those, then the class may "belong" to the interface, and then one may program with an instance of the interface, and it will work with all classes that belong to the interface.


## More code examples

**Dog** and **Koozie** are two differnt classes that both are using the interface **Item**

```
class Dog : public Item {
  public:
    Dog(istringstream &ss);
    string Description() const;
    double Price() const;
    double Expenses() const;
  protected:
    string color;
    string size;
    double yards;
    double price;
};
class Koozie : public Item {
  public:
    Koozie(istringstream &ss);
    string Description() const;
    double Price() const;
    double Expenses() const;
  protected:
    string color;
    string monogram;
    double yards;
    double price;
};

```
In the main code, we no longer declare the **Dog** or **Koozie** pointers. Instead, we simply declare a pointer to an **Item**:
```
int main()
{
  Item *i;           // No longer do we have separate Dog / Koozie pointers.
  istringstream ss;
  ...
}
```
Now, when we create an instance of Dog or Koozie, We can just make a pointer to the **Item**
and use simple if statements to determine which method, **dog** or **koozie**, to call 
```
while (getline(cin, line)) {
    ss.clear();
    ss.str(line);
    ss >> key;
    if (key == "Koozie") {          // Here is the relevant code.
      i = new Koozie(ss);           // Since Koozie/Dog implement the 
    } else if (key == "Dog") {      // Item interface, we can treat 
      i = new Dog(ss);              // them as items.
    }
    desc = i->Description();        // Now there is no code duplication.
    price = i->Price();
    expense = i->Expenses();
    delete i;

    tp += p;
    te += e;
    printf("%-60s %6.2lf %6.2lf\n", desc.c_str(), p, e);
  }
```


# Inheritance


Inheritance allows you to set up an arbitrarily complex hierarchy of methods, variables and virtual methods. The main class (superclass) contains all three of these things, and then any subclass that is derived from the superclass "inherits" the methods and variables and may use them as if they belong to the superclass. A pointer to a subclass may be treated as a pointer to the superclass.



From lecture notes, you are able to use inheritance in the etsy store program to make multiple items with the same shared variables like color yards and prices without having to have repeated code