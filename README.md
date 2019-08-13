##Iron Ninja

We are going to be revisiting our Hungry Ninja classes and build out a few new classes using Inheritance, Abstract Classes,and Interfaces. First, let's create an interface for things that can be consumed this will include our Food class, but also could be applied to a new Drink class! Our ninjas can now Consume rather than just "Eat". Let's also make Ninja an abstract class that we can branch out into more specific child classes of eaters. One that is partial to "sweets" and one that favors "spicy" things.


**Objectives**

* Build on top of your OOP knowledge
* Get practice working with interfaces 
* Get practice with Abstract Classes
---
**Tasks**

***IConsumable.cs***

Create a the following *IConsumable* interface (code provided), that contains properties for Name, Calories, IsSweet, and IsSpicy, and a method for GetInfo()

```javascript
interface IConsumable
{
    string Name {get;set;}
    int Calories {get;set;}
    bool IsSpicy {get;set;}
    bool IsSweet {get;set;}
    string GetInfo();
}   
```
***Food.cs***

Refactor the former Food class to implement the IConsumable interface (code provided)
```javascript
class Food : IConsumable
{
    public string Name {get;set;}
    public int Calories {get;set;}
    public bool IsSpicy {get;set;}
    public bool IsSweet {get;set;}
    public string GetInfo()
    {
        return $"{Name} (Food).  Calories: {Calories}.  Spicy?: {IsSpicy}, Sweet?: {IsSweet}";
    }
    public Food(string name, int calories, bool spicy, bool sweet)
    {
        Name = name;
        Calories = calories;
        IsSpicy = spicy;
        IsSweet = sweet;
    }
}   
```
***Drink.cs***

Create a Drink class that implements the IConsumable interface. Make sure Drink objects are always sweet.

```javascript
class Drink : IConsumable
{
    public string Name {get;set;}
    public int Calories {get;set;}
    public bool IsSpicy {get;set;}
    public bool IsSweet {get;set;}
    
    // Implement a GetInfo Method
    // Add a constructor method
}   
```
***Ninja.cs***

Convert Ninja to an abstract class. Child classes of Ninja should determine when they are full, and how they eat - or rather *consume*, as we now have both Food and Drink. (code provided)
```javascript
abstract class Ninja
{
    protected int calorieIntake;
    public List<IConsumable> ConsumptionHistory;
    public Ninja()
    {
        calorieIntake = 0;
        ConsumptionHistory = new List<IConsumable>();
    }
    public abstract bool IsFull {get;}
    public abstract void Consume(IConsumable item);
}
```
***SweetTooth.cs***

Make a child class of Ninja, for a SweetTooth. A SweetTooth should be "full" at 1500 calories. When a SweetTooth "Consumes":

_If NOT Full_

  * adds calorie value to SweetTooth's total calorieIntake (+10 additional calories if the consumable item is "Sweet")
  * adds the randomly selected IConsumable object to SweetTooth's ConsumptionHistory list
  * calls the IConsumable object's GetInfo() method

_If Full_

  * issues a warning to the console that the SweetTooth is full and cannot eat anymore
```javascript
class SweetTooth : Ninja
{
    // provide override for IsFull (Full at 1500 Calories)
    public override void Consume(IConsumable item)
    {
        // provide override for Consume
    }
}
```
***SpiceHound.cs***

Make a child class of Ninja, for a SpiceHound. A SpiceHound should be "full" at 1200 calories. When a SpiceHound "Consumes":

_If NOT Full_

* adds calorie value to SpiceHound's total calorieIntake (-5 additional calories if the consumable item is "Spicy")
* adds the randomly selected IConsumable object to SpiceHound's ConsumptionHistory list
* calls the IConsumable object's GetInfo() method

_If Full_

* issues a warning to the console that the SpiceHound is full and cannot eat anymore
```javascript
class SpiceHound : Ninja
{
    // provide override for IsFull (Full at 1200 Calories)
    public override void Consume(IConsumable item)
    {
        // provide override for Consume
    }
}
```
---
##Complete The Following:

* [ ] Build out the IConsumable interface as specified
* [ ] Build out the Food, Drink, Ninja, SweetTooth, and SpiceHound classes as specified
* [ ] Revisit the Buffet class to contain a Menu of IConsumables, and add a few Drinks to the Menu
* [ ] In your Program's Main method: instantiate a Buffet, a SweetTooth, and a SpiceHound.
* [ ] In your Program's Main method: have both the SweetTooth and Spice hound "Consume" from the Buffet until Full.
* [ ] In your Program's Main method: write to the console which of the two consumed the most items and the number of items consumed.