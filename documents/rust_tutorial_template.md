# Rust Tutorial Project — Principles of Programming Languages

> **สำหรับนักศึกษา:** ใช้ไฟล์นี้เป็น Template สำหรับจัดทำบทเรียน Rust ของกลุ่ม  
> **Topic No.:** `XX`  
> **Topic Name:** `[ชื่อหัวข้อ]`  
> **Group No.:** `XX`

---

## 1. Members

| # | Name | Student ID | GitHub Username | Main Responsibility |
|---|---|---|---|---|
| 1 | `[ชื่อ-นามสกุล]` | `[รหัส]` | `@[username]` | Concept + Code |
| 2 | `[ชื่อ-นามสกุล]` | `[รหัส]` | `@[username]` | Code + Demo |
| 3 | `[ชื่อ-นามสกุล]` | `[รหัส]` | `@[username]` | Rust vs Other Language + PPL |
| 4 | `Sothea Sokea` | `670710258` | `@sotheasokea` | Exercises + Common Mistakes |

---

## 2. Learning Objectives

หลังจากศึกษา Topic นี้แล้ว ผู้เรียนสามารถ:

1. `[อธิบายแนวคิดสำคัญได้]`
2. `[เขียนโปรแกรม Rust ที่เกี่ยวข้องได้]`
3. `[วิเคราะห์พฤติกรรม/กฎของภาษาได้]`
4. `[เปรียบเทียบ Rust กับภาษาอื่นได้]`

---

## 3. Introduction

อธิบายว่า Topic นี้คืออะไร มีความสำคัญอย่างไร และใช้แก้ปัญหาอะไรในการเขียนโปรแกรม

`[เขียนเนื้อหาที่นี่]`

---

## 4. Key Concepts

### 4.1 `[Concept 1]`

**คำอธิบาย**

`[อธิบายแนวคิด]`

**ตัวอย่าง**

```rust
fn main() {
    println!("Hello, Rust!");
}
```

**Explanation**

`[อธิบายว่า code ทำงานอย่างไร]`

---

### 4.2 `[Concept 2]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.3 `[Concept 3]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.4 `[Concept 4 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.5 `[Concept 5 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

## 5. Important Syntax / Rules

| Syntax / Rule | Meaning | Example |
|---|---|---|
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |

### Important Rules

1. `[กฎสำคัญข้อที่ 1]`
2. `[กฎสำคัญข้อที่ 2]`
3. `[กฎสำคัญข้อที่ 3]`

---

## 6. Runnable Code Examples

> **ข้อกำหนด:** Code ทุกตัวต้อง Compile และ Run ได้จริงก่อนนำมาใส่ในเอกสาร

### Example 1 — `[ชื่อ Example]`

**Purpose:** `[ต้องการสาธิตอะไร]`

```rust
fn main() {
    // Write your runnable Rust code here
}
```

**Expected Output**

```text
[expected output]
```

**Explanation**

`[อธิบาย code ทีละส่วนที่สำคัญ]`

---

### Example 2 — `[ชื่อ Example]`

**Purpose:** `[ต้องการสาธิตอะไร]`

```rust
fn main() {
    // Write your runnable Rust code here
}
```

**Expected Output**

```text
[expected output]
```

**Explanation**

`[อธิบาย code]`

---

## 7. Common Mistakes

### Mistake 1 — `การพยายามใช้ค่าที่ถูกย้าย (Move) ไปแล้ว`

**Problem**

`เมื่อ my_name ถูกส่งไปยังฟังก์ชัน print_name() สิทธิ์ความเป็นเจ้าของ (ownership) ของ String จะถูกย้ายไปยังฟังก์ชันนั้น ดังนั้น my_name จึงไม่สามารถนำมาใช้งานต่อใน main() ได้`

**Incorrect Code**

```rust
fn print(message: String){
  println!("{}", message);
}

fn main(){
   let message = String::from("It's not okay!");
   print(message);
   println!("{}", message);
}
```

**Correct Code**

```rust
fn print(message: String){
  println!("{}", message);
}

fn main(){
   let message = String::from("It's not okay!");
   print(message.clone());
   println!("{}", message);
}
```

**Why?**

`.clone() จะสร้าง สำเนาแบบ deep copy ของ String จัดสรรหน่วยความจำ heap ใหม่ แต่มีเนื้อหาเดียวกัน ตัว clone นี่แหละที่จะถูกย้ายเข้าไปใน print ส่วน message ตัวเดิมใน main ไม่ถูกแตะต้องเลย จึงยังใช้งานต่อได้หลังจากนั้น`

