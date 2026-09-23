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

### Mistake 2 — `การคืนค่า Reference ของตัวแปรแบบ Local (Dangling Pointer)`

**Problem**

`message เป็นตัวแปร local ที่ถูกสร้างขึ้นภายในฟังก์ชัน เมื่อฟังก์ชันทำงานจบและ return ออกมา ตัวแปร message จะหลุดออกจาก scope และถูก drop (หน่วยความจำของมันจะถูกคืนกลับไป/ถูกลบทิ้งไป)`

**Incorrect Code**

```rust
fn get_message()-> &String{
  let message = String::from("will this work?");
  &message
}

fn main(){
   let message = get_message();
}
```

**Correct Code**

```rust
fn get_message()-> String{
  let message = String::from("will this work?");
  message
}

fn main(){
   let message = get_message();
   println!("{}", message);
}
```

**Why?**

`return message ตัวมันเอง ไม่ใช่ reference ของมัน ใน Rust เมื่อ return ค่าแบบเป็นเจ้าของ (owned value) แบบนี้ ความเป็นเจ้าของ (ownership) จะถูกย้าย ออกจากฟังก์ชันไปให้ผู้เรียกใช้ String จะไม่ถูก drop ตอนฟังก์ชันจบ แต่จะถูกส่งต่อไปแทน และตัวแปร message ใน main ก็จะกลายเป็นเจ้าของข้อมูลตัวเดียวกันนี้แทน`

---
### Mistake 3 — `การใช้ Mutable และ Immutable Reference ปะปนกัน`

**Problem**

`ในเวลาเดียวกัน คุณสามารถมี immutable reference (&T) ได้หลายตัว หรือ mutable reference (&mut T) ได้แค่ตัวเดียว แต่จะมี ทั้งสองแบบพร้อมกันไม่ได้`

**Incorrect Code**

```rust
fn main(){
   let mut message = String::from("one kind active, different can't borrow");
   let m1 = &message;
   let m2 = &message;
   let m3 = &mut message;

   println!("{} {} {}", m1, m2, m3);
}
```

**Correct Code**

```rust
fn main(){
   let mut message = String::from("one kind active, different can't borrow");
   let m1 = &message;
   let m2 = &message;
   println!("{} {}", m1, m2);

   let m3 = &mut message;
   println!("{}", m3);
}
```

**Why?**

`+ m1, m2 ถูกใช้ครั้งสุดท้ายที่ println!("{} {}", m1, m2); → หลังจากบรรทัดนี้ borrow ของทั้งคู่ก็ "จบ" ทันที (ไม่ต้องรอถึงปิด } ของ main)`

`+ พอถึงบรรทัด let m3 = &mut message; ไม่มี immutable borrow ไหนยังค้างอยู่แล้ว เพราะฉะนั้นการสร้าง mutable borrow (m3) จึงไม่ไปซ้อนทับกับ m1, m2`

---
### Mistake 4 — `การแก้ไข Collection ในขณะที่กำลังวนลูป (Iterating) อยู่`

**Problem**

`ไม่สามารถเปลี่ยนขนาดหรือข้อมูลภายใน Vector หรือ Map ได้ในขณะที่กำลังวนลูปอ่านค่าอยู่ เนื่องจากตัวลูปเองกำลังถือครอง Reference ของ Collection นั้นเอาไว้`

**Incorrect Code**

```rust
fn main(){
   let mut numbers = vec![1, 2, 3];

  for num in &numbers {
      if *num == 2 {
          numbers.push(4);
      }
  }
}
```

**Correct Code**

```rust
fn main(){
  let mut numbers = vec![1, 2, 3];
  let mut nums = vec![];
  for num in &numbers {
      if *num == 2 {
          nums.push(4);
      }
  }
  numbers.extend(nums);
  println!("{:?}", numbers);
}
```

**Why?**

`ในระหว่าง loop for num in &numbers จะถือ immutable borrow ของ numbers ตลอดทั้ง loop แต่สังเกตว่าในนี้ ไม่มีตรงไหนพยายามแก้ไข numbers เลย แก้ไขแค่ nums ซึ่งเป็น Vec เปล่าๆ อีกตัวที่ไม่เกี่ยวข้องกับ borrow เดิมเลย ดังนั้นจึงไม่มีการชนกัน อ่าน numbers และเขียนลง nums ซึ่งเป็นคนละหน่วยความจำกัน ไม่มี overlap`

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

### Exercise 1 — `[ชื่อโจทย์]`

**Problem**

`[เขียนโจทย์]`

**Hint**

`[คำใบ้]`

**Solution**

```rust
// Solution code
```

**Explanation**

`[อธิบายแนวทางแก้]`

---

### Exercise 2 — `[ชื่อโจทย์]`

**Problem**

`[เขียนโจทย์]`

**Hint**

`[คำใบ้]`

**Solution**

```rust
// Solution code
```

**Explanation**

`[อธิบายแนวทางแก้]`

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
