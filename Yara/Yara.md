# 🚀 Introduction to Yara

Welcome! In this lesson, you'll build on your basic Linux skills and learn about **Yara**—a powerful tool in information security. This isn't a test, but a hands-on guide to help you experiment and understand how Yara works. 🧑‍💻

> **Fun Fact:** Yara stands for "Yet Another Ridiculous Acronym" and was developed by Victor M. Alvarez (@plusvic) and @VirusTotal.  
> 👉 [Check the GitHub repo here.](https://github.com/VirusTotal/yara)

---

## 🧐 What is Yara?

> "The pattern matching swiss knife for malware researchers (and everyone else)"  
> — Virustotal, 2020

Yara helps you identify information in files using both binary and textual patterns (like hexadecimal values and strings).  
**Yara rules** are used to label these patterns—often to detect if a file is malicious based on its features.

### 💡 Example: Strings in Malware

Just like in programming, malware uses strings to store data. Here are some examples:

| Type        | Data                                 | Description                                 |
|-------------|--------------------------------------|---------------------------------------------|
| Ransomware  | `12t9YDPgwueZ9NyMgw519p7AA8isjr6SMw` | Bitcoin Wallet for ransom payments          |
| Botnet      | `12.34.56.7`                         | IP address of the Command and Control (C&C) |

---

## ❓ Quick Questions

- **What is the name of the base-16 numbering system that Yara can detect?**  
       `hexadecimal` ✅

- **Would the text "Enter your Name" be a string in an application?**  
       `Yay` ✅

---

# 🛠️ Your First Yara Rule

![image](yara.png)

Yara uses its own simple rule language. Every Yara command needs:

1. The rule file you create
2. The file, directory, or process ID to scan

**Example:**  
To use `myrule.yar` on a directory called `somedirectory`:
```bash
yara myrule.yar somedirectory
```
`.yar` is the standard extension for Yara rules.

### ✍️ Let's Create a Basic Rule

1. Create a file:
        ```bash
        touch somefile
        ```
2. Create your first rule file:
        ```bash
        touch myfirstrule.yar
        ```
3. Edit `myfirstrule.yar` and add:
        ```yara
        rule examplerule {
                      condition: true
        }
        ```

This rule checks if the file exists. If it does, Yara outputs the rule name.

**Run it:**
```bash
yara myfirstrule.yar somefile
```
If the file exists, you'll see:
```
examplerule somefile
```
If not, you'll get an error.

---

# 🔍 Yara Rule Anatomy

Yara rules have several sections:

| Keyword   | Description                                      |
|-----------|--------------------------------------------------|
| meta      | Descriptive info (doesn't affect the rule logic) |
| strings   | Patterns to search for (text or hex)             |
| condition | The logic that triggers a match                  |

### 📝 Example: Searching for Strings

```yara
rule helloworld_checker {
              strings:
                            $hello_world = "Hello World!"
              condition:
                            $hello_world
}
```
This matches any file containing "Hello World!".

#### 🔄 Case Variations

To match different cases:
```yara
rule helloworld_checker {
              strings:
                            $hello_world = "Hello World!"
                            $hello_world_lowercase = "hello world"
                            $hello_world_uppercase = "HELLO WORLD"
              condition:
                            any of them
}
```
Now, any of those strings will trigger the rule.

---

## ⚙️ Advanced Conditions

You can use operators like `<=`, `>=`, `!=` and combine conditions with `and`, `or`, `not`.

**Example:**
```yara
rule helloworld_checker {
              strings:
                            $hello_world = "Hello World!"
              condition:
                            #hello_world <= 10
}
```
This matches if "Hello World!" appears 10 times or less.

**Combining Conditions:**
```yara
rule helloworld_checker {
              strings:
                            $hello_world = "Hello World!"
              condition:
                            $hello_world and filesize < 10KB
}
```
This matches only if the file contains "Hello World!" **and** is smaller than 10KB.

---