---
### Mistake 2 — `เข้าใจผิดว่าการ assign คือการ copy ทั้งที่จริงๆ คือการ move`

**Problem**

`มาจากภาษาอย่าง Python, Java หรือ JS การเขียน let s2 = s1; อาจดูเหมือนแค่สร้างตัวแปรตัวที่สองที่ชี้ไปยังข้อมูลเดียวกัน แล้วใช้ได้ทั้งสองชื่อ แต่ใน Rust สำหรับ type ที่ไม่ใช่ Copy นี่คือการ move ไม่ใช่การ copy s1 จะใช้งานไม่ได้ทันทีที่ s2 ถูกสร้างขึ้น`

**Incorrect Code**

```rust
fn main() {
    let s1 = String::from("move not copy");
    let s2 = s1;              // ความเป็นเจ้าของถูกย้ายจาก s1 ไป s2
    println!("{}", s1);       // ERROR: s1 ใช้งานไม่ได้แล้ว
}
```

**Correct Code**

```rust
fn main() {
    let s1 = String::from("move not copy");
    let s2 = s1.clone();           
    println!("{}", s1);       
}
```

**Why?**

`ใช้ .clone() ถ้าต้องการให้มีเจ้าของสองตัวจริงๆ ที่เป็นอิสระจากกัน หรือใช้แค่ s2 ต่อไป แล้วเลิกพยายามใช้ s1`

---
### Mistake 3 — `Move บางส่วนออก struct (Partial move)`

**Problem**

`การย้าย field เดียวออกจาก struct จะทำให้ struct นั้น "ใช้งานไม่ได้บางส่วน" จะใช้ struct ทั้งก้อน (หรือ field ที่ถูกย้ายไปนั้น) อีกไม่ได้ ถึงแม้ field อื่นๆ จะยังใช้งานได้ปกติก็ตาม จุดนี้มักทำให้คนงงตอนแรกที่เจอ เพราะ error message อาจดูสับสน struct ยัง "มีอยู่" แต่บาง field ในนั้นใช้ไม่ได้แล้ว`

**Incorrect Code**

```rust
struct User {
    name: String,
    age: u32,
}

fn main() {
    let user = User { name: String::from("Alice"), age: 30 };

    let name = user.name;         // ย้ายเฉพาะ field name ออกมา
    println!("{}", user.name);    // ERROR: user.name ถูกย้ายไปแล้ว
    println!("{}", user.age);     // ใช้ได้ปกติ — age เป็น Copy ไม่ได้ถูกย้าย
}
```

**Correct Code**

```rust
struct User {
    name: String,
    age: u32,
}

fn main() {
    let user = User { name: String::from("Alice"), age: 30 };

    let name = user.name.clone();
    println!("{}", user.name);    
    println!("{}", user.age);     
}
```

**Why?**

`clone field นั้นถ้าต้องการใช้ทั้งสองที่ หรือ destructure struct ทั้งหมดแล้วสร้างใหม่ตามที่ต้องการ หรือจัดโครงสร้างโค้ดใหม่ให้การ move เกิดขึ้นเป็นลำดับสุดท้าย`

---
### Mistake 4 — `Move ค่าเข้าไปใน loop แล้วพยายามใช้ซ้ำ`

**Problem**

`การเรียก greet(name) ครั้งแรกจะย้าย name เข้าไปในฟังก์ชัน พอถึงรอบถัดไปของ loop name ก็ไม่มีอยู่แล้ว compiler จะฟ้องว่าการเรียกครั้งที่สองใช้ค่าที่ถูกย้ายไปแล้ว นี่เป็นข้อผิดพลาดที่พบบ่อยมากเวลาแปลงโค้ดแบบ "loop ที่ใช้ตัวแปรซ้ำ" มาจากภาษาอื่น`

**Incorrect Code**

```rust
fn main() {
    let name = String::from("Alice");

    for i in 0..3 {
        greet(name);   // ERROR รอบที่ 2: name ถูกย้ายไปแล้ว
    }
}

fn greet(name: String) {
    println!("Hello, {}", name);
}
```

**Correct Code**

```rust
fn main() {
    let name = String::from("Alice");

    for i in 0..3 {
        println!("Hello, {}", name);
    }
}
// another way is using clone when we want to use function
fn greet(name: String) {
    println!("Hello, {}", name);
}
```

**Why?**

`clone ข้างในลูปถ้าต้องการสำเนาใหม่ทุกรอบ หรือจัดโครงสร้างโค้ดใหม่ให้ฟังก์ชันรับค่าไปแล้ว return กลับมา`

---

### Mistake 5 — `Anti-Pattern: "Clone ทุกอย่าง"`

