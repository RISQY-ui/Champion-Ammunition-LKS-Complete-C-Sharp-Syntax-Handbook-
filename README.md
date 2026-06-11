# Amunisi-Juara-LKS-Complete-C-Syntax-Handbook
---
# Syntax C# Lengkap - Amunisi LKS Game Faris

## 📋 Daftar Isi

- [1. Variabel & Tipe Data](#1-variabel--tipe-data)
- [2. Deklarasi Variabel](#2-deklarasi-variabel)
- [3. Konversi Tipe Data (Casting)](#3-konversi-tipe-data-casting)
- [4. Operator](#4-operator)
- [5. Percabangan (IF, ELSE, SWITCH)](#5-percabangan-if-else-switch)
- [6. Perulangan (Looping)](#6-perulangan-looping)
- [7. Array](#7-array)
- [8. List (Dynamic Array)](#8-list-dynamic-array)
- [9. Dictionary](#9-dictionary)
- [10. String Operation](#10-string-operation)
- [11. Random Number](#11-random-number)
- [12. Method (Fungsi)](#12-method-fungsi)
- [13. Class & Object](#13-class--object)
- [14. Exception Handling (Try-Catch)](#14-exception-handling-try-catch)
- [15. Enum (Data Tetap)](#15-enum-data-tetap)
- [16. DateTime (Tanggal & Waktu)](#16-datetime-tanggal--waktu)
- [17. File I/O (Baca Tulis File)](#17-file-io-baca-tulis-file)
- [18. Koneksi Database SQL Server](#18-koneksi-database-sql-server)
- [19. Ringkasan Cepat](#19-ringkasan-cepat)

---

## 1. Variabel & Tipe Data

| Tipe Data | Keyword | Range / Ukuran | Contoh |
|-----------|---------|----------------|--------|
| Bilangan bulat | `int` | -2M s/d 2M | `int level = 5;` |
| Bilangan bulat (positif) | `uint` | 0 s/d 4M | `uint score = 1000;` |
| Bilangan bulat kecil | `byte` | 0 s/d 255 | `byte exp = 50;` |
| Bilangan bulat pendek | `short` | -32.768 s/d 32.767 | `short lives = 3;` |
| Bilangan bulat panjang | `long` | sangat besar | `long gold = 9999999;` |
| Desimal (presisi rendah) | `float` | 6-7 digit | `float speed = 5.5f;` |
| Desimal (presisi tinggi) | `double` | 15-16 digit | `double damage = 99.9;` |
| Desimal (keuangan) | `decimal` | 28-29 digit | `decimal price = 10000m;` |
| Teks | `string` | 2GB maksimal | `string name = "Faris";` |
| Satu karakter | `char` | satu huruf | `char grade = 'A';` |
| Boolean (true/false) | `bool` | true atau false | `bool isAlive = true;` |
| Tanggal & waktu | `DateTime` | tahun 1-9999 | `DateTime now = DateTime.Now;` |

### Contoh Kode

```csharp
int playerLevel = 10;
float playerSpeed = 5.5f;
double playerDamage = 99.9;
string playerName = "Faris Ganteng";
bool isAlive = true;
DateTime startGame = DateTime.Now;
```

---

2. Deklarasi Variabel

```csharp
// ======= CARA 1: Deklarasi lalu isi =======
int experience;
experience = 100;

// ======= CARA 2: Langsung isi =======
int health = 100;
string playerName = "Faris";

// ======= CARA 3: Multiple variabel =======
int x = 10, y = 20, z = 30;
string a = "A", b = "B", c = "C";

// ======= CARA 4: Var (tipe data otomatis) =======
var level = 5;           // otomatis jadi int
var title = "Hero";       // otomatis jadi string
var isWin = true;         // otomatis jadi bool

// ======= CARA 5: Konstanta (nilai tetap) =======
const float GRAVITY = 9.8f;
const int MAX_LEVEL = 100;
const string GAME_NAME = "Adventure Game";

// ======= CARA 6: Nullable (bisa kosong) =======
int? playerScore = null;
string? middleName = null;
```

---

3. Konversi Tipe Data (Casting)

```csharp
// ======= DARI STRING KE ANGKA (PENTING UNTUK INPUT) =======
string inputDariTextBox = "100";
int damage = Convert.ToInt32(inputDariTextBox);
long bigNumber = Convert.ToInt64(inputDariTextBox);
float speed = Convert.ToSingle("5.5");
double damageD = Convert.ToDouble("99.9");
decimal price = Convert.ToDecimal("10000");

// ======= DARI ANGKA KE STRING =======
int level = 10;
string levelText = level.ToString();
string healthText = health.ToString();

// ======= CASTING PAKSA =======
float a = 10.5f;
int b = (int)a;           // b = 10 (desimal ilang)
double c = (double)a;      // c = 10.5

// ======= PARSE (Alternatif Convert) =======
int number = int.Parse("123");
float numberFloat = float.Parse("12.34");

// ======= TRY PARSE (Aman - Tidak Error) =======
string input = "abc123";
bool success = int.TryParse(input, out int result);
// success = false, result = 0 (tidak error)
```

---

4. Operator

Aritmatika

Operator Fungsi Contoh
+ Penjumlahan int c = a + b;
- Pengurangan int c = a - b;
* Perkalian int c = a * b;
/ Pembagian int c = a / b;
% Modulus (sisa bagi) int sisa = 10 % 3; // 1

Increment & Decrement

```csharp
int score = 0;
score++;        // score = 1 (tambah 1)
score--;        // score = 0 (kurang 1)
score += 5;     // score = 5 (tambah 5)
score -= 2;     // score = 3 (kurang 2)
score *= 2;     // score = 6 (kali 2)
score /= 3;     // score = 2 (bagi 3)
```

Perbandingan (Hasil bool)

Operator Fungsi Contoh
== Sama dengan if (a == b)
!= Tidak sama if (a != b)
> Lebih besar if (a > b)
< Lebih kecil if (a < b)
>= Lebih besar sama dengan if (a >= b)
<= Lebih kecil sama dengan if (a <= b)

Logika (Boolean)

Operator Fungsi Contoh
&& AND (keduanya true) if (a > 0 && b > 0)
`  `
! NOT (kebalikan) if (!isDead)

---

5. Percabangan (IF, ELSE, SWITCH)

IF Sederhana

```csharp
if (health <= 0)
{
    isAlive = false;
    MessageBox.Show("Game Over!");
}
```

IF-ELSE

```csharp
if (score >= 100)
{
    MessageBox.Show("You Win!");
}
else
{
    MessageBox.Show("Try Again!");
}
```

IF-ELSE IF (Banyak Kondisi)

```csharp
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
else
{
    grade = "D";
}
```

Switch Case

```csharp
switch (playerClass)
{
    case "Warrior":
        health = 150;
        damage = 20;
        break;
    case "Mage":
        health = 80;
        damage = 35;
        break;
    case "Archer":
        health = 100;
        damage = 25;
        break;
    default:
        health = 100;
        damage = 15;
        break;
}
```

Ternary Operator (Singkat)

```csharp
// format: kondisi ? nilai_true : nilai_false
string status = (health > 0) ? "Hidup" : "Mati";
int bonus = (score > 100) ? 50 : 10;
```

---

6. Perulangan (Looping)

For Loop (Tahu jumlahnya)

```csharp
// Looping dari 0 sampai 9
for (int i = 0; i < 10; i++)
{
    Console.WriteLine("Loop ke-" + i);
}

// Looping mundur
for (int i = 10; i > 0; i--)
{
    Console.WriteLine("Countdown: " + i);
}

// Looping array
string[] items = { "Sword", "Shield", "Potion" };
for (int i = 0; i < items.Length; i++)
{
    Console.WriteLine(items[i]);
}
```

While Loop (Tidak tahu jumlahnya)

```csharp
int health = 100;
while (health > 0)
{
    health -= 10;
    Console.WriteLine("Health: " + health);
}

// While dengan kondisi true (infinite sampai break)
bool isRunning = true;
while (isRunning)
{
    string input = Console.ReadLine();
    if (input == "quit")
    {
        isRunning = false;
    }
}
```

Do-While Loop (Jalan minimal 1x)

```csharp
int attempts = 0;
int password;
do
{
    Console.Write("Masukkan password: ");
    password = Convert.ToInt32(Console.ReadLine());
    attempts++;
} while (password != 12345 && attempts < 3);
```

Foreach Loop (Untuk collection)

```csharp
string[] monsters = { "Goblin", "Orc", "Dragon" };
foreach (string monster in monsters)
{
    Console.WriteLine("Musuh: " + monster);
}

List<int> scores = new List<int> { 100, 200, 300 };
foreach (int score in scores)
{
    totalScore += score;
}
```

Break & Continue

```csharp
// Break: menghentikan loop
for (int i = 0; i < 10; i++)
{
    if (i == 5)
        break;  // berhenti di 5
    Console.WriteLine(i);
}

// Continue: skip ke iterasi berikutnya
for (int i = 0; i < 10; i++)
{
    if (i % 2 == 0)
        continue;  // skip angka genap
    Console.WriteLine(i);  // cuma angka ganjil
}
```

---

7. Array

Array Satu Dimensi

```csharp
// Cara 1: Langsung isi
string[] inventory = { "Sword", "Shield", "Potion" };
int[] scores = { 100, 200, 300 };

// Cara 2: Tentukan ukuran dulu
string[] monsters = new string[3];
monsters[0] = "Goblin";
monsters[1] = "Orc";
monsters[2] = "Dragon";

// Cara 3: Dengan constructor
int[] numbers = new int[] { 1, 2, 3, 4, 5 };

// Akses array
string firstItem = inventory[0];     // "Sword"
string lastItem = inventory[^1];     // "Potion" (index dari belakang)

// Ubah isi array
inventory[1] = "Super Shield";

// Panjang array
int length = inventory.Length;  // 3

// Cari index
int index = Array.IndexOf(inventory, "Potion");  // 2
```

Array Dua Dimensi (Papan Game)

```csharp
// Cara 1
int[,] map = new int[5, 5];
map[0, 0] = 1;
map[1, 2] = 3;
map[4, 4] = 9;

// Cara 2: Langsung isi
int[,] gameMap = {
    {1, 1, 1, 1, 1},
    {1, 0, 0, 0, 1},
    {1, 0, 9, 0, 1},
    {1, 0, 0, 0, 1},
    {1, 1, 1, 1, 1}
};

// Akses array 2D
int value = gameMap[2, 2];  // 9

// Looping array 2D
for (int i = 0; i < gameMap.GetLength(0); i++)
{
    for (int j = 0; j < gameMap.GetLength(1); j++)
    {
        Console.Write(gameMap[i, j] + " ");
    }
    Console.WriteLine();
}
```

Array 3 Dimensi (Jarang Tapi Mungkin)

```csharp
int[,,] cube = new int[3, 3, 3];
cube[0, 0, 0] = 1;
cube[1, 1, 1] = 5;
cube[2, 2, 2] = 9;
```

---

8. List (Dynamic Array)

Dasar List

```csharp
using System.Collections.Generic;

// Membuat List
List<string> playerItems = new List<string>();
List<int> playerScores = new List<int>();

// Menambah data
playerItems.Add("Potion");
playerItems.Add("Key");
playerItems.Add("Sword");

// Menambah banyak data sekaligus
playerItems.AddRange(new[] { "Bow", "Arrow", "Shield" });

// Menyisipkan di index tertentu
playerItems.Insert(1, "Health Potion");  // index 1

// Menghapus data
playerItems.Remove("Key");                 // hapus berdasarkan value
playerItems.RemoveAt(0);                   // hapus index ke-0
playerItems.RemoveRange(1, 2);             // hapus 2 data dari index 1
playerItems.Clear();                       // hapus semua

// Akses data
string firstItem = playerItems[0];

// Jumlah data
int totalItems = playerItems.Count;

// Cek apakah ada
bool punyaSword = playerItems.Contains("Sword");

// Cari index
int index = playerItems.IndexOf("Sword");

// Sorting
playerItems.Sort();     // A-Z
playerItems.Reverse();  // Z-A

// Looping List
foreach (string item in playerItems)
{
    Console.WriteLine(item);
}

// List dengan custom class
List<Player> players = new List<Player>();
players.Add(new Player { Name = "Faris", Level = 10 });
```

List Method Lengkap

Method Fungsi
Add(item) Menambah item
AddRange(items) Menambah banyak item
Insert(index, item) Menyisipkan di index
Remove(item) Hapus berdasarkan value
RemoveAt(index) Hapus berdasarkan index
RemoveRange(index, count) Hapus beberapa
Clear() Hapus semua
Contains(item) Cek apakah ada
IndexOf(item) Cari index
Sort() Urutkan ascending
Reverse() Balik urutan
Count Jumlah item (property)

---

9. Dictionary

Dasar Dictionary

```csharp
using System.Collections.Generic;

// Membuat Dictionary (Key - Value)
Dictionary<string, int> playerStats = new Dictionary<string, int>();

// Menambah data
playerStats.Add("Health", 100);
playerStats.Add("Mana", 50);
playerStats.Add("Exp", 0);
playerStats.Add("Level", 1);

// Cara lain
playerStats["Strength"] = 10;
playerStats["Defense"] = 5;

// Mengambil data
int health = playerStats["Health"];  // 100

// Mengubah data
playerStats["Health"] = 80;

// Menghapus data
playerStats.Remove("Mana");

// Cek apakah ada key
if (playerStats.ContainsKey("Health"))
{
    Console.WriteLine("Ada Health!");
}

// Cek apakah ada value
if (playerStats.ContainsValue(100))
{
    Console.WriteLine("Ada yang bernilai 100!");
}

// Jumlah data
int count = playerStats.Count;

// Looping Dictionary (hanya key)
foreach (string key in playerStats.Keys)
{
    Console.WriteLine(key);
}

// Looping Dictionary (key dan value)
foreach (KeyValuePair<string, int> stat in playerStats)
{
    Console.WriteLine($"{stat.Key}: {stat.Value}");
}

// Dictionary dengan tipe berbeda
Dictionary<int, string> playerById = new Dictionary<int, string>();
playerById[1] = "Faris";
playerById[2] = "Komi";
```

Dictionary Method Lengkap

Method Fungsi
Add(key, value) Menambah data
Remove(key) Menghapus berdasarkan key
Clear() Menghapus semua
ContainsKey(key) Cek apakah key ada
ContainsValue(value) Cek apakah value ada
TryGetValue(key, out value) Ambil data aman (tidak error)
Count Jumlah data

TryGetValue (Aman - Tidak Error)

```csharp
Dictionary<string, int> stats = new Dictionary<string, int>();
stats.Add("Health", 100);

// Cara aman ambil data
if (stats.TryGetValue("Mana", out int mana))
{
    Console.WriteLine($"Mana: {mana}");
}
else
{
    Console.WriteLine("Mana tidak ada!");
}
```

---

10. String Operation

Dasar String

```csharp
string name = "Faris Ganteng";

// Panjang string
int length = name.Length;  // 13

// Menggabungkan string
string greeting = "Halo " + name;
string greeting2 = string.Concat("Halo ", name);
string greeting3 = $"Halo {name}";  // String interpolation (C# 6+)
string greeting4 = string.Format("Halo {0}", name);

// Mengambil substring
string firstName = name.Substring(0, 5);   // "Faris"
string lastName = name.Substring(6);        // "Ganteng"

// Mencari posisi
int index = name.IndexOf("Ganteng");  // 6
int lastIndex = name.LastIndexOf("n"); // 12

// Cek apakah mengandung kata
bool contains = name.Contains("Faris");  // true
bool startsWith = name.StartsWith("Far"); // true
bool endsWith = name.EndsWith("eng");     // true

// Mengganti kata
string newName = name.Replace("Ganteng", "Cantik");  // "Faris Cantik"

// Hapus spasi di awal/akhir
string messy = "  Hello  ";
string clean = messy.Trim();  // "Hello"
string trimStart = messy.TrimStart();  // "Hello  "
string trimEnd = messy.TrimEnd();      // "  Hello"

// Ubah huruf besar/kecil
string upper = name.ToUpper();  // "FARIS GANTENG"
string lower = name.ToLower();  // "faris ganteng"

// Split (memecah string menjadi array)
string data = "Faris,20,100,true";
string[] parts = data.Split(',');
string namePart = parts[0];   // "Faris"
string agePart = parts[1];     // "20"

// Join (menggabungkan array jadi string)
string[] items = { "Sword", "Shield", "Potion" };
string inventory = string.Join(", ", items);  // "Sword, Shield, Potion"

// IsNullOrEmpty (Cek kosong)
if (string.IsNullOrEmpty(input))
{
    MessageBox.Show("Input tidak boleh kosong!");
}

// IsNullOrWhiteSpace (Cek kosong atau cuma spasi)
if (string.IsNullOrWhiteSpace(input))
{
    MessageBox.Show("Input tidak boleh kosong atau cuma spasi!");
}
```

StringBuilder (Untuk String Panjang)

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
sb.Append("Faris ");
sb.AppendLine("Ganteng");
sb.Append("Belajar ");
sb.Append("C#");

string result = sb.ToString();  // "Faris Ganteng\nBelajar C#"
```

---

11. Random Number

```csharp
// Membuat Random object
Random rnd = new Random();

// Angka random 0 s/d 99
int randomNumber = rnd.Next(100);

// Angka random 1 s/d 100
int randomDamage = rnd.Next(1, 101);

// Angka random 0.0 s/d 1.0 (double)
double randomDouble = rnd.NextDouble();

// Angka random untuk array
string[] enemies = { "Goblin", "Orc", "Dragon", "Slime" };
int randomIndex = rnd.Next(enemies.Length);
string randomEnemy = enemies[randomIndex];

// Random bool (50% true, 50% false)
bool isCritical = rnd.Next(2) == 1;

// Random dengan seed (hasil sama setiap run)
Random fixedRnd = new Random(123);  // angka seed
int sameNumber = fixedRnd.Next(100); // akan sama setiap program jalan

// Contoh untuk game
Random rng = new Random();
int attackDamage = rng.Next(15, 30);     // damage antara 15-30
int critChance = rng.Next(1, 101);       // 1-100
bool isCrit = critChance <= 20;           // 20% chance crit
int finalDamage = isCrit ? attackDamage * 2 : attackDamage;
```

---

12. Method (Fungsi)

Dasar Method

```csharp
// Method tanpa return (void)
public void DisplayMessage()
{
    Console.WriteLine("Hello World!");
}

// Method dengan parameter
public void GreetPlayer(string playerName)
{
    Console.WriteLine($"Halo {playerName}!");
}

// Method dengan return value
public int AddNumbers(int a, int b)
{
    return a + b;
}

// Method dengan multiple parameter
public float CalculateDamage(float baseDamage, float multiplier, int level)
{
    return baseDamage * multiplier * (1 + level * 0.1f);
}

// Method dengan parameter default
public void Attack(string target, int damage = 10)
{
    Console.WriteLine($"{target} terkena damage {damage}");
}
// Attack("Goblin") → damage 10
// Attack("Dragon", 50) → damage 50

// Method dengan named arguments
Attack(damage: 30, target: "Orc");

// Method overload (nama sama, parameter beda)
public int Multiply(int a, int b) { return a * b; }
public double Multiply(double a, double b) { return a * b; }

// Method dengan output parameter (out)
public bool TryDivide(int a, int b, out int result)
{
    if (b == 0)
    {
        result = 0;
        return false;
    }
    result = a / b;
    return true;
}

// Cara pakai
if (TryDivide(10, 2, out int hasil))
{
    Console.WriteLine($"Hasil: {hasil}");
}

// Method dengan ref parameter
public void IncreaseByRef(ref int value)
{
    value += 10;
}

// Cara pakai
int score = 50;
IncreaseByRef(ref score);  // score sekarang 60

// Method dengan params (parameter tidak terbatas)
public int SumNumbers(params int[] numbers)
{
    int total = 0;
    foreach (int num in numbers)
    {
        total += num;
    }
    return total;
}

// Cara pakai
int total = SumNumbers(1, 2, 3, 4, 5);  // 15
```

Method untuk Game

```csharp
public class GameLogic
{
    // Hitung damage
    public int CalculateDamage(int baseAttack, int enemyDefense)
    {
        int damage = baseAttack - enemyDefense;
        return damage > 0 ? damage : 1;  // minimal damage 1
    }
    
    // Cek level up
    public bool CheckLevelUp(int currentExp, int expNeeded)
    {
        return currentExp >= expNeeded;
    }
    
    // Random encounter
    public string RandomEnemy()
    {
        string[] enemies = { "Goblin", "Orc", "Slime", "Skeleton" };
        Random rnd = new Random();
        return enemies[rnd.Next(enemies.Length)];
    }
    
    // Heal player
    public int HealPlayer(int currentHealth, int maxHealth, int healAmount)
    {
        int newHealth = currentHealth + healAmount;
        return newHealth > maxHealth ? maxHealth : newHealth;
    }
}
```

---

13. Class & Object

Dasar Class

```csharp
// Membuat Class
public class Player
{
    // Fields (variabel anggota)
    private string name;
    private int level;
    private int health;
    
    // Properties (getter setter modern)
    public string Name 
    { 
        get { return name; }
        set { name = value; }
    }
    
    // Auto-implemented property (cara simpel)
    public int Level { get; set; }
    public int Health { get; set; }
    public int MaxHealth { get; set; }
    public List<string> Inventory { get; set; }
    
    // Constructor (dijalankan saat object dibuat)
    public Player()
    {
        Name = "New Player";
        Level = 1;
        Health = 100;
        MaxHealth = 100;
        Inventory = new List<string>();
    }
    
    // Constructor dengan parameter
    public Player(string name, int level)
    {
        Name = name;
        Level = level;
        Health = 100;
        MaxHealth = 100;
        Inventory = new List<string>();
    }
    
    // Method dalam class
    public void TakeDamage(int damage)
    {
        Health -= damage;
        if (Health <= 0)
        {
            Health = 0;
            Die();
        }
    }
    
    public void Heal(int amount)
    {
        Health += amount;
        if (Health > MaxHealth)
        {
            Health = MaxHealth;
        }
    }
    
    public void AddItem(string item)
    {
        Inventory.Add(item);
        Console.WriteLine($"{item} ditambahkan ke inventory!");
    }
    
    private void Die()
    {
        Console.WriteLine($"{Name} telah mati... Game Over!");
    }
    
    public void DisplayInfo()
    {
        Console.WriteLine($"=== Player Info ===");
        Console.WriteLine($"Name: {Name}");
        Console.WriteLine($"Level: {Level}");
        Console.WriteLine($"Health: {Health}/{MaxHealth}");
        Console.WriteLine($"Inventory: {string.Join(", ", Inventory)}");
    }
}

// Cara menggunakan Class
Player player1 = new Player();
player1.Name = "Faris";
player1.Level = 5;
player1.AddItem("Sword");
player1.AddItem("Potion");
player1.DisplayInfo();

Player player2 = new Player("Komi", 10);
player2.TakeDamage(30);
player2.Heal(20);
```

Inheritance (Pewarisan)

```csharp
// Base class (parent)
public class Character
{
    public string Name { get; set; }
    public int Health { get; set; }
    public int Damage { get; set; }
    
    public virtual void Attack(Character target)
    {
        target.Health -= Damage;
        Console.WriteLine($"{Name} menyerang {target.Name} dengan damage {Damage}");
    }
    
    public virtual void Display()
    {
        Console.WriteLine($"Name: {Name}, Health: {Health}");
    }
}

// Derived class (child) - Warrior
public class Warrior : Character
{
    public int Armor { get; set; }
    
    public Warrior()
    {
        Health = 150;
        Damage = 25;
        Armor = 20;
    }
    
    public override void Attack(Character target)
    {
        int finalDamage = Damage + (Armor / 10);
        target.Health -= finalDamage;
        Console.WriteLine($"[Warrior] {Name} menyerang dengan damage {finalDamage}!");
    }
    
    public void ShieldBlock()
    {
        Console.WriteLine($"{Name} memblok dengan shield!");
    }
}

// Derived class (child) - Mage
public class Mage : Character
{
    public int Mana { get; set; }
    
    public Mage()
    {
        Health = 80;
        Damage = 40;
        Mana = 100;
    }
    
    public override void Attack(Character target)
    {
        if (Mana >= 10)
        {
            Mana -= 10;
            target.Health -= Damage;
            Console.WriteLine($"[Mage] {Name} melontarkan fireball dengan damage {Damage}!");
        }
        else
        {
            Console.WriteLine($"[Mage] {Name} kehabisan mana!");
        }
    }
    
    public void CastSpell(string spell)
    {
        Console.WriteLine($"{Name} menggunakan spell: {spell}!");
    }
}

// Cara pakai
Warrior warrior = new Warrior();
warrior.Name = "Arthas";
Mage mage = new Mage();
mage.Name = "Jaina";

warrior.Attack(mage);
mage.Attack(warrior);
```

Static Class & Static Method

```csharp
// Static class (tidak bisa diinstansiasi)
public static class GameManager
{
    public static int TotalEnemies { get; set; }
    public static int TotalPlayers { get; set; }
    
    public static void StartGame()
    {
        Console.WriteLine("Game Started!");
        TotalEnemies = 0;
        TotalPlayers = 1;
    }
    
    public static void GameOver()
    {
        Console.WriteLine("Game Over!");
    }
}

// Langsung dipakai tanpa membuat object
GameManager.StartGame();
GameManager.TotalEnemies = 10;
```

---

14. Exception Handling (Try-Catch)

```csharp
// Dasar Try-Catch
try
{
    int result = 10 / int.Parse("0");
    Console.WriteLine(result);
}
catch (DivideByZeroException ex)
{
    Console.WriteLine("Error: Tidak bisa membagi dengan nol!");
    Console.WriteLine($"Detail: {ex.Message}");
}
catch (FormatException ex)
{
    Console.WriteLine("Error: Format angka salah!");
}
catch (Exception ex)
{
    Console.WriteLine($"Error umum: {ex.Message}");
}

// Try-Catch-Finally
try
{
    SqlConnection conn = new SqlConnection(connectionString);
    conn.Open();
    // proses database
}
catch (SqlException ex)
{
    MessageBox.Show("Error database: " + ex.Message);
}
finally
{
    // Selalu dijalankan (baik error atau tidak)
    if (conn != null)
        conn.Close();
}

// Throw Exception (melempar error sendiri)
public void ValidateAge(int age)
{
    if (age < 0)
        throw new ArgumentException("Umur tidak boleh negatif!");
    if (age < 17)
        throw new Exception("Umur tidak mencukupi untuk game ini!");
}

// Cara pakai
try
{
    ValidateAge(-5);
}
catch (ArgumentException ex)
{
    Console.WriteLine(ex.Message);
}
```

---

15. Enum (Data Tetap)

```csharp
// Membuat Enum
public enum PlayerClass
{
    Warrior,
    Mage,
    Archer,
    Assassin
}

public enum ItemType
{
    Weapon,
    Armor,
    Potion,
    KeyItem
}

public enum GameState
{
    Running,
    Paused,
    GameOver,
    Victory
}

// Enum dengan nilai custom
public enum DamageType
{
    Physical = 1,
    Magic = 2,
    Fire = 3,
    Ice = 4,
    Poison = 5
}

// Cara pakai Enum
PlayerClass myClass = PlayerClass.Warrior;
ItemType item = ItemType.Potion;

// Switch dengan Enum
switch (myClass)
{
    case PlayerClass.Warrior:
        Console.WriteLine("Kamu adalah prajurit tangguh!");
        break;
    case PlayerClass.Mage:
        Console.WriteLine("Kamu adalah penyihir bijak!");
        break;
    case PlayerClass.Archer:
        Console.WriteLine("Kamu adalah pemanah akurat!");
        break;
    case PlayerClass.Assassin:
        Console.WriteLine("Kamu adalah bayangan maut!");
        break;
}

// Konversi Enum ke string
string className = myClass.ToString();  // "Warrior"

// Konversi string ke Enum
PlayerClass newClass = (PlayerClass)Enum.Parse(typeof(PlayerClass), "Mage");

// Konversi Enum ke int
int classValue = (int)PlayerClass.Mage;  // 1
int damageValue = (int)DamageType.Fire;   // 3

// Looping semua nilai Enum
foreach (PlayerClass pc in Enum.GetValues(typeof(PlayerClass)))
{
    Console.WriteLine(pc);
}
```

---

16. DateTime (Tanggal & Waktu)

```csharp
// Mendapatkan waktu sekarang
DateTime now = DateTime.Now;           // 12/06/2025 14:30:25
DateTime today = DateTime.Today;       // 12/06/2025 00:00:00
DateTime utcNow = DateTime.UtcNow;     // UTC time

// Membuat DateTime tertentu
DateTime specificDate = new DateTime(2025, 12, 25);           // 25 Des 2025
DateTime specificDateTime = new DateTime(2025, 12, 25, 14, 30, 0);  // 25 Des 2025 14:30:00

// Ekstrak bagian dari DateTime
int year = now.Year;           // 2025
int month = now.Month;         // 6
int day = now.Day;             // 12
int hour = now.Hour;           // 14
int minute = now.Minute;       // 30
int second = now.Second;       // 25
DayOfWeek weekday = now.DayOfWeek;  // Thursday

// Format DateTime ke string
string format1 = now.ToString("dd/MM/yyyy");     // 12/06/2025
string format2 = now.ToString("dd-MM-yyyy");     // 12-06-2025
string format3 = now.ToString("yyyy-MM-dd");     // 2025-06-12
string format4 = now.ToString("HH:mm:ss");       // 14:30:25
string format5 = now.ToString("dd MMMM yyyy");   // 12 June 2025

// Operasi DateTime
DateTime tomorrow = now.AddDays(1);
DateTime yesterday = now.AddDays(-1);
DateTime nextWeek = now.AddDays(7);
DateTime nextHour = now.AddHours(1);
DateTime nextMonth = now.AddMonths(1);

// Menghitung selisih
DateTime start = new DateTime(2025, 1, 1);
DateTime end = DateTime.Now;
TimeSpan diff = end - start;
int daysDiff = diff.Days;        // jumlah hari
double totalHours = diff.TotalHours;

// Untuk save game / waktu bermain
DateTime gameStart = DateTime.Now;
// ... game berjalan ...
TimeSpan playTime = DateTime.Now - gameStart;
Console.WriteLine($"Waktu bermain: {playTime.Hours} jam {playTime.Minutes} menit");
```

---

17. File I/O (Baca Tulis File)

```csharp
using System.IO;

// ======= MENULIS FILE =======

// Menulis teks ke file (membuat baru atau overwrite)
string content = "Player Name: Faris\nLevel: 10\nScore: 1000";
File.WriteAllText("savegame.txt", content);

// Menambah teks ke file
File.AppendAllText("savegame.txt", $"\nPlay Time: {DateTime.Now}");

// Menulis array baris
string[] lines = { "=== Save Game ===", "Health: 100", "Mana: 50", "Gold: 500" };
File.WriteAllLines("savegame2.txt", lines);

// ======= MEMBACA FILE =======

// Baca semua teks
string allText = File.ReadAllText("savegame.txt");
Console.WriteLine(allText);

// Baca per baris
string[] allLines = File.ReadAllLines("savegame.txt");
foreach (string line in allLines)
{
    Console.WriteLine(line);
}

// Baca dengan StreamReader (lebih efisien untuk file besar)
using (StreamReader reader = new StreamReader("savegame.txt"))
{
    string line;
    while ((line = reader.ReadLine()) != null)
    {
        Console.WriteLine(line);
    }
}

// ======= CEK FILE =======

if (File.Exists("savegame.txt"))
{
    Console.WriteLine("File ditemukan!");
    File.Delete("savegame.txt");  // hapus file
}
else
{
    Console.WriteLine("File tidak ditemukan!");
}

// ======= UNTUK GAME =======

public class SaveGame
{
    public string PlayerName { get; set; }
    public int Level { get; set; }
    public int Health { get; set; }
    public int Score { get; set; }
    
    public void Save(string filename)
    {
        string content = $"{PlayerName}|{Level}|{Health}|{Score}";
        File.WriteAllText(filename, content);
    }
    
    public void Load(string filename)
    {
        if (File.Exists(filename))
        {
            string content = File.ReadAllText(filename);
            string[] parts = content.Split('|');
            PlayerName = parts[0];
            Level = int.Parse(parts[1]);
            Health = int.Parse(parts[2]);
            Score = int.Parse(parts[3]);
        }
    }
}
```

---

18. Koneksi Database SQL Server

Dasar Koneksi

```csharp
using System.Data;
using System.Data.SqlClient;

// Connection string
string connectionString = "Data Source=localhost;Initial Catalog=nama_database;Integrated Security=True";

// Atau dengan username password
string connString = "Server=localhost;Database=hotelnew;User Id=sa;Password=12345;";

// ======= SELECT (Membaca Data) =======
public void LoadPlayers()
{
    string query = "SELECT * FROM players";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlCommand cmd = new SqlCommand(query, conn);
        
        try
        {
            conn.Open();
            SqlDataReader reader = cmd.ExecuteReader();
            
            while (reader.Read())
            {
                int id = reader.GetInt32(0);
                string name = reader.GetString(1);
                int level = reader.GetInt32(2);
                
                Console.WriteLine($"ID: {id}, Name: {name}, Level: {level}");
            }
        }
        catch (Exception ex)
        {
            MessageBox.Show("Error: " + ex.Message);
        }
    }
}

// ======= SELECT dengan Parameter (Cegah SQL Injection) =======
public Player GetPlayerById(int playerId)
{
    string query = "SELECT * FROM players WHERE id = @id";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlCommand cmd = new SqlCommand(query, conn);
        cmd.Parameters.AddWithValue("@id", playerId);
        
        conn.Open();
        SqlDataReader reader = cmd.ExecuteReader();
        
        if (reader.Read())
        {
            Player player = new Player();
            player.Id = reader.GetInt32(0);
            player.Name = reader.GetString(1);
            player.Level = reader.GetInt32(2);
            return player;
        }
    }
    return null;
}

// ======= INSERT (Menambah Data) =======
public bool InsertPlayer(string name, int level)
{
    string query = "INSERT INTO players (name, level) VALUES (@name, @level)";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlCommand cmd = new SqlCommand(query, conn);
        cmd.Parameters.AddWithValue("@name", name);
        cmd.Parameters.AddWithValue("@level", level);
        
        try
        {
            conn.Open();
            int rowsAffected = cmd.ExecuteNonQuery();
            return rowsAffected > 0;
        }
        catch (Exception ex)
        {
            MessageBox.Show("Error: " + ex.Message);
            return false;
        }
    }
}

// ======= UPDATE (Mengedit Data) =======
public bool UpdatePlayerLevel(int playerId, int newLevel)
{
    string query = "UPDATE players SET level = @level WHERE id = @id";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlCommand cmd = new SqlCommand(query, conn);
        cmd.Parameters.AddWithValue("@level", newLevel);
        cmd.Parameters.AddWithValue("@id", playerId);
        
        conn.Open();
        int rowsAffected = cmd.ExecuteNonQuery();
        return rowsAffected > 0;
    }
}

// ======= DELETE (Menghapus Data) =======
public bool DeletePlayer(int playerId)
{
    string query = "DELETE FROM players WHERE id = @id";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlCommand cmd = new SqlCommand(query, conn);
        cmd.Parameters.AddWithValue("@id", playerId);
        
        conn.Open();
        int rowsAffected = cmd.ExecuteNonQuery();
        return rowsAffected > 0;
    }
}

// ======= LOGIN / CEK USERNAME PASSWORD =======
public bool Login(string username, string password)
{
    string query = "SELECT * FROM users WHERE username = @username AND password = @password";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlCommand cmd = new SqlCommand(query, conn);
        cmd.Parameters.AddWithValue("@username", username);
        cmd.Parameters.AddWithValue("@password", password);
        
        conn.Open();
        SqlDataReader reader = cmd.ExecuteReader();
        
        // IF (dr.HasRows) - pintu gerbang login
        if (reader.HasRows)
        {
            return true;  // Login berhasil
        }
        else
        {
            return false; // Login gagal
        }
    }
}

// ======= MENAMPILKAN DATA KE DataGridView =======
public void LoadDataToGridView(DataGridView dgv)
{
    string query = "SELECT * FROM players";
    
    using (SqlConnection conn = new SqlConnection(connectionString))
    {
        SqlDataAdapter adapter = new SqlDataAdapter(query, conn);
        DataTable dataTable = new DataTable();
        
        try
        {
            conn.Open();
            adapter.Fill(dataTable);
            dgv.DataSource = dataTable;
        }
        catch (Exception ex)
        {
            MessageBox.Show("Error: " + ex.Message);
        }
    }
}
```

---

19. Ringkasan Cepat

Tipe Data Paling Sering Dipakai

Keyword Contoh Kapan Pakai
int int level = 5; Angka bulat (level, score, id)
string string name = "Faris"; Teks (nama, deskripsi)
bool bool isAlive = true; Kondisi true/false
float float speed = 5.5f; Angka desimal (kecepatan)
List<T> List<string> items; Kumpulan data dinamis
Dictionary<K,V> Dictionary<string,int> Data pairing key-value

Method Paling Sering Dipakai

Method Fungsi
Convert.ToInt32() String → int
ToString() Angka → string
int.Parse() String → int (bisa error)
int.TryParse() String → int (aman)
MessageBox.Show() Tampil pesan di Windows Forms
Console.WriteLine() Tampil di console

Koneksi Database Paling Sering

Method Fungsi
SqlConnection Koneksi ke database
SqlCommand Menjalankan query
SqlDataReader Membaca hasil SELECT
ExecuteNonQuery() Untuk INSERT/UPDATE/DELETE
ExecuteReader() Untuk SELECT
Parameters.AddWithValue() Parameter query (cegah SQL Injection)

---

Dokumentasi lengkap syntax C# untuk keperluan LKS Game Faris.
