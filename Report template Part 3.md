# **Assignment 1- Part 3 \- Report**

Shahyah Darioosh

## Code description

What the code does:

The code take in the cipher as a string input, and then goes through each character, and shifts it as long as it does not match the characters meant to be ignored. The algorithm then shifts each character by a specified amount that increases each cycle, and print out each converted text, and the amount it is shifted by.

How to run the makefile:
- Type "make"
- type "./mc_cipher"
- Enter the cipher text in the terminal when prompted


## Attack method

I used a brute force method which tries every possible shift of the english alphabet to find the correct text. The assumptions I made are the ones given in the assignment 1 document, and I created a set that ignores them (I named the set "map" as I intended to use a map, but decided not to, and forgot to change the name, only just realized).

## Alternative method

Another way to decrypt the text potentially faster is using frequency analysis. To do this we would find what the most common letter in the cipher text is, and assume it represents a common english letter like the letter "e" for instance. Based on that assumption we would calculate the most likely shift. To make my code do that I would need to modify it to find the most common letter in the cipher, calculate what shift is needed to make it represent e, and decrypt using that shift instead of trying each one. If that doesn't work you can move on to the second most common letter until you get the right text.

## Results

Key = 7 left, 19 right

Plaintext:

may it be a light to you i@n dark places, when al\$l other light\$s go out

