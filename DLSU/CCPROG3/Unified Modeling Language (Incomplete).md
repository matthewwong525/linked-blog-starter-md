- Versatile modeling language used across various domains. Primary purpose is to provide a standardized method for visualizing the design of a system.

- It's like a blueprint in traditional engineering disciplines, UML offers graphical representation of a system architecture. It's not a programming language and it is a visual tool for system design.

- Relationship among entities in an architecture.


## Class
- a blueprint for creating objects.
- represents entities with attributes (data) and methods (behavior).

## Components of a Class

| Class Name        | Attributes                      | Methods                            |
| ----------------- | ------------------------------- | ---------------------------------- |
| Centered and bold | Variables that define the state | Functions that define the behavior |
## Visibility and Modifiers

| Public            | Private                         | Default                            | Protected |
| ----------------- | ------------------------------- | ---------------------------------- | --------- |
| Centered and bold | Variables that define the state | Functions that define the behavior |           |

## Relationship between Classes

| Association       | Multiplicity                                           | Aggregation                        | Composition |     |     |
| ----------------- | ------------------------------------------------------ | ---------------------------------- | ----------- | --- | --- |
| Centered and bold | number of occurrences in relationships between classes | Functions that define the behavior |             |     |     |


## Class Diagram Relationships
![[Pasted image 20250603092723.png]]

## Association and Multiplicity
Association: Line between classes
Multiplicity: 

## Aggregation vs Composition
Aggregation: Hollow diamond, parts can exist independently
Composition: Filled diamond, parts cannot exist independently
Example:
- Aggregation

## Inheritance and Dependency
Inheritance: Arrow with hollow triangle
Dependency: Dotted arrow

## Benefits of Class Diagrams
- Clarify system structure

## Drawing Class Diagrams
- Use UML tools (e.g., Lucidchart, StarUML, draw.io)
- Follow naming conventions
- Keep diagrams clean and readable
- Avoid overcomplicating relationships

## Use Cases of Class Diagrams
- Software design and architecture
- Database schema modeling

---

## Class Relationships
Association
Aggregation
Composition

### Classes and Objects
- Objects cannot perform much by themselves, otherwise they become god-objects which violate OOP!
- Objects should interact with each other in order to accomplish complex tasks.

### Association


### Types of Association
1. Directed


---
**June 20, 2025**


	**Association**
	- Bidirectional
	- Reflexive
	
	Aggregation
	Composition
	Inheritance

**Association** - Bidirectional
- Back and forth arrows between classes
- E.g. Both classes have the same method that accepts the instance of the other class as params.

```java
public class Player {
	public void attack(Enemy enemy) {
		enemy.receiveDamage();
	}
}

public class Enemy {
	public void attack(Player player) {
		player.receiveDamage();
	}
}
```

**Association** - Reflexive
- E.g. Relationship to itself. Function has a instance parameter accepting itself 

```java
public class Player {
	private double health;
	private double healAmount;
	
	public void heal(Player player) {
		player.setHealth(player.getHealth() + this.healAmount);
	}

	// ...
}
```

**Aggregation** (Diamond Unshaded) (Weapon part of Character)
- The class has an instance attribute or field and a method accepting that field of another class.
```java
public class Character {
	private Weapon weapon = null;

	public void equip(Weapon weapon) {
		this.weapon = weapon;
	}

	// ...
}

public class Weapon {
	private double attackValue;
	public double getAttackValue() {
		return this.attackValue;
	}
}
```

**Composition** (Diamond Shaded) (Inventory has <> Character)
- E.g. Other instance attribute is instantiated during the current class constructor initialization.
```java
public class Character {
	private Inventory inventory;
	public Character() {
		this.inventory = new Inventory();
	}
}

public class Inventory {
	// ...
}
```


\* = Multiplicity?
1 = 