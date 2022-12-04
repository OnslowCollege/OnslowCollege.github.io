---
title: Password Checker
nav_exclude: true
---

# Task 1: Password Checker

Create a program that allows one user to specify a password, then allows another user to guess the password.

## 1.1 Requirements

1. The program must ask the user for a password. The password must conform to the following criteria:
    1. It may only be four characters in length
    2. It may only contain the characters ``1``, ``2``, ``3``, or ``4``
2. Clear the screen by printing 100 blank links so that the second user can't see the password
3. The program then asks another user to guess the password
4. The user has up to 10 guesses
5. For each guess, print out the digit, replacing each digit with the following:
    1. For each correct guess, print 🟢
    2. For each wrong guess, print 🟥
6. At the end of the game, print out the correct and incorrect guess lines.
7. If the user guesses correctly within 10 guesses, congratulate them for guessing correctly
    - If the user does **not** guess correctly, reveal the password

## 1.2 Hint

Strings can be treated the same as lists:
- They can be accessed with a subscript
- You can use a for loop on a string
  - Each character in the string is the individual list item

## 1.3 Example output

### Player 1 sets a password

```
Welcome to Password Checker!
Player 1 will enter a 4-digit password containing 1, 2, 3, or 4.
Player 2 will guess the password.

Player 1, enter a password: abcd
Sorry, the password must only contain 1, 2, 3, or 4.

Player 1, enter a password: 1239
Sorry, the password must only contain 1, 2, 3, or 4.

Player 1, enter a password: 1234
```

After this, print 100 empty lines.

### Player 2 guesses the password

```
Player 2, guess the password: 1323
🟢 🟥 🟥 🟥

Player 2, guess the password: 1432
🟢 🟥 🟢 🟥

Player 2, guess the password: 1234
🟢 🟢 🟢 🟢

🟢 🟥 🟥 🟥
🟢 🟥 🟢 🟥
🟢 🟢 🟢 🟢

Congratulations! You guessed the password.
```

### Player 2 fails to guess the password

```
Player 2, guess the password: 4321
🟥 🟥 🟥 🟥

Player 2, guess the password: 4123
🟥 🟥 🟥 🟥

Player 2, guess the password: 4443
🟥 🟥 🟥 🟥

Player 2, guess the password: 2222
🟥 🟢 🟥 🟥

Player 2, guess the password: 3221
🟥 🟢 🟥 🟥

Player 2, guess the password: 4231
🟥 🟢 🟢 🟥

Player 2, guess the password: 2341
🟥 🟥 🟥 🟥

Player 2, guess the password: 3333
🟥 🟥 🟢 🟥

Player 2, guess the password: 1221
🟢 🟢 🟥 🟥

Player 2, guess the password: 1231
🟢 🟢 🟢 🟥

🟥 🟥 🟥 🟥
🟥 🟥 🟥 🟥
🟥 🟥 🟥 🟥
🟥 🟢 🟥 🟥
🟥 🟢 🟥 🟥
🟥 🟢 🟢 🟥
🟥 🟥 🟥 🟥
🟥 🟥 🟢 🟥
🟢 🟢 🟥 🟥
🟢 🟢 🟢 🟥

Sorry, you did not guess in time.
The password was: 1234
```

# Task 2: Extension

## 2.1 Requirements

Improve the game with the following features:

1. Allow the password to contain all digits (0 to 9)
2. Instead of asking for a password, generate a random one
3. If a user guesses a correct digit but it is in the wrong location, print 🔶
4. When printing the guess lines at the end, also tell the user how many guesses they made.

## 2.2 Example output

If the password is ``1234``:

```
Player 2, guess the password: 1337
🟢 🔶 🟢 🟥

Player 2, guess the password: 1733
🟢 🟥 🟢 🔶

Player 2, guess the password: 1234
🟢 🟢 🟢 🟢

🟢 🔶 🟢 🟥
🟢 🟥 🟢 🔶
🟢 🟢 🟢 🟢

Congratulations! You guessed the password in 3 guesses.
```