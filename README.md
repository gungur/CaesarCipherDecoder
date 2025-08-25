# Caesar Cipher Decoder

## Overview

This project implements a Caesar cipher decoder in C. The program reads an encoded message from a file, prompts the user for their CS login, and uses that login as a key to calculate the number of shifts needed to decode the message using the Caesar cipher technique.

## Files

- `decode.c` - Main source code file containing the implementation
- `cipher.txt` - Input file containing the encoded message
- `decode.s` - Assembly code generated from the C source
- `decode.o` - Object file
- `decode` - Executable file
- `myfortune.txt` - Output file containing the decoded message
- `log-p1.pdf` - Work log documenting the development process
- `objectfile_contents.txt` - Disassembly of the object file
- `execfile_contents.txt` - Disassembly of the executable file

## How It Works

### Caesar Cipher
The Caesar cipher is a substitution cipher where each letter in the plaintext is shifted a fixed number of positions down or up the alphabet. In this implementation:
- Left shifts are used to encode messages
- Right shifts are used to decode messages

### Key Generation
The number of shifts required for decoding is calculated using the user's CS login:
1. The program takes the bitwise XOR of all characters in the login string
2. The result is taken modulo 26 to ensure it's within the alphabet range (1-25)
3. If the result is 0, it defaults to 1 shift

### Decoding Process
1. Read the ciphertext from `cipher.txt`
2. Prompt the user for their CS login
3. Calculate shifts needed based on the login
4. Apply right shifts to each lowercase letter in the ciphertext
5. Output the decoded plaintext

## Usage

1. Ensure `cipher.txt` exists in the same directory with the encoded message
2. Compile the program: `gcc decode.c -o decode`
3. Run the executable: `./decode`
4. Enter your CS login when prompted
5. The decoded message will be displayed

## Example

Input ciphertext: `bzm h anqqnv rnld ahsbnhmr ?`

With CS login: `gungurthi`

Output plaintext: `can i borrow some bitcoins ?`

## Implementation Details

### Functions

- `main()` - Orchestrates the decoding process
- `read_cipher_file()` - Reads the encoded message from file
- `get_login_key()` - Prompts user for CS login
- `decode()` - Applies Caesar cipher decoding
- `calculate_shifts()` - Computes shifts from login key

### Memory Management
The program uses dynamic memory allocation (`malloc`) for strings and properly handles memory for the ciphertext and login input.

### Error Handling
The program includes error checking for:
- File opening failures
- File reading errors
- User input errors

## Building from Source

```bash
gcc -Wall -std=c99 decode.c -o decode
```
