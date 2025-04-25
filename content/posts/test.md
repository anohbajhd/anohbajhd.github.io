+++
date = '2025-04-23T11:00:00+05:00'
title = 'Don’t Trust Your Code—Test It'
tags = ['hugo', 'github', 'python', 'testing']
+++

# Why Testing Your Code Matters

When we write code, we want it to work. But sometimes, it doesn’t. That’s where **testing** comes in.

Testing helps us check if our code is doing what we want. It tells us if something is broken, so we can fix it early — before it becomes a big problem.

---

## Why Should We Test?

Let’s say you make a function that adds two numbers. You think it works. But what if it doesn’t? You don’t want to find out later, when everything depends on it.

> Testing is like asking your code:  
> **“Hey, are you really doing your job?”**

---
## Types of Testing (The Basics)

Here are the basic ones you’ll encounter:

| **Type**          | **What it Tests**                                |
|-------------------|--------------------------------------------------|
| **Unit Testing**   | Small pieces of code, like functions             |
| **Integration**    | How different parts of code work together        |
| **Functional**     | Whole features from a user perspective           |
| **Regression**     | Makes sure old features still work after changes |

> As a beginner, we’ll mostly be doing **unit testing**.

## Tools We Use: `pytest`

We'll use **`pytest`**, which is a powerful and easy-to-use testing tool in Python.

### 🔧 Install `pytest`:

If you don’t have it yet, run this command:

![command screenshot](/python/sa1.png)

## A Simple Way to Test: `pytest`

In Python, there’s a tool called **pytest**. It helps you test your code easily.

For example:

![code screenshot](/python/sa.png)

---

### You write a function:

#### `def` — Define a Function

- `def` is short for **define**.
- It's used to **create a function** in Python.

![code screenshot](/python/sb.png)

#### `assert` — Check if Something is True

- `assert` is used to check if a condition is true.
- If it **is true**, Python does nothing and continues.
- If it’s **false**, Python throws an `AssertionError`.

This code is checking:

- Does `add(2, 3)` give `5`?
- Does `add(0, 0)` give `0`?
- And so on.

---

## Testing with `pytest`

Put this in a file called `test_add.py`, then run this in your terminal:

![code screenshot](/python/sb.png)

If all is good, you’ll see a **green message**.  
If something is wrong, `pytest` will show you **what failed**.

---

## Why Use `pytest`?

- It’s simple to use  
- The code is easy to read  
- You get clear messages when something fails  

---

## Final Thoughts

Testing might feel boring at first.  
But it **saves you time and trouble later**.

Start small — test just one function.  
It’s a good habit to build.

> Your code will thank you.  
> And so will your future self.