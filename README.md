# Python Fundamentals: Assignment 3

A set of three beginner Python programs covering **while loops with control statements**, **for loops**, and **functions**. Each program is written and run in a Jupyter Notebook.

## Contents

| # | Program | Concepts practiced |
|---|---------|--------------------|
| 1 | [Number Guessing Game](#1-number-guessing-game) | `while`, `break`, `continue`, `while-else`, `random` |
| 2 | [Multiplication Table Generator](#2-multiplication-table-generator) | `for`, `range()`, f-strings |
| 3 | [BMI Calculator](#3-bmi-calculator) | functions, parameters, `return`, `round()` |

## Repository structure

```
.
├── Python_Assignment_3.ipynb   # all three programs with outputs
├── Python_Funda_Assignment_3_-_While_Loop__For_loop_and_Functions.pdf   # assignment brief
└── README.md
```

## How to run

1. Install [Python 3](https://www.python.org/downloads/) and Jupyter:
   ```bash
   pip install notebook
   ```
2. Clone this repository and open the notebook:
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   jupyter notebook Python_Assignment_3.ipynb
   ```
3. Run each cell with **Shift + Enter**.

---

## 1. Number Guessing Game

**Goal:** The computer picks a random number between 1 and 10, and the user gets **3 attempts** to guess it.

**How it works**
- `random.randint(1, 10)` generates the secret number.
- A `while` loop runs as long as the user has attempts left.
- **`continue`**: an out-of-range guess is rejected and the loop restarts without using up an attempt.
- **`break`**: a correct guess ends the loop immediately.
- **`else` on the `while`**: runs only if the loop finishes without `break`, meaning the user used all attempts without guessing correctly.

```python
import random

secret_num = random.randint(1, 10)
attempts = 3

while attempts > 0:
    num = int(input("Guess the number (between 1 and 10): "))

    if num < 1 or num > 10:
        print("Your guess is out of range. Please guess a number between 1 and 10.")
        continue
    elif num > secret_num:
        print("Too high! Try again.")
    elif num < secret_num:
        print("Too low! Try again.")
    else:
        print("Congratulations! You guessed the correct number.")
        break

    attempts -= 1
    print("Attempts left:", attempts)

else:
    print("Better luck next time!")
```

**Sample output**

```
Guess the number (between 1 and 10): 15
Your guess is out of range. Please guess a number between 1 and 10.
Guess the number (between 1 and 10): 8
Too high! Try again.
Attempts left: 2
Guess the number (between 1 and 10): 4
Congratulations! You guessed the correct number.
```

---

## 2. Multiplication Table Generator

**Goal:** Print the multiplication table (1 to 10) for a number entered by the user.

**How it works**
- `range(1, 11)` produces the numbers 1 to 10 (the stop value is excluded).
- Each pass of the `for` loop calculates `i * num` and prints one line.

```python
num = int(input("Enter the number for which you want the multiplication table: "))

for i in range(1, 11):
    print(f"{num} x {i} = {num * i}")
```

**Sample output**

```
Enter the number for which you want the multiplication table: 7
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
```

---

## 3. BMI Calculator

**Goal:** Calculate Body Mass Index using the formula

```
BMI = weight (kg) / height (m)²
```

**How it works**
- `calculate_bmi(weight, height)` takes the values as **parameters** and **returns** the result.
- Input is collected outside the function, so the function can be reused with any values.
- `round(..., 2)` keeps the output to two decimal places.

```python
def calculate_bmi(weight, height):
    return weight / height ** 2

weight = float(input("Enter your weight in kg: "))
height = float(input("Enter your height in meters: "))

bmi = calculate_bmi(weight, height)
print("Your BMI is:", round(bmi, 2))
```

**Sample output**

```
Enter your weight in kg: 58
Enter your height in meters: 1.62
Your BMI is: 22.1
```

> **Note:** height must be entered in **meters** (for example `1.62`), not feet.

---

## Key takeaways

- `while-else` runs the `else` block only when the loop ends **without** `break`.
- `continue` skips the rest of the current pass; `break` leaves the loop entirely.
- `range(start, stop)` excludes the `stop` value.
- Functions with parameters and `return` are more reusable than functions that read input internally.

## Tech used

- Python 3
- Jupyter Notebook
