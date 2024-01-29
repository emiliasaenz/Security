# Work Guide: Classical Cryptography

## Part 1: Research Topics

In this section, you will research various classical cryptography topics. Each topic has a set of questions to guide your learning.

### 1. The Substitution Cipher

1. What is the substitution cipher and how does it differ from the shift cipher?

In a substitution cipher, each character in the plaintext is replaced by any different letter, following a specific system that can vary throughout the message depending on a key. This method allows for a wide range of substitutions, making the key more complex and the cipher generally more secure against basic decryption methods like frequency analysis.

<img width="637" alt="Captura de pantalla 2024-01-27 a la(s) 20 06 42" src="https://github.com/emiliasaenz/Security/assets/143628612/6924b02f-5349-4c63-8255-95d396c3eecd">

A shift cipher, involves a simpler and more uniform substitution method. The alphabet is shifted a fixed number of places either up or down. This uniform shift means the key is simply the number of positions the alphabet is shifted, making it less complex and less secure. With only 26 possible variations in the English alphabet, shift ciphers are more susceptible to being broken, especially through frequency analysis

<img width="579" alt="Captura de pantalla 2024-01-27 a la(s) 20 07 15" src="https://github.com/emiliasaenz/Security/assets/143628612/c3e5d5da-49e8-4dae-af05-f2be333fd165">

2. How can you create a substitution cipher using a keyword or a random permutation?

To create a substitution cipher using a keyword, generate a keyword that serves as the key and defines how letters from the cipher alphabet correspond to those in the plain alphabet. Any repeated letters in the keyword are first eliminated. Following this, the cipher alphabet is constructed by aligning the letters of the keyword with A, B, C, and so forth, until all letters in the keyword are utilized. Subsequently, the remaining letters of the cipher alphabet are arranged in their usual alphabetical sequence, while skipping any letters that were already included as part of the key.

<img width="647" alt="Captura de pantalla 2024-01-27 a la(s) 20 13 14" src="https://github.com/emiliasaenz/Security/assets/143628612/eb8aa6da-51df-44e7-a562-c648a83097bf">

To create a substitution cipher using a random permutation, generate a random shuffle of the alphabet, where each letter is uniquely mapped to another. This shuffled list forms the key. Encrypt the plaintext by substituting each letter with its corresponding letter in the random permutation. While this method offers better security than simple ciphers like the shift cipher, it can still be vulnerable to frequency analysis, especially in longer texts. The effectiveness of this cipher heavily relies on the randomness and unpredictability of the permutation.

3. What are the advantages and disadvantages of the substitution cipher?

Advantages: 
- Easy and straightforward to understand and implement
- Offers better security than simple shift ciphers due to a larger number of possible keys
- Faster to execute compared to complex encryption algorithms

Disadvantages:
- Can be broken by skilled cryptanalysts using frequency analysis to deduce letter mappings.
- Not suitable for encrypting very confidential data due to their relative ease of being cracked
- Securely sharing the substitution key between sender and receiver can be problematic.
- Limited Key Space due to the limited number of possible substitutions

4. How can frequency analysis be used to break a substitution cipher?

By counting how often each letter appears in the ciphertext and comparing it to the expected frequency of each letter in the language of the plaintex. Also by examing patterns such as common words, letter pairings, and grammatical rules.

5. Can you provide an example of a historical use of the substitution cipher?

The historical use of a substitution cipher is exemplified in the 16th century by Mary, Queen of Scots, during her imprisonment by Queen Elizabeth I of England, where each letter of the alphabet was substituted with a symbol or another letter. Mary utilized a substitution cipher to secretly communicate with her supporters, planning her escape and potentially plotting to assassinate Elizabeth. However, her encrypted messages were intercepted and deciphered by Elizabeth's spymaster, Sir Francis Walsingham, and his cryptanalyst, Thomas Phelippes. The cracking of this cipher exposed Mary's involvement in the Babington Plot, ultimately leading to her trial and execution for treason in 1587. 

### 2. The Affine Cipher

1. What is the affine cipher and how does it combine the shift and substitution ciphers?

The Affine cipher is a combination of monoalphabetic substitution cipher and Ceasar's shift cipher, where each letter in the alphabet is mapped to its numeric equivalent, encrypted using modular arithmetic, and converted back to a ciphertext letter. The key consists of 2 numbers, a and b. 
The 'b' value in the formula introduces a linear shift, it determines how far along the alphabet the cipher shifts each letter. The multiplication by 'a'  adds a more complex substitution pattern than a simple shift.