**Problem**

`แม้จะไม่ใช่ข้อผิดพลาดระดับคอมไพเลอร์ แต่นี่คือข้อผิดพลาดทางพฤติกรรม เมื่อ Borrow Checker แจ้งเตือนข้อผิดพลาด ผู้เริ่มต้นมักจะใส่ .clone() ไว้ในทุกตัวแปรเพียงเพื่อบังคับให้โค้ดสามารถคอมไพล์ผ่าน`

**Incorrect Code**

```rust
struct User {
    name: String,
    email: String,
    bio: String,
}

fn print_name(name: String) {   // รับแบบ owned โดยไม่จำเป็น
    println!("{}", name);
}

fn main() {
    let user = User {
        name: String::from("Alice"),
        email: String::from("alice@su.ac.th"),
        bio: String::from("no bio added"),
    };

    print_name(user.name.clone());   // clone() ทั้งที่แค่จะ print เฉยๆ
    println!("{}", user.name);       // ต้องใช้ user.name ต่อ เลย clone ไปก่อน
}
```

**Correct Code**

```rust
struct User {
    name: String,
    email: String,
    bio: String,
}

fn print_name(name: &str) {      // ยืมแค่ &str แทนที่จะรับ owned String
    println!("{}", name);
}

fn main() {
    let user = User {
        name: String::from("Alice"),
        email: String::from("alice@su.ac.th"),
        bio: String::from("no bio added"),
    };

    print_name(&user.name);      // แค่ยืม ไม่ต้อง clone
    println!("{}", user.name);   // ยังใช้งานได้ปกติ เพราะไม่มีอะไรถูกย้ายหรือลบไปไหน
}
```

**Why?**

`การถอยกลับมาทบทวนโครงสร้างโปรแกรมใหม่: พิจารณาว่าตัวแปรใดควรเป็นเจ้าของข้อมูลอย่างแท้จริง และให้ส่วนที่เหลือในโค้ดทำการยืม (Borrow) ไปใช้แทน`

---

## 8. Exercises

> จัดทำแบบฝึกหัด **2 ข้อ** ที่สอดคล้องกับ Topic และมีระดับความยากเหมาะสม

### Exercise 1 — `Clone or Lose It`

**Problem**

ให้ฟังก์ชัน `describe(item: String) -> String` ที่รับความเป็นเจ้าของ `String` เข้ามา แล้ว return `String` ใหม่ในรูปแบบ `"Item: {item}"`
 
ใน `main` ให้ทำตามนี้:
1. สร้างตัวแปร `String` ชื่อ `item` ที่มีค่าเป็น `"Book"`
2. เรียก `describe(item)` แล้ว print ผลลัพธ์
3. print `item` อีกครั้งหลังจากนั้น

เขียน main โดยไม่เปลี่ยนพฤติกรรมของ `describe` (ยังต้องรับความเป็นเจ้าของ `String` เหมือนเดิม)
```rust
fn describe(item: String) -> String {
    format!("Item: {}", item)
}
```

**Hint**

``describe` รับ `item: String` แบบ by value ดังนั้นการเรียก `describe(item)` จะย้ายความเป็นเจ้าของออกไปจาก `item` ใน `main` ต้องหาวิธีที่ทำให้ `item` ยังใช้งานได้หลังจากนั้น โดยไม่เปลี่ยน signature ของ `describe` มีคำสั่งอะไรที่ช่วยให้คุณส่ง *สำเนา* ไปแทนตัวจริงได้บ้าง?`

**Solution**

```rust
fn describe(item: String) -> String {
    format!("Item: {}", item)
}
 
fn main() {
    let item = String::from("Book");
 
    let result = describe(item.clone());   // ส่งสำเนาไป เก็บตัวจริงไว้
    println!("{}", result);
 
    println!("{}", item);   // ยังใช้งานได้ เพราะตัวจริงไม่เคยถูกย้าย
}
```

**Explanation**

เนื่องจากโจทย์มีข้อบังคับว่าห้ามเปลี่ยนโครงสร้างของฟังก์ชัน describe (ไม่สามารถเปลี่ยนให้ไปรับค่าแบบยืม หรือ Reference &String ได้) ฟังก์ชันนี้จึง บังคับ ว่าต้องรับสิทธิ์ความเป็นเจ้าของไปเท่านั้น

+วิธีแก้คือการใช้คำสั่ง .clone() เมื่อเราเรียกใช้ describe(item.clone()):

>โปรแกรมจะสร้างสำเนาของข้อความ "Book" ขึ้นมาใหม่ในหน่วยความจำ Heap อย่างสมบูรณ์แบบและแยกขาดจากกัน

