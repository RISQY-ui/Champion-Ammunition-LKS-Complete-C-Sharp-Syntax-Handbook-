# Complete C# Syntax Handbook - LKS Competition Ammunition for Faris

---

## 📋 Table of Contents

- [1. Variables & Data Types](#1-variables--data-types)
- [2. Variable Declaration](#2-variable-declaration)
- [3. Type Casting (Data Conversion)](#3-type-casting-data-conversion)
- [4. Operators](#4-operators)
- [5. Conditional Statements (IF, ELSE, SWITCH)](#5-conditional-statements-if-else-switch)
- [6. Looping (For, While, Foreach)](#6-looping-for-while-foreach)
- [7. Arrays](#7-arrays)
- [8. List (Dynamic Array)](#8-list-dynamic-array)
- [9. Dictionary (Key-Value)](#9-dictionary-key-value)
- [10. String Operations](#10-string-operations)
- [11. Random Numbers](#11-random-numbers)
- [12. Methods (Functions)](#12-methods-functions)
- [13. Classes & Objects](#13-classes--objects)
- [14. Exception Handling (Try-Catch)](#14-exception-handling-try-catch)
- [15. Enum (Constant Data)](#15-enum-constant-data)
- [16. DateTime (Date & Time)](#16-datetime-date--time)
- [17. File I/O (Read & Write Files)](#17-file-io-read--write-files)
- [18. SQL Server Database Connection](#18-sql-server-database-connection)
- [19. Quick Reference Summary](#19-quick-reference-summary)

---

## 1. Variables & Data Types

| Data Type | Keyword | Range / Size | Example |
|-----------|---------|--------------|---------|
| Integer (whole number) | `int` | -2M to 2M | `int level = 5;` |
| Unsigned Integer (positive only) | `uint` | 0 to 4M | `uint score = 1000;` |
| Byte (very small) | `byte` | 0 to 255 | `byte exp = 50;` |
| Short Integer | `short` | -32,768 to 32,767 | `short lives = 3;` |
| Long Integer (very large) | `long` | very large | `long gold = 9999999;` |
| Decimal (single precision) | `float` | 6-7 digits | `float speed = 5.5f;` |
| Decimal (double precision) | `double` | 15-16 digits | `double damage = 99.9;` |
| Decimal (financial/precise) | `decimal` | 28-29 digits | `decimal price = 10000m;` |
| Text / String | `string` | up to 2GB | `string name = "Faris";` |
| Single Character | `char` | one letter | `char grade = 'A';` |
| Boolean (true/false) | `bool` | true or false | `bool isAlive = true;` |
| Date & Time | `DateTime` | year 1-9999 | `DateTime now = DateTime.Now;` |

### Code Examples

```csharp
int playerLevel = 10;
float playerSpeed = 5.5f;
double playerDamage = 99.9;
string playerName = "Faris The Legend";
bool isAlive = true;
DateTime gameStartTime = DateTime.Now;
decimal totalGold = 50000.50m;
```

---

## 2. Variable Declaration

### Method 1: Declare Then Assign

```csharp
int experience;
experience = 100;
```

### Method 2: Declare and Assign Immediately

```csharp
int health = 100;
string playerName = "Faris";
```

### Method 3: Multiple Variables at Once

```csharp
int x = 10, y = 20, z = 30;
string firstName = "Faris", lastName = "The Gamer";
```

### Method 4: Using var (Automatic Type Inference)

```csharp
var level = 5;              // automatically int
var title = "Hero";          // automatically string
var isWin = true;            // automatically bool
var salary = 50000.50m;      // automatically decimal
```

### Method 5: Constants (Fixed Values)

```csharp
const float GRAVITY = 9.8f;
const int MAX_LEVEL = 100;
const string GAME_NAME = "Epic Adventure";
const decimal PLAYER_STARTING_GOLD = 1000m;
```

### Method 6: Nullable Types (Can Be Null)

```csharp
int? playerScore = null;        // can be null
string? middleName = null;      // can be null
double? optionalHealth = null;  // can be null

// Checking nullable
if (playerScore.HasValue)
{
    Console.WriteLine($"Score: {playerScore.Value}");
}

// Using null coalescing operator
int actualScore = playerScore ?? 0;  // 0 if null
```

---

## 3. Type Casting (Data Conversion)

### String to Number (IMPORTANT FOR INPUT)

```csharp
string inputFromTextBox = "100";

// Using Convert class
int damage = Convert.ToInt32(inputFromTextBox);
long bigNumber = Convert.ToInt64(inputFromTextBox);
float speed = Convert.ToSingle("5.5");
double damageDouble = Convert.ToDouble("99.9");
decimal price = Convert.ToDecimal("10000");
bool success = Convert.ToBoolean("true");

// Using Parse method
int number = int.Parse("123");
float numberFloat = float.Parse("12.34");
bool isActive = bool.Parse("true");
```

### Number to String

```csharp
int level = 10;
double health = 75.5;

string levelText = level.ToString();           // "10"
string healthText = health.ToString();         // "75.5"
string hexNumber = 255.ToString("X");          // "FF"
string currencyText = 1000.ToString("C");      // "$1,000.00"
```

### Forced Casting

```csharp
float a = 10.5f;
int b = (int)a;         // b = 10 (decimal lost)

double c = 99.9;
int d = (int)c;         // d = 99

long largeNum = 999999999;
int smallNum = (int)largeNum;  // potential overflow
```

### Safe Parsing (TryParse - Won't Throw Error)

```csharp
string input = "abc123";

// Safe way - won't crash
bool success = int.TryParse(input, out int result);
if (success)
{
    Console.WriteLine($"Number: {result}");
}
else
{
    Console.WriteLine("Invalid input!");
    // result = 0 (default value)
}

// More examples
if (double.TryParse("99.99", out double value))
{
    Console.WriteLine($"Value: {value}");
}

if (bool.TryParse("true", out bool active))
{
    Console.WriteLine($"Active: {active}");
}
```

---

## 4. Operators

### Arithmetic Operators

| Operator | Function | Example | Result |
|----------|----------|---------|--------|
| `+` | Addition | `10 + 5` | 15 |
| `-` | Subtraction | `10 - 3` | 7 |
| `*` | Multiplication | `4 * 5` | 20 |
| `/` | Division | `20 / 4` | 5 |
| `%` | Modulo (remainder) | `10 % 3` | 1 |

```csharp
int baseDamage = 20;
int enemyDefense = 5;
int finalDamage = baseDamage - enemyDefense;  // 15

int totalHealth = 100;
int damagePerSecond = totalHealth / 10;       // 10 damage/sec

int playerExp = 250;
int expPerLevel = 100;
int leftoverExp = playerExp % expPerLevel;    // 50
```

### Increment & Decrement

```csharp
int score = 0;

score++;        // score = 1 (increment by 1)
score--;        // score = 0 (decrement by 1)
score += 5;     // score = 5 (add 5)
score -= 2;     // score = 3 (subtract 2)
score *= 2;     // score = 6 (multiply by 2)
score /= 3;     // score = 2 (divide by 3)
score %= 2;     // score = 0 (remainder of division)

// Pre and post increment
int a = 5;
int b = a++;    // b = 5, then a = 6 (post-increment)
int c = ++a;    // a = 7, then c = 7 (pre-increment)
```

### Comparison Operators (Return bool)

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | true |
| `!=` | Not equal to | `5 != 3` | true |
| `>` | Greater than | `10 > 5` | true |
| `<` | Less than | `3 < 5` | true |
| `>=` | Greater or equal | `5 >= 5` | true |
| `<=` | Less or equal | `3 <= 5` | true |

```csharp
int playerHealth = 50;
int maxHealth = 100;

if (playerHealth == maxHealth)
    Console.WriteLine("Fully healed!");

if (playerHealth < 30)
    Console.WriteLine("Warning: Low health!");

if (playerHealth >= 50)
    Console.WriteLine("Healthy!");

bool isDead = playerHealth == 0;
```

### Logical Operators (Boolean)

| Operator | Meaning | Example |
|----------|---------|---------|
| `&&` | AND (both must be true) | `health > 0 && mana > 0` |
| `\|\|` | OR (at least one must be true) | `isDead \|\| isStunned` |
| `!` | NOT (reverse the value) | `!isDead` |

```csharp
int level = 5;
int exp = 250;

// AND operator - both must be true
if (level >= 5 && exp >= 200)
{
    Console.WriteLine("You can upgrade!");
}

// OR operator - at least one must be true
if (isDead || isStunned)
{
    Console.WriteLine("Cannot attack!");
}

// NOT operator - reverses the boolean
if (!isAlive)
{
    Console.WriteLine("Player is dead");
}

// Complex conditions
if ((playerHealth > 0 && playerMana > 0) || hasPotion)
{
    Console.WriteLine("Can continue fighting!");
}
```

### Assignment Operators

```csharp
int health = 100;

health = 50;        // Simple assignment
health += 10;       // Equivalent to: health = health + 10
health -= 5;        // Equivalent to: health = health - 5
health *= 2;        // Equivalent to: health = health * 2
health /= 4;        // Equivalent to: health = health / 4
health %= 3;        // Equivalent to: health = health % 3
```

---

## 5. Conditional Statements (IF, ELSE, SWITCH)

### Simple IF

```csharp
int playerHealth = 0;

if (playerHealth <= 0)
{
    isAlive = false;
    MessageBox.Show("Game Over! You died.");
}
```

### IF-ELSE

```csharp
int score = 85;

if (score >= 100)
{
    MessageBox.Show("You Win! Perfect score!");
}
else
{
    MessageBox.Show("Try again! Better luck next time.");
}
```

### IF-ELSE IF (Multiple Conditions)

```csharp
int score = 85;
string grade;

if (score >= 90)
{
    grade = "A";
}
else if (score >= 80)
{
    grade = "B";
}
else if (score >= 70)
{
    grade = "C";
}
else if (score >= 60)
{
    grade = "D";
}
else
{
    grade = "F";
}

Console.WriteLine($"Your grade: {grade}");
```

### Switch Case Statement

```csharp
string playerClass = "Warrior";

switch (playerClass)
{
    case "Warrior":
        health = 150;
        damage = 20;
        armor = 10;
        Console.WriteLine("Warrior: High HP and Defense");
        break;
        
    case "Mage":
        health = 80;
        damage = 35;
        mana = 100;
        Console.WriteLine("Mage: High Damage and Mana");
        break;
        
    case "Archer":
        health = 100;
        damage = 25;
        speed = 15;
        Console.WriteLine("Archer: Balanced Stats");
        break;
        
    default:
        health = 100;
        damage = 15;
        Console.WriteLine("Unknown class: Default stats assigned");
        break;
}
```

### Switch with Fall-through

```csharp
int dayOfWeek = 3;
string dayName = "";

switch (dayOfWeek)
{
    case 1:
        dayName = "Monday";
        break;
    case 2:
        dayName = "Tuesday";
        break;
    case 3:
    case 4:
    case 5:
        dayName = "Weekday";  // Falls through for 3, 4, 5
        break;
    case 6:
    case 7:
        dayName = "Weekend";  // Falls through for 6, 7
        break;
    default:
        dayName = "Invalid day";
        break;
}
```

### Ternary Operator (Shorthand IF-ELSE)

```csharp
// Format: condition ? valueIfTrue : valueIfFalse

string status = (health > 0) ? "Alive" : "Dead";
int bonus = (score > 100) ? 50 : 10;
string message = (age >= 18) ? "Adult" : "Minor";

// Nested ternary
string rank = (score >= 90) ? "Excellent" : 
              (score >= 80) ? "Good" : 
              (score >= 70) ? "Average" : 
              "Poor";
```

---

## 6. Looping (For, While, Foreach)

### For Loop (When You Know the Count)

```csharp
// Basic for loop from 0 to 9
for (int i = 0; i < 10; i++)
{
    Console.WriteLine($"Loop iteration: {i}");
}

// Countdown loop
for (int i = 10; i > 0; i--)
{
    Console.WriteLine($"Countdown: {i}");
}

// Loop through array
string[] weapons = { "Sword", "Bow", "Staff", "Dagger" };
for (int i = 0; i < weapons.Length; i++)
{
    Console.WriteLine($"{i + 1}. {weapons[i]}");
}

// Loop with custom increment
for (int i = 0; i <= 100; i += 10)
{
    Console.WriteLine(i);  // 0, 10, 20, 30... 100
}

// Nested loops (for 2D array or pattern)
for (int row = 0; row < 3; row++)
{
    for (int col = 0; col < 3; col++)
    {
        Console.Write($"({row},{col}) ");
    }
    Console.WriteLine();
}
```

### While Loop (When Count is Unknown)

```csharp
int health = 100;

while (health > 0)
{
    health -= 10;
    Console.WriteLine($"Health: {health}");
}
Console.WriteLine("Game Over!");

// While with condition
int attempts = 0;
while (attempts < 3)
{
    Console.Write("Guess the number: ");
    int guess = int.Parse(Console.ReadLine());
    
    if (guess == 42)
    {
        Console.WriteLine("Correct!");
        break;  // Exit loop
    }
    attempts++;
}

// Infinite loop with break
bool isRunning = true;
while (isRunning)
{
    string input = Console.ReadLine();
    if (input.ToLower() == "quit")
    {
        isRunning = false;
    }
}
```

### Do-While Loop (Executes at Least Once)

```csharp
int password;
int attempts = 0;

do
{
    Console.Write("Enter password: ");
    password = int.Parse(Console.ReadLine());
    attempts++;
    
    if (password != 12345)
    {
        Console.WriteLine("Wrong password! Try again.");
    }
} while (password != 12345 && attempts < 3);

if (password == 12345)
{
    Console.WriteLine("Access granted!");
}
else
{
    Console.WriteLine("Too many attempts. Access denied!");
}
```

### Foreach Loop (For Collections)

```csharp
// Loop through array
string[] enemies = { "Goblin", "Orc", "Dragon" };
foreach (string enemy in enemies)
{
    Console.WriteLine($"Enemy: {enemy}");
}

// Loop through List
List<int> scores = new List<int> { 100, 200, 300, 450 };
int totalScore = 0;
foreach (int score in scores)
{
    totalScore += score;
}
Console.WriteLine($"Total Score: {totalScore}");

// Loop through Dictionary
Dictionary<string, int> stats = new Dictionary<string, int>
{
    { "Health", 100 },
    { "Mana", 50 },
    { "Strength", 20 }
};

foreach (KeyValuePair<string, int> stat in stats)
{
    Console.WriteLine($"{stat.Key}: {stat.Value}");
}

// Loop with index (C# 7.1+)
foreach ((string enemy, int index) in enemies.Select((e, i) => (e, i)))
{
    Console.WriteLine($"{index + 1}. {enemy}");
}
```

### Break and Continue

```csharp
// Break: Stop the loop completely
for (int i = 0; i < 10; i++)
{
    if (i == 5)
        break;  // Exit loop at i = 5
    Console.WriteLine(i);  // Prints: 0, 1, 2, 3, 4
}

// Continue: Skip to next iteration
for (int i = 0; i < 10; i++)
{
    if (i % 2 == 0)
        continue;  // Skip even numbers
    Console.WriteLine(i);  // Prints: 1, 3, 5, 7, 9
}

// Practical example: Find first enemy
string[] enemies = { "Slime", "Goblin", "Boss", "Dragon" };
foreach (string enemy in enemies)
{
    if (enemy == "Boss")
    {
        Console.WriteLine("Found the Boss!");
        break;
    }
    Console.WriteLine($"Fighting {enemy}...");
}
```

---

## 7. Arrays

### One-Dimensional Array

```csharp
// Method 1: Direct initialization
string[] inventory = { "Sword", "Shield", "Potion", "Key" };
int[] levels = { 1, 5, 10, 15, 20 };
double[] prices = { 99.99, 149.99, 199.99 };

// Method 2: Define size first
string[] weapons = new string[5];
weapons[0] = "Dagger";
weapons[1] = "Sword";
weapons[2] = "Bow";
weapons[3] = "Staff";
weapons[4] = "Hammer";

// Method 3: With new keyword
int[] enemyHealth = new int[] { 50, 100, 150 };
bool[] bossDefeated = new bool[] { true, false, true };

// Accessing array elements
string firstWeapon = weapons[0];      // "Dagger"
string lastWeapon = weapons[^1];      // "Hammer" (from end)
string secondLast = weapons[^2];      // "Staff"

// Array length
int arraySize = weapons.Length;       // 5

// Modifying array elements
weapons[2] = "Crossbow";

// Finding element position
int indexOfSword = Array.IndexOf(weapons, "Sword");  // 1

// Copying array
string[] weaponsCopy = (string[])weapons.Clone();
```

### Two-Dimensional Array (Game Board)

```csharp
// Method 1: Initialize with size
int[,] gameBoard = new int[5, 5];
gameBoard[0, 0] = 1;
gameBoard[2, 2] = 9;
gameBoard[4, 4] = 5;

// Method 2: Direct initialization
int[,] levelMap = new int[,]
{
    { 1, 1, 1, 1, 1 },
    { 1, 0, 0, 0, 1 },
    { 1, 0, 9, 0, 1 },
    { 1, 0, 0, 0, 1 },
    { 1, 1, 1, 1, 1 }
};

// Accessing 2D array
int value = levelMap[2, 2];  // 9

// Looping through 2D array
Console.WriteLine("Game Map:");
for (int row = 0; row < levelMap.GetLength(0); row++)
{
    for (int col = 0; col < levelMap.GetLength(1); col++)
    {
        Console.Write(levelMap[row, col] + " ");
    }
    Console.WriteLine();
}

// Output:
// 1 1 1 1 1 
// 1 0 0 0 1 
// 1 0 9 0 1 
// 1 0 0 0 1 
// 1 1 1 1 1 
```

### Three-Dimensional Array (Rare)

```csharp
int[,,] cube = new int[3, 3, 3];
cube[0, 0, 0] = 1;
cube[1, 1, 1] = 5;
cube[2, 2, 2] = 9;

// Accessing
int cubeValue = cube[1, 1, 1];  // 5
```

### Jagged Array

```csharp
// Array of arrays (each row can have different size)
int[][] jagged = new int[3][];
jagged[0] = new int[5];
jagged[1] = new int[3];
jagged[2] = new int[4];

jagged[0][0] = 1;
jagged[1][2] = 5;
jagged[2][3] = 9;

// Direct initialization
int[][] scores = new int[][]
{
    new int[] { 100, 200, 300 },
    new int[] { 150, 250 },
    new int[] { 120, 180, 220, 300 }
};
```

---

## 8. List (Dynamic Array)

### Basic List Operations

```csharp
using System.Collections.Generic;

// Creating Lists
List<string> inventory = new List<string>();
List<int> playerScores = new List<int>();
List<double> prices = new List<double>();

// Adding items
inventory.Add("Potion");
inventory.Add("Elixir");
inventory.Add("Sword");

// Adding multiple items
inventory.AddRange(new[] { "Bow", "Arrow", "Shield" });

// Inserting at specific index
inventory.Insert(1, "Health Potion");  // Insert at index 1

// Accessing elements
string firstItem = inventory[0];
string lastItem = inventory[inventory.Count - 1];

// Removing items
inventory.Remove("Potion");          // Remove by value
inventory.RemoveAt(0);               // Remove by index
inventory.RemoveRange(1, 2);         // Remove 2 items starting from index 1
inventory.Clear();                   // Remove all items

// Checking items
int itemCount = inventory.Count;
bool hasPotion = inventory.Contains("Potion");
int indexOfBow = inventory.IndexOf("Bow");

// Sorting
inventory.Sort();        // Sort alphabetically (A-Z)
inventory.Reverse();     // Reverse order

// Getting range
List<string> subList = inventory.GetRange(1, 3);  // Items from index 1, count 3
```

### Looping Through List

```csharp
List<string> enemies = new List<string> { "Goblin", "Orc", "Dragon" };

// For loop
for (int i = 0; i < enemies.Count; i++)
{
    Console.WriteLine($"{i + 1}. {enemies[i]}");
}

// Foreach loop
foreach (string enemy in enemies)
{
    Console.WriteLine($"Enemy: {enemy}");
}

// LINQ (Language Integrated Query)
var result = enemies.Where(e => e.Contains("o")).ToList();
```

### List with Custom Objects

```csharp
public class Player
{
    public string Name { get; set; }
    public int Level { get; set; }
}

// Create list of players
List<Player> players = new List<Player>();
players.Add(new Player { Name = "Faris", Level = 10 });
players.Add(new Player { Name = "Komi", Level = 8 });
players.Add(new Player { Name = "Mika", Level = 12 });

// Loop through players
foreach (Player p in players)
{
    Console.WriteLine($"{p.Name} - Level {p.Level}");
}
```

---

## 9. Dictionary (Key-Value)

### Basic Dictionary Operations

```csharp
using System.Collections.Generic;

// Creating Dictionary
Dictionary<string, int> playerStats = new Dictionary<string, int>();

// Adding items
playerStats.Add("Health", 100);
playerStats.Add("Mana", 50);
playerStats.Add("Strength", 15);
playerStats.Add("Defense", 10);

// Adding/updating with []
playerStats["Experience"] = 0;
playerStats["Level"] = 1;

// Accessing values
int health = playerStats["Health"];    // 100
int level = playerStats["Level"];       // 1

// Updating value
playerStats["Health"] = 80;

// Removing items
playerStats.Remove("Mana");
playerStats.Clear();  // Remove all

// Checking existence
bool hasHealth = playerStats.ContainsKey("Health");
bool hasValue100 = playerStats.ContainsValue(100);

// Count
int totalStats = playerStats.Count;
```

### Safe Dictionary Access (TryGetValue)

```csharp
Dictionary<string, int> stats = new Dictionary<string, int>
{
    { "Health", 100 },
    { "Mana", 50 }
};

// Safe way to get value (won't crash if key doesn't exist)
if (stats.TryGetValue("Stamina", out int stamina))
{
    Console.WriteLine($"Stamina: {stamina}");
}
else
{
    Console.WriteLine("Stamina not found!");
}
```

### Looping Through Dictionary

```csharp
Dictionary<string, int> inventory = new Dictionary<string, int>
{
    { "Sword", 1 },
    { "Potion", 5 },
    { "Arrow", 20 }
};

// Loop with keys only
foreach (string item in inventory.Keys)
{
    Console.WriteLine(item);
}

// Loop with values only
foreach (int quantity in inventory.Values)
{
    Console.WriteLine(quantity);
}

// Loop with key and value
foreach (KeyValuePair<string, int> kvp in inventory)
{
    Console.WriteLine($"{kvp.Key}: {kvp.Value}");
}

// Deconstruction (C# 7+)
foreach (var (item, quantity) in inventory)
{
    Console.WriteLine($"{item} x{quantity}");
}
```

### Dictionary with Different Types

```csharp
// String to List
Dictionary<string, List<string>> heroAbilities = 
    new Dictionary<string, List<string>>
{
    { "Warrior", new List<string> { "Slash", "Defend", "Charge" } },
    { "Mage", new List<string> { "Fireball", "Teleport", "Heal" } },
    { "Archer", new List<string> { "Shoot", "Dodge", "Multishot" } }
};

// Access nested data
List<string> warriorAbilities = heroAbilities["Warrior"];
foreach (string ability in warriorAbilities)
{
    Console.WriteLine(ability);
}

// Integer to String
Dictionary<int, string> playerById = new Dictionary<int, string>
{
    { 1, "Faris" },
    { 2, "Komi" },
    { 3, "Mika" }
};

string playerName = playerById[1];  // "Faris"
```

---

## 10. String Operations

### Basic String Operations

```csharp
string playerName = "Faris The Legend";

// Length
int length = playerName.Length;  // 17

// Concatenation
string greeting = "Hello " + playerName;
string greeting2 = string.Concat("Greetings, ", playerName);
string greeting3 = $"Welcome back, {playerName}";  // String interpolation
string greeting4 = string.Format("Hello {0}, welcome!", playerName);

// Substring (extract part of string)
string firstName = playerName.Substring(0, 5);     // "Faris"
string lastName = playerName.Substring(6);         // "The Legend"
string middle = playerName.Substring(6, 3);        // "The"

// Finding position
int indexOfThe = playerName.IndexOf("The");        // 6
int lastIndexOfA = playerName.LastIndexOf("a");    // 13

// Checking content
bool contains = playerName.Contains("Faris");      // true
bool startsWith = playerName.StartsWith("Faris");  // true
bool endsWith = playerName.EndsWith("end");        // true

// Replacing text
string newName = playerName.Replace("Legend", "King");  // "Faris The King"

// Trimming whitespace
string messy = "   Hello World   ";
string clean = messy.Trim();         // "Hello World"
string trimStart = messy.TrimStart(); // "Hello World   "
string trimEnd = messy.TrimEnd();     // "   Hello World"

// Change case
string upper = playerName.ToUpper();  // "FARIS THE LEGEND"
string lower = playerName.ToLower();  // "faris the legend"

// Splitting into array
string data = "Faris,20,100,true";
string[] parts = data.Split(',');
string name = parts[0];    // "Faris"
string age = parts[1];     // "20"
string score = parts[2];   // "100"
string active = parts[3];  // "true"

// Joining array into string
string[] items = { "Sword", "Shield", "Potion" };
string inventory = string.Join(", ", items);  // "Sword, Shield, Potion"
```

### Checking Empty or Null

```csharp
string input = "";

// Check if null or empty
if (string.IsNullOrEmpty(input))
{
    Console.WriteLine("Input is empty!");
}

// Check if null, empty, or only whitespace
if (string.IsNullOrWhiteSpace(input))
{
    Console.WriteLine("Input is empty or whitespace!");
}
```

### String Builder (For Complex String Building)

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
sb.Append("Faris ");
sb.AppendLine("The Legend");  // Adds newline
sb.Append("Loves ");
sb.Append("C#");

string result = sb.ToString();  
// "Faris The Legend\nLoves C#"

// More efficient than string concatenation in loops
var sb2 = new StringBuilder();
for (int i = 0; i < 100; i++)
{
    sb2.Append(i);
    sb2.Append(", ");
}
string allNumbers = sb2.ToString();
```

---

## 11. Random Numbers

### Basic Random Generation

```csharp
Random rnd = new Random();

// Random number 0 to 99
int randomNum = rnd.Next(100);

// Random number 1 to 100 (inclusive)
int randomDamage = rnd.Next(1, 101);

// Random double 0.0 to 1.0
double randomPercent = rnd.NextDouble();

// Random boolean (50% true, 50% false)
bool isCritical = rnd.Next(2) == 1;
```

### Practical Game Examples

```csharp
Random rng = new Random();

// Random attack damage (15-30)
int baseDamage = 20;
int variableDamage = rng.Next(baseDamage - 5, baseDamage + 11);

// Random critical hit (20% chance)
int critChance = rng.Next(1, 101);
bool isCrit = critChance <= 20;
int finalDamage = isCrit ? variableDamage * 2 : variableDamage;

// Random enemy encounter
string[] enemies = { "Goblin", "Orc", "Dragon", "Slime", "Skeleton" };
string randomEnemy = enemies[rng.Next(enemies.Length)];

// Random reward
int goldReward = rng.Next(50, 201);  // 50-200 gold

// Shuffling items (Fisher-Yates)
int[] deck = Enumerable.Range(0, 52).ToArray();
for (int i = deck.Length - 1; i > 0; i--)
{
    int randomIndex = rng.Next(i + 1);
    // Swap
    int temp = deck[i];
    deck[i] = deck[randomIndex];
    deck[randomIndex] = temp;
}
```

### Fixed Seed for Reproducibility

```csharp
// Same seed = same random numbers (for testing)
Random fixedRng = new Random(42);
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(fixedRng.Next(100));
}
// Output will be the same every time

// Without seed = different each run
Random variableRng = new Random();
```

---

## 12. Methods (Functions)

### Basic Method Structure

```csharp
// Method with no parameters and no return
public void SayHello()
{
    Console.WriteLine("Hello, World!");
}

// Method with parameters
public void GreetPlayer(string name)
{
    Console.WriteLine($"Hello, {name}!");
}

// Method with return value
public int AddNumbers(int a, int b)
{
    return a + b;
}

// Method with multiple parameters and return
public float CalculateDamage(float baseDamage, float modifier, int level)
{
    return baseDamage * modifier * (1 + level * 0.1f);
}
```

### Default Parameters

```csharp
public void Attack(string target, int damage = 10, bool isCrit = false)
{
    int finalDamage = isCrit ? damage * 2 : damage;
    Console.WriteLine($"{target} takes {finalDamage} damage!");
}

// Calling with different parameter combinations
Attack("Goblin");                    // damage=10, isCrit=false
Attack("Orc", 25);                   // damage=25, isCrit=false
Attack("Dragon", 50, true);          // damage=50, isCrit=true
```

### Named Arguments

```csharp
public void CreateCharacter(string name, int level, string classType, int health = 100)
{
    Console.WriteLine($"{name} - Level {level} {classType} (HP: {health})");
}

// Using named arguments
CreateCharacter(name: "Faris", level: 10, classType: "Warrior");
CreateCharacter(health: 150, classType: "Warrior", level: 10, name: "Faris");
```

### Method Overloading

```csharp
// Same name, different parameters
public int Multiply(int a, int b)
{
    return a * b;
}

public double Multiply(double a, double b)
{
    return a * b;
}

public string Multiply(string s, int times)
{
    string result = "";
    for (int i = 0; i < times; i++)
    {
        result += s;
    }
    return result;
}

// Usage
int result1 = Multiply(5, 3);              // 15
double result2 = Multiply(5.5, 2.2);       // 12.1
string result3 = Multiply("Ha", 3);        // "HaHaHa"
```

### Out Parameter (Return Multiple Values)

```csharp
public bool TryDivide(int dividend, int divisor, out int result, out double resultDouble)
{
    if (divisor == 0)
    {
        result = 0;
        resultDouble = 0.0;
        return false;
    }
    result = dividend / divisor;
    resultDouble = (double)dividend / divisor;
    return true;
}

// Usage
if (TryDivide(10, 3, out int intResult, out double doubleResult))
{
    Console.WriteLine($"Integer: {intResult}, Double: {doubleResult}");
}
```

### Ref Parameter (Pass by Reference)

```csharp
public void IncreaseHealth(ref int health, int amount)
{
    health += amount;
}

// Usage
int playerHealth = 50;
IncreaseHealth(ref playerHealth, 30);
Console.WriteLine(playerHealth);  // 80 (value changed)
```

### Params Parameter (Variable Arguments)

```csharp
public int SumNumbers(params int[] numbers)
{
    int total = 0;
    foreach (int num in numbers)
    {
        total += num;
    }
    return total;
}

// Usage
int sum1 = SumNumbers(1, 2, 3);              // 6
int sum2 = SumNumbers(10, 20, 30, 40, 50);   // 150
int sum3 = SumNumbers();                     // 0
```

### Methods for Game Logic

```csharp
public class GameLogic
{
    // Calculate damage
    public int CalculateFinalDamage(int baseAttack, int enemyDefense, Random rnd)
    {
        int variance = rnd.Next(baseAttack / 2);
        int damage = baseAttack + variance - enemyDefense;
        return damage > 1 ? damage : 1;  // Minimum damage is 1
    }
    
    // Check level up
    public bool CheckLevelUp(int currentExp, int expNeeded)
    {
        return currentExp >= expNeeded;
    }
    
    // Random encounter
    public string RandomEncounter(Random rnd)
    {
        string[] encounters = { "Enemy!", "Treasure!", "Nothing" };
        return encounters[rnd.Next(encounters.Length)];
    }
    
    // Heal player
    public int HealPlayer(int currentHealth, int maxHealth, int healAmount)
    {
        int newHealth = currentHealth + healAmount;
        return newHealth > maxHealth ? maxHealth : newHealth;
    }
    
    // Is player dead
    public bool IsPlayerDead(int health)
    {
        return health <= 0;
    }
}
```

---

## 13. Classes & Objects

### Basic Class Structure

```csharp
public class Player
{
    // Fields (private data)
    private string name;
    private int level;
    private int health;
    private int maxHealth;
    
    // Properties (public access with get/set)
    public string Name 
    { 
        get { return name; }
        set { name = value; }
    }
    
    // Auto-implemented property (shorthand)
    public int Level { get; set; }
    public int Experience { get; set; }
    public List<string> Inventory { get; set; }
    public int Gold { get; set; }
    
    // Constructor (called when object is created)
    public Player()
    {
        Name = "New Player";
        Level = 1;
        health = 100;
        maxHealth = 100;
        Experience = 0;
        Gold = 0;
        Inventory = new List<string>();
    }
    
    // Constructor with parameters
    public Player(string playerName, int startingLevel)
    {
        Name = playerName;
        Level = startingLevel;
        health = 100;
        maxHealth = 100;
        Experience = 0;
        Gold = 0;
        Inventory = new List<string>();
    }
    
    // Methods
    public void TakeDamage(int damage)
    {
        health -= damage;
        if (health <= 0)
        {
            health = 0;
            Die();
        }
    }
    
    public void Heal(int amount)
    {
        health += amount;
        if (health > maxHealth)
        {
            health = maxHealth;
        }
    }
    
    public void AddExperience(int exp)
    {
        Experience += exp;
        if (Experience >= Level * 100)
        {
            LevelUp();
        }
    }
    
    public void AddItem(string item)
    {
        Inventory.Add(item);
        Console.WriteLine($"{item} added to inventory!");
    }
    
    public void AddGold(int amount)
    {
        Gold += amount;
        Console.WriteLine($"Gold increased by {amount}. Total: {Gold}");
    }
    
    private void LevelUp()
    {
        Level++;
        maxHealth += 10;
        health = maxHealth;
        Experience = 0;
        Console.WriteLine($"Level Up! Now level {Level}");
    }
    
    private void Die()
    {
        Console.WriteLine($"{Name} has died... Game Over!");
    }
    
    public void DisplayInfo()
    {
        Console.WriteLine("=== Player Information ===");
        Console.WriteLine($"Name: {Name}");
        Console.WriteLine($"Level: {Level}");
        Console.WriteLine($"Health: {health}/{maxHealth}");
        Console.WriteLine($"Experience: {Experience}");
        Console.WriteLine($"Gold: {Gold}");
        Console.WriteLine($"Inventory: {string.Join(", ", Inventory)}");
    }
}
```

### Using the Class (Creating Objects)

```csharp
// Create player objects
Player player1 = new Player();
player1.Name = "Faris";
player1.Level = 5;

Player player2 = new Player("Komi", 10);

// Use methods
player1.AddItem("Sword");
player1.AddItem("Potion");
player1.AddGold(100);
player1.TakeDamage(20);
player1.Heal(15);
player1.AddExperience(150);

// Display info
player1.DisplayInfo();

// player2.DisplayInfo();
```

### Inheritance (Class Inheriting from Another)

```csharp
// Base class
public class Character
{
    public string Name { get; set; }
    public int Level { get; set; }
    public int Health { get; set; }
    
    public virtual void TakeDamage(int damage)
    {
        Health -= damage;
    }
    
    public virtual void DisplayInfo()
    {
        Console.WriteLine($"{Name} - Level {Level}");
    }
}

// Derived class
public class Warrior : Character
{
    public int Armor { get; set; }
    
    public Warrior()
    {
        Armor = 5;
    }
    
    // Override method
    public override void TakeDamage(int damage)
    {
        int reducedDamage = damage - Armor;
        base.TakeDamage(reducedDamage > 0 ? reducedDamage : 1);
    }
    
    public override void DisplayInfo()
    {
        base.DisplayInfo();
        Console.WriteLine($"Armor: {Armor}");
    }
}

// Usage
Warrior warrior = new Warrior();
warrior.Name = "Faris";
warrior.Level = 10;
warrior.Health = 150;
warrior.TakeDamage(20);  // Takes less damage due to armor
warrior.DisplayInfo();
```

---

## 14. Exception Handling (Try-Catch)

### Basic Try-Catch

```csharp
try
{
    string input = Console.ReadLine();
    int number = int.Parse(input);
    Console.WriteLine($"You entered: {number}");
}
catch (FormatException)
{
    Console.WriteLine("Error: Please enter a valid number!");
}
catch (Exception ex)
{
    Console.WriteLine($"An error occurred: {ex.Message}");
}
```

### Try-Catch-Finally

```csharp
FileStream file = null;
try
{
    file = new FileStream("data.txt", FileMode.Open);
    // Read file
    Console.WriteLine("File opened successfully!");
}
catch (FileNotFoundException)
{
    Console.WriteLine("Error: File not found!");
}
finally
{
    // Always executed
    file?.Close();
    Console.WriteLine("File closed.");
}
```

### Multiple Specific Exceptions

```csharp
try
{
    int[] numbers = { 1, 2, 3 };
    int value = numbers[10];  // IndexOutOfRangeException
    
    string text = null;
    int length = text.Length;  // NullReferenceException
    
    int result = 10 / 0;  // DivideByZeroException
}
catch (IndexOutOfRangeException)
{
    Console.WriteLine("Error: Array index out of range!");
}
catch (NullReferenceException)
{
    Console.WriteLine("Error: Null reference!");
}
catch (DivideByZeroException)
{
    Console.WriteLine("Error: Cannot divide by zero!");
}
catch (Exception ex)
{
    Console.WriteLine($"Unexpected error: {ex.Message}");
}
```

### Throwing Custom Exceptions

```csharp
public class InsufficientHealthException : Exception
{
    public InsufficientHealthException(string message) : base(message)
    {
    }
}

public void Attack(int damage)
{
    if (damage < 0)
    {
        throw new InsufficientHealthException("Damage cannot be negative!");
    }
    
    Console.WriteLine($"Attack for {damage} damage!");
}

// Usage
try
{
    Attack(-10);
}
catch (InsufficientHealthException ex)
{
    Console.WriteLine($"Attack failed: {ex.Message}");
}
```

---

## 15. Enum (Constant Data)

### Basic Enum

```csharp
public enum PlayerClass
{
    Warrior,  // 0
    Mage,     // 1
    Archer,   // 2
    Rogue     // 3
}

public enum Direction
{
    North,
    South,
    East,
    West
}

// Usage
PlayerClass myClass = PlayerClass.Warrior;
Direction facing = Direction.North;

Console.WriteLine(myClass);      // Warrior
Console.WriteLine((int)myClass);  // 0

if (myClass == PlayerClass.Warrior)
{
    Console.WriteLine("I am a warrior!");
}
```

### Enum with Custom Values

```csharp
public enum ItemType
{
    Weapon = 1,
    Armor = 2,
    Consumable = 3,
    Quest = 4
}

public enum Status
{
    Alive = 1,
    Dead = 0,
    Stunned = 2,
    Poisoned = 3
}

// Usage
ItemType item = ItemType.Weapon;
Console.WriteLine((int)item);  // 1
```

### Enum in Switch Statement

```csharp
public enum GameState
{
    MainMenu,
    Playing,
    Paused,
    GameOver
}

GameState state = GameState.Playing;

switch (state)
{
    case GameState.MainMenu:
        Console.WriteLine("Show main menu");
        break;
    case GameState.Playing:
        Console.WriteLine("Game is running");
        break;
    case GameState.Paused:
        Console.WriteLine("Game is paused");
        break;
    case GameState.GameOver:
        Console.WriteLine("Game over screen");
        break;
}
```

---

## 16. DateTime (Date & Time)

### Basic DateTime

```csharp
// Current date and time
DateTime now = DateTime.Now;
Console.WriteLine(now);  // e.g., 6/15/2026 2:30:45 PM

// Current UTC time
DateTime utcNow = DateTime.UtcNow;

// Specific date
DateTime birthDate = new DateTime(2005, 1, 15);
Console.WriteLine(birthDate);  // 1/15/2005 12:00:00 AM

// Parse from string
DateTime parsed = DateTime.Parse("2026-06-15 14:30:00");

// Components
Console.WriteLine(now.Year);      // 2026
Console.WriteLine(now.Month);     // 6
Console.WriteLine(now.Day);       // 15
Console.WriteLine(now.Hour);      // 14
Console.WriteLine(now.Minute);    // 30
Console.WriteLine(now.Second);    // 45
```

### DateTime Calculations

```csharp
DateTime startDate = DateTime.Now;
DateTime futureDate = startDate.AddDays(7);        // 7 days later
DateTime yesterday = startDate.AddDays(-1);        // 1 day ago
DateTime nextMonth = startDate.AddMonths(1);       // 1 month later
DateTime nextYear = startDate.AddYears(1);         // 1 year later
DateTime futureTime = startDate.AddHours(3);       // 3 hours later

// Time difference
TimeSpan difference = futureDate - startDate;
Console.WriteLine(difference.Days);       // 7
Console.WriteLine(difference.TotalHours);  // 168
```

### Formatting DateTime

```csharp
DateTime now = DateTime.Now;

// Various formats
Console.WriteLine(now.ToString("yyyy-MM-dd"));           // 2026-06-15
Console.WriteLine(now.ToString("MM/dd/yyyy"));           // 06/15/2026
Console.WriteLine(now.ToString("dddd, MMMM dd, yyyy"));  // Monday, June 15, 2026
Console.WriteLine(now.ToString("hh:mm:ss tt"));          // 02:30:45 PM
Console.WriteLine(now.ToString("HH:mm:ss"));             // 14:30:45
```

---

## 17. File I/O (Read & Write Files)

### Writing to Files

```csharp
using System.IO;

// Write text to file (overwrites if exists)
File.WriteAllText("data.txt", "Hello, World!");

// Append text to file
File.AppendAllText("data.txt", "\nLine 2\nLine 3");

// Write multiple lines
string[] lines = { "Line 1", "Line 2", "Line 3" };
File.WriteAllLines("data.txt", lines);

// Writing with stream
using (StreamWriter writer = new StreamWriter("data.txt"))
{
    writer.WriteLine("First line");
    writer.WriteLine("Second line");
    writer.WriteLine("Third line");
}
```

### Reading from Files

```csharp
using System.IO;

// Read all text
string content = File.ReadAllText("data.txt");
Console.WriteLine(content);

// Read all lines
string[] lines = File.ReadAllLines("data.txt");
foreach (string line in lines)
{
    Console.WriteLine(line);
}

// Read with stream
using (StreamReader reader = new StreamReader("data.txt"))
{
    string line;
    while ((line = reader.ReadLine()) != null)
    {
        Console.WriteLine(line);
    }
}
```

### Checking File Existence

```csharp
string filePath = "data.txt";

if (File.Exists(filePath))
{
    Console.WriteLine("File exists!");
    string content = File.ReadAllText(filePath);
}
else
{
    Console.WriteLine("File does not exist!");
}
```

### Working with Directories

```csharp
// Create directory
if (!Directory.Exists("MyFolder"))
{
    Directory.CreateDirectory("MyFolder");
}

// List files in directory
string[] files = Directory.GetFiles("MyFolder");
foreach (string file in files)
{
    Console.WriteLine(file);
}

// Delete file
if (File.Exists("oldfile.txt"))
{
    File.Delete("oldfile.txt");
}

// Delete directory
if (Directory.Exists("MyFolder"))
{
    Directory.Delete("MyFolder", true);  // true = recursive
}
```

---

## 18. SQL Server Database Connection

### Connection String

```csharp
using System.Data.SqlClient;

string connectionString = "Server=localhost;Database=GameDB;User Id=sa;Password=YourPassword;";
// or
string connectionString = "Data Source=localhost;Initial Catalog=GameDB;Integrated Security=true;";
```

### Basic Database Operations

```csharp
using System.Data.SqlClient;

public class DatabaseManager
{
    private string connectionString = "Server=localhost;Database=GameDB;User Id=sa;Password=YourPassword;";
    
    // INSERT
    public void InsertPlayer(string name, int level)
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = "INSERT INTO Players (Name, Level) VALUES (@name, @level)";
            
            using (SqlCommand command = new SqlCommand(query, connection))
            {
                command.Parameters.AddWithValue("@name", name);
                command.Parameters.AddWithValue("@level", level);
                
                connection.Open();
                command.ExecuteNonQuery();
                Console.WriteLine("Player inserted!");
            }
        }
    }
    
    // SELECT (Read)
    public void GetPlayers()
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = "SELECT * FROM Players";
            
            using (SqlCommand command = new SqlCommand(query, connection))
            {
                connection.Open();
                SqlDataReader reader = command.ExecuteReader();
                
                while (reader.Read())
                {
                    string name = reader["Name"].ToString();
                    int level = (int)reader["Level"];
                    Console.WriteLine($"{name} - Level {level}");
                }
            }
        }
    }
    
    // UPDATE
    public void UpdatePlayerLevel(int playerId, int newLevel)
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = "UPDATE Players SET Level = @level WHERE Id = @id";
            
            using (SqlCommand command = new SqlCommand(query, connection))
            {
                command.Parameters.AddWithValue("@level", newLevel);
                command.Parameters.AddWithValue("@id", playerId);
                
                connection.Open();
                command.ExecuteNonQuery();
                Console.WriteLine("Player level updated!");
            }
        }
    }
    
    // DELETE
    public void DeletePlayer(int playerId)
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = "DELETE FROM Players WHERE Id = @id";
            
            using (SqlCommand command = new SqlCommand(query, connection))
            {
                command.Parameters.AddWithValue("@id", playerId);
                
                connection.Open();
                command.ExecuteNonQuery();
                Console.WriteLine("Player deleted!");
            }
        }
    }
}
```

### Usage Example

```csharp
DatabaseManager dbManager = new DatabaseManager();

// Insert
dbManager.InsertPlayer("Faris", 10);
dbManager.InsertPlayer("Komi", 8);

// Read
dbManager.GetPlayers();

// Update
dbManager.UpdatePlayerLevel(1, 15);

// Delete
dbManager.DeletePlayer(2);
```

---

## 19. Quick Reference Summary

### Essential Keywords

| Keyword | Purpose |
|---------|---------|
| `using` | Import namespace or manage resources |
| `class` | Define a class |
| `public` | Accessible from anywhere |
| `private` | Only accessible within the class |
| `static` | Belongs to class, not instance |
| `void` | Method returns nothing |
| `return` | Return value from method |
| `new` | Create new object instance |
| `if / else` | Conditional execution |
| `switch / case` | Multiple conditions |
| `for / while / foreach` | Looping |
| `break / continue` | Control loop flow |
| `try / catch / finally` | Exception handling |
| `throw` | Throw exception |

### Common Namespaces

```csharp
using System;                       // Basic types and functions
using System.Collections.Generic;   // List, Dictionary, etc.
using System.Text;                  // String builder
using System.IO;                    // File operations
using System.Data.SqlClient;        // SQL Server
using System.Linq;                  // LINQ queries
```

### Quick Comparison Table

| Task | Code | Example |
|------|------|---------|
| Input | `Console.ReadLine()` | `string name = Console.ReadLine();` |
| Output | `Console.WriteLine()` | `Console.WriteLine("Hello");` |
| Create List | `new List<T>()` | `List<int> scores = new List<int>();` |
| Create Dictionary | `new Dictionary<K,V>()` | `Dictionary<string, int> stats = new Dictionary<string, int>();` |
| Loop Array | `foreach` | `foreach (int num in numbers)` |
| Try-Catch | `try { } catch` | `try { ... } catch (Exception ex)` |
| Random | `new Random()` | `Random rnd = new Random();` |
| File Read | `File.ReadAllText()` | `File.ReadAllText("file.txt");` |
| File Write | `File.WriteAllText()` | `File.WriteAllText("file.txt", content);` |

---

## 📚 Quick Tips for LKS Competition

1. **Always use try-catch** when dealing with user input
2. **Use meaningful variable names** (not a, b, c)
3. **Comment your code** for clarity
4. **Validate input** before processing
5. **Use List instead of Array** when size is dynamic
6. **Use Dictionary** for key-value pair lookups
7. **Break code into methods** for reusability
8. **Handle exceptions** gracefully
9. **Use appropriate data types** (int for whole numbers, double for decimals)
10. **Test edge cases** (empty input, null, zero, negative numbers)

---

**Last Updated:** June 2026

**Created by:** Faris

**Purpose:** LKS Competition Preparation & C# Reference Guide

**Status:** 📚 Complete & Ready for Competition

---

> Remember: **Practice makes perfect!** Keep coding and testing these examples. Good luck with your competition! 🚀