<img width="699" alt="Captura de pantalla 2024-01-28 a la(s) 23 34 41" src="https://github.com/emiliasaenz/Security/assets/143628612/4bd24c40-beab-4a8b-b59a-564cc8f318f4">

2. How can you encrypt and decrypt messages using the affine cipher?
   
Encryption:
The encryption function for a single letter is   

<img width="504" alt="Captura de pantalla 2024-01-28 a la(s) 23 30 33" src="https://github.com/emiliasaenz/Security/assets/143628612/f58d0842-c5a4-45de-b4f6-ba67266a7cf2">

Decryption:

For deciphering, we must find the inverse function on the ciphertext to retrieve the plaintext. The first step is to convert each of the ciphertext letters into their integer values. The decryption function is  

<img width="633" alt="Captura de pantalla 2024-01-28 a la(s) 23 54 13" src="https://github.com/emiliasaenz/Security/assets/143628612/8187729d-6dad-4b83-9afe-68d0f0eda239">

x is an inverse of a

3. What are the advantages and vulnerabilities of the affine cipher?

Advantages:

- By combining linear shifting and multiplication, the affine cipher is more complex and secure than a basic Caesar shift cipher.
- Is relatively simple to implement, requiring only basic mathematical operations
- The cipher has more key options than a simple shift cipher, as it uses two keys

Vulnerabilities:

- Is a very insecure cipher
- The Affine cipher is a substitution cipher, so all the methods that are used to cryptanalyse substitution ciphers can be used for the affine cipher. 
- Due to its vulnerabilities to various cryptographic attacks, it is not suitable for encrypting large amounts of data or highly sensitive information.


4. How can you break the affine cipher using known plaintext attacks?

Breaking the affine cipher with a known plaintext attack involves using specific pairs of plaintext and corresponding ciphertext to determine the cipher's keys. Initially, known pairs of plaintext and ciphertext are translated into numerical values based on their positions in the alphabet (e.g., A=0, B=1). With at least one pair, but ideally two, you set up equations matching the affine cipher's formula. These equations represent the relationship between the plaintext, ciphertext, and the unknown keys 'a' and 'b'. Solving these equations, often through a combination of algebraic manipulation and modular arithmetic, reveals the values of 'a' and 'b'.

For a practical example, if it's known that plaintext 'A' (0) encrypts to ciphertext 'C' (2), and 'B' (1) to 'E' (4), two equations can be formulated: 2 = (0a + b) mod 26 and 4 = (1a + b) mod 26. Solving these equations will yield the values of 'a' and 'b'. In cases where only one pair is known, a brute force approach can be used to guess 'a' and then solve for 'b'. 

5. Can you provide an example of a practical use of the affine cipher?

The affine cipher, due to its simplicity and the level of security it offers, is not commonly used in practical, modern-day applications where high-level security is required

In recreational settings like puzzle books, escape rooms, or certain types of games, the affine cipher can be used to create interesting challenges. Players might need to decrypt a message encrypted with the affine cipher to solve a puzzle or progress in the game.


### 3. The Hill Cipher

1. What is the Hill cipher and how does it differ from previous ciphers?
2. How can you encrypt and decrypt messages using the Hill cipher?
3. What are the advantages and limitations of the Hill cipher?
4. How does the Hill cipher utilize matrix operations?
5. Can you provide an example of a real-world application of the Hill cipher?

### 4. The Permutation Cipher

1. What is the permutation cipher and how does it work?
2. How can you encrypt and decrypt messages using the permutation cipher?
3. What are the strengths and weaknesses of the permutation cipher?
4. How can you break the permutation cipher using brute force or frequency analysis?
5. Can you provide an example of a historical use of the permutation cipher?


## Part 2: Cryptanalysis Research

In this section, you will research various cryptanalysis techniques for classical ciphers. Each topic has a set of questions to guide your learning.

### 1. Introduction to Cryptanalysis

1. What is cryptanalysis and why is it important in cybersecurity?
2. What are the different types of cryptanalysis techniques?
3. How does cryptanalysis differ from cryptography?
4. Can you provide an example of a famous cryptanalysis success story?
5. What are the ethical considerations in cryptanalysis?

### 2. The Affine Cipher

1. How can you break the affine cipher using known plaintext attacks?
2. What is the vulnerability of the affine cipher to modular inverses?
3. How can you improve the security of the affine cipher?
4. Can you provide an example of a real-world attack on the affine cipher?
5. What are the limitations of cryptanalysis on the affine cipher?

### 3. The Substitution Cipher