>ฟังก์ชัน describe จะรับเอาสิทธิ์ความเป็นเจ้าของของ ตัวสำเนา นี้ไปใช้แทน และทำลายตัวสำเนานั้นทิ้งเมื่อฟังก์ชันทำงานจบ

>ตัวแปร item ต้นฉบับที่อยู่ใน main จะไม่เคยถูกย้ายสิทธิ์หรือถูกแตะต้องเลย มันจึงยังคงใช้งานได้ตามปกติและสามารถนำมาสั่งพิมพ์ในบรรทัดสุดท้ายได้

---

### Exercise 2 — `The Half-Moved Book`

**Problem**

`คุณได้รับ struct `Book` ที่มี field เป็น `String` สองตัว และมี loop ที่ต้องการสร้าง label สำหรับแต่ละเล่ม แล้ว print ข้อมูลเต็มของแต่ละเล่มทีหลัง`
 
```rust
struct Book {
    title: String,
    author: String,
}
 
fn make_label(title: String) -> String {
    format!("[{}]", title)
}
 
fn main() {
    let books = vec![
        Book { title: String::from("Rust programming"), author: String::from("Graydon Hoare") },
        Book { title: String::from("C programming"), author: String::from("Dennis Ritchie") },
    ];
 
    for book in books {
        let label = make_label(book.title);
        println!("{}", label);
        println!("by {} - full title: {}", book.author, book.title);
    }
}
```
โค้ดนี้ compile ไม่ผ่าน หน้าที่ของคุณคือ:
1. หาให้ได้ว่าค่าตัวไหนถูก move และ move ที่จุดไหนกันแน่
2. แก้โค้ดให้ compile ผ่าน **และ** print label, author, กับ full title ของแต่ละเล่มได้ถูกต้อง โดยไม่เปลี่ยนพฤติกรรมของ `make_label` (ยังต้องรับความเป็นเจ้าของ `String` เหมือนเดิม)
3. โบนัส: ลองเขียนวิธีแก้แบบที่สองที่ต่างออกไป (มีวิธีแก้ที่ถูกต้องมากกว่าหนึ่งวิธี)

**Hint**

`book.title` ถูกย้ายเข้าไปใน `make_label(book.title)` หลังจากบรรทัดนั้น `book.title` ยังใช้งานได้อยู่ไหม? แล้ว field อื่นของ `book` (เช่น `book.author`) ยังใช้ได้ปกติหรือเปล่า? นี่เป็นปัญหาแบบเดียวกับการเข้าถึง field ของ struct หลังจากบางส่วนถูกย้ายไปแล้ว ลองคิดดูว่า field ไหนที่ต้องรอดจนถึงหลังจากเรียกฟังก์ชันนั้น แล้วจะทำยังไงให้มันรอด

**Solution**

```rust
struct Book {
    title: String,
    author: String,
}
 
fn make_label(title: String) -> String {
    format!("[{}]", title)
}
 
fn main() {
    let books = vec![
        Book { title: String::from("Rust programming"), author: String::from("Graydon Hoare") },
        Book { title: String::from("C programming"), author: String::from("Dennis Ritchie") },
    ];
 
    for book in books {
        let label = make_label(book.title.clone());
        println!("{}", label);
        println!("by {} - full title: {}", book.author, book.title);
    }
}
```

**Explanation**

`ปัญหาคือ **partial move**: `book.title` ถูกย้ายเข้าไปใน `make_label` ดังนั้นหลังจากบรรทัดนั้น `book.title` จะใช้งานต่อใน `println!` ที่อ้างอิงถึง `book.title` อีกครั้งไม่ได้ ส่วน `book.author` ไม่ได้รับผลกระทบเพราะไม่ได้ถูกแตะต้อง`

---

## 9. PPL Perspective

> **ส่วนนี้เป็นหัวใจของรายวิชา Principles of Programming Languages**

วิเคราะห์ Topic นี้ในมุมมองของ Programming Languages

### 9.1 Syntax

`[Topic นี้เกี่ยวข้องกับ syntax อย่างไร]`

### 9.2 Semantics

`[คำสั่ง/construct เหล่านี้มีความหมายหรือพฤติกรรมอย่างไร]`

### 9.3 Type System

`[เกี่ยวข้องกับ type system อย่างไร ถ้ามี]`

### 9.4 Memory / Resource Management

`[เกี่ยวข้องกับ memory หรือ resource management อย่างไร ถ้ามี]`

### 9.5 Abstraction / Other PPL Concepts

`[อธิบาย abstraction, scope, binding, paradigm หรือแนวคิด PPL อื่นที่เกี่ยวข้อง]`