1. How can you break the substitution cipher using frequency analysis?
2. What is the vulnerability of the substitution cipher to known plaintext attacks?
3. How can you improve the security of the substitution cipher?
4. Can you provide an example of a real-world attack on the substitution cipher?
5. What are the limitations of cryptanalysis on the substitution cipher?

### 4. The Hill Cipher

1. How can you break the Hill cipher using matrix algebra?
2. What is the vulnerability of the Hill cipher to key length?
3. How can you improve the security of the Hill cipher?
4. Can you provide an example of a real-world attack on the Hill cipher?
5. What are the limitations of cryptanalysis on the Hill cipher?

### 5. The Permutation Cipher

1. How can you break the permutation cipher using brute force or frequency analysis?
2. What is the vulnerability of the permutation cipher to known plaintext attacks?
3. How can you improve the security of the permutation cipher?
4. Can you provide an example of a real-world attack on the permutation cipher?
5. What are the limitations of cryptanalysis on the permutation cipher?



# Lab Guide: Cryptography Programming Exercises

## Classic Cryptography Topics

### 1. Substitution Cipher

#### Exercise:
Write a Python function `substitution_cipher_encrypt(plaintext, key)` that takes a plaintext string and a substitution key as input and returns the corresponding ciphertext using the substitution cipher.

#### Example:
> - Plaintext: "HELLO"
> - Key: {'H': 'X', 'E': 'Y', 'L': 'Z', 'O': 'A'}
> - Ciphertext: "XYZZA"

> - Plaintext: "WORLD"
> - Key: {'W': 'Q', 'O': 'P', 'R': 'S', 'L': 'T', 'D': 'U'}
> - Ciphertext: "QPSUT"

### 2. Affine Cipher

#### Exercise:
Write a Python function `affine_cipher_encrypt(plaintext, a, b)` that takes a plaintext string and two integer values a and b as input and returns the corresponding ciphertext using the affine cipher.

#### Example:
> - Plaintext: "HELLO"
> - a: 5
> - b: 8
> - Ciphertext: "RCLLA"

> - Plaintext: "WORLD"
> - a: 3
> - b: 7
> - Ciphertext: "VXGOQ"

### 3. Hill Cipher

#### Exercise:
Write a Python function `hill_cipher_encrypt(plaintext, key)` that takes a plaintext string and a 2x2 matrix key as input and returns the corresponding ciphertext using the Hill cipher.

#### Example:
> - Plaintext: "HELLOWORLD"
> - Key: [[2, 3], [1, 4]]
> - Ciphertext: "AXDDQYBEFX"

### 4. Permutation Cipher

#### Exercise:
Write a Python function `permutation_cipher_encrypt(plaintext, key)` that takes a plaintext string and a permutation key as input and returns the corresponding ciphertext using the permutation cipher.

#### Example:
> - Plaintext: "HELLO"
> - Key: [3, 1, 4, 2, 5]
> - Ciphertext: "LHLEO"

> - Plaintext: "WORLD"
> - Key: [2, 4, 1, 5, 3]
> - Ciphertext: "OLWDR"

## Cryptanalysis Topics

### 1. Affine Cipher

Write a Python function `break_affine_cipher(ciphertext)` that takes a string `ciphertext` as input and attempts to break the affine cipher by trying all possible combinations of `a` and `b` values. The function should return the most likely plaintext obtained by decrypting the ciphertext using the correct `a` and `b` values.

Example:
```python
ciphertext = "Czggj, Tqxxa!"
plaintext = break_affine_cipher(ciphertext)
print(plaintext)
```
Output:
```
Hello, World!
```

### 2. Substitution Cipher

Write a Python function `break_substitution_cipher(ciphertext)` that takes a string `ciphertext` as input and attempts to break the substitution cipher by performing frequency analysis on the letters in the ciphertext. The function should return the most likely plaintext obtained by decrypting the ciphertext using the correct key.

Example:
```python
ciphertext = "XYZZA, CDCFA!"
plaintext = break_substitution_cipher(ciphertext)
print(plaintext)
```
Output:
```
Hello, World!
```

### 3. Hill Cipher

Write a Python function `break_hill_cipher(ciphertext, n)` that takes a string `ciphertext` and an integer `n` as input and attempts to break the Hill cipher by performing frequency analysis on the letters in the ciphertext and using matrix algebra. The function should return the most likely plaintext obtained by decrypting the ciphertext using the correct key.

Example:
```python
ciphertext = "XZGZJ, ZJGFA!"
n = 2
plaintext = break_hill_cipher(ciphertext, n)
print(plaintext)
```
Output:
```
Hello, World!
```