### 9.6 Why Rust?

`[Rust ใช้แนวคิดนี้เพื่อเพิ่ม safety, reliability หรือ performance อย่างไร]`

---

## 10. Rust vs. Other Language

**Comparison Language:** `[Python / C / C++ / Java / Kotlin / ...]`

| Aspect | Rust | Other Language |
|---|---|---|
| Syntax | `[อธิบาย]` | `[อธิบาย]` |
| Semantics / Behavior | `[อธิบาย]` | `[อธิบาย]` |
| Type System | `[อธิบาย]` | `[อธิบาย]` |
| Memory Management | `[อธิบาย]` | `[อธิบาย]` |
| Safety | `[อธิบาย]` | `[อธิบาย]` |

### Rust Example

```rust
// Rust code
```

### `[Other Language]` Example

```python
# Other language code
```

### Analysis

`[อธิบายความแตกต่างที่สำคัญ และเหตุผลด้านการออกแบบภาษา]`

---

## 11. Teach Your Topic

การนำเสนอมีสมาชิก **4 คน คนละประมาณ 5 นาที**

| Member | Responsibility | Time |
|---|---|---:|
| Member 1 | Concept + Short Code Illustration | 5 min |
| Member 2 | Detailed Code + Live Demo | 5 min |
| Member 3 | Rust vs Other Language + PPL Analysis | 5 min |
| Member 4 | Exercises + Common Mistakes + Challenge | 5 min |

### Individual Contribution

**Member 1**

`[สิ่งที่รับผิดชอบ]`

**Member 2**

`[สิ่งที่รับผิดชอบ]`

**Member 3**

`[สิ่งที่รับผิดชอบ]`

**Member 4**

`[สิ่งที่รับผิดชอบ]`

> สมาชิกทุกคนต้องสามารถอธิบาย Code ของกลุ่มได้ ไม่ใช่เฉพาะส่วนที่ตนเองเขียน

---

## 12. References

> แนะนำให้มีอย่างน้อย **4 แหล่งอ้างอิง** และควรใช้เอกสารทางการเป็นหลัก

1. `[The Rust Programming Language — Rust Book]`
2. `[Rust by Example / Rust Reference]`
3. `[Official documentation ที่เกี่ยวข้องกับ Topic]`
4. `[แหล่งอ้างอิงเพิ่มเติม]`

---

## 13. AI Usage Declaration

สามารถใช้ AI เป็นเครื่องมือช่วยเรียนรู้และพัฒนาได้ แต่สมาชิกทุกคนต้องเข้าใจและสามารถอธิบายผลงานของกลุ่มได้

| AI Tool | Purpose | How the Result Was Verified |
|---|---|---|
| `[เช่น ChatGPT]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |
| `[AI tool]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |

### Declaration

- [ ] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [ ] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [ ] ระบุการใช้ AI อย่างโปร่งใส

**รายละเอียดการใช้ AI**

`[อธิบายว่าใช้ AI ในขั้นตอนใด และสมาชิกตรวจสอบผลลัพธ์อย่างไร]`

---

## 14. GitHub Contribution

| Member | Issues | Commits | Pull Requests | Code Reviews | Contribution |
|---|---:|---:|---:|---:|---|
| Member 1 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 2 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 3 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 4 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |

### Teamwork Reflection

**How did your team collaborate?**

`[อธิบายกระบวนการทำงานร่วมกัน]`

**Problems encountered**

`[ปัญหาที่พบ]`

**How did you solve them?**

`[วิธีแก้ปัญหา]`

---

## 15. Final Checklist

- [ ] Learning Objectives ครบ 3–4 ข้อ
- [ ] Key Concepts ครบถ้วน
- [ ] Syntax / Rules
- [ ] Runnable Code Examples
- [ ] Code Compile และ Run ได้จริง
- [ ] Common Mistakes
- [ ] Exercises 2 ข้อ พร้อม Solutions
- [ ] PPL Perspective
- [ ] Rust vs Other Language
- [ ] References อย่างน้อย 4 แหล่ง
- [ ] AI Usage Declaration
- [ ] GitHub Contribution
- [ ] สมาชิกทั้ง 4 คนมีส่วนร่วม
- [ ] สมาชิกทั้ง 4 คนพร้อมนำเสนอคนละ 5 นาที
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ของกลุ่มได้

---

## Submission Information

**Repository:** `[GitHub repository URL]`

**Chapter Path:** `[เช่น chapters/01-introduction/]`

**Final PR:** `#[PR number]`

**Submitted by:** `[Group XX]`

**Date:** `[YYYY-MM-DD]`
