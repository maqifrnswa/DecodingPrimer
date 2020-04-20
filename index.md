# So you want to decode...

This is an intro on how one can start getting in to decoding games. While there are plenty of helpful tools and walkthroughs on the internet, many new decoders can easily become overwhelmed figuring out which tools to use or where to even start when presented with something like `IXRuZW1uZXRoZ2lsbkUgZWh0IG5pb0o=`. This primer will walk through "how to strategize" when presented with a decoding problem with examples. In the end, you'll have the basic understanding of what's happening that you can then use to try out and learn their vast number of decoding tools available on the internet. How we'll do it:

1. Learn the two ways encrypted/encoded messages are created.
   1. "Encrypting"
   1. "Encoding"
1. Recognize/guess starting points when you find an encrypted/encoded message

## How to encrypt/encode a message

To figure out how to decode, you first have to know how a messages are encoded in the first place. To make things easier, you can think of encoding as some combination of the following 2 processes:

* **Encrypting** is taking the message and rearranging or substituting the characters to hide a message. In other words, encrypting keeps the same _character set_ (e.g., ASCII characters a-z A-Z and arabic numerals 0-9) but substituties one for another or rearranges their order. For example, reversing the order of characters would encrypt `hello` as `olleh`. These methods are called **ciphers**
*  **Encoding** is kind of the converse of encrypting in that it keeps the message the same, just represents it in a different way. For example, Morse code would encode `hello` as `.... . .-.. .-.. ---`. These methods are called **codings**

That's basically it! To create an encoded/encrypted message, you do some combination of one or more of the above. To decrypt, you just do the opposite. The game then becomes, "how do I recoginize if I need to decrypt or decode, and which do I use?" To do that, we first can learn about common encryption and encoding techniques

### Common encryption techniques

The following is a quick summary of a few of the basic techniques. Encryption can generally be thought of as one of two techniques: (a) some sort of rearranging of the order and (b) substituting letters for others. Given a message, you can hide its meaning by doing things like:

#### Rearranging: Reversing the order of characters
`hello` as `olleh`

#### Rearranging: Skip Characters, skip cipher
In a **skip cipher** you write the message every _n_ characters. So id _n_=4: `abcdefgh` becomes `aebfcgdh` How to easily encrypt: write you message on mulitiple lines, each with _n_ characters. So, with _n_=4:
```
abcd
efgh
```
Then read the columns, from left to right: `ae` `bf` `cg` `dh`. To decode, write your message in rows and read down the columns. Here you may have to try different combinations to get it to work, or use something like [https://multidec.web-lab.at/skip.php](https://multidec.web-lab.at/skip.php) to do it for you for many combinations at once. For example: `aebfcgdh` is written as:
```
ae
bf
cg
dh
```
Then reading the columns: `abcdefgh`

#### Rearranging: Variants of skip cipher
There are plenty of variants to skip that play games with how many to skip at a time, which is why you'll see many online. For example, you can use a passcode to change _n_ after each character, you have a **transposition cipher** [https://www.dcode.fr/transposition-cipher](https://www.dcode.fr/transposition-cipher). You also can change _n_ in a clever way using a  **rail fence cipher** [https://en.wikipedia.org/wiki/Rail_fence_cipher](https://en.wikipedia.org/wiki/Rail_fence_cipher). Also, you don't always have to go from left to right, top to bottom, but the direction can change as well as in a **route/path cipher** [https://www.dcode.fr/route-cipher](https://www.dcode.fr/route-cipher). And there are many, many, more. The point here is that you may need to brute force trying different techniques until one "clicks." Luckily, there are many online tools to try out.

#### Substitution: Rotating number of characters, ROT ciphers
You can encrypt a message by "rotating" a certain number of characters. Here, "rotating" means exchange every letter for one _n_ letters away on the alphabet. For example, recalling Arthur C. Clarke & Stanley Kubric, the letters `HAL` can be rotated 1 letter to give us `IBM`. The letter after `h` is `i`, and so one. The letter after `z` is `a`. This is called a **ROT cipher** [https://www.dcode.fr/rot-cipher](https://www.dcode.fr/rot-cipher), the most common being **ROT13** or **Ceasar cipher**. Decrypting and encrypting  are the same, it's just that the decrypting and encrypting rotations have to equal 26. So **ROT1** encoding can be docded with **ROT25**. That's why **ROT13** is popular - it is encorypted and decrypted in the same way. Alternatively, you can encrypt a message by rotating _n_ to the left then decode by rotating _n_ to the right.

#### Substitution: Variants on ROT ciphers
You can change the _n_ of the substitution with every character. For example, if you have a password, you can use that to 
encrypt and decrypt a message. This is called **viginere cipher** [https://www.dcode.fr/vigenere-cipher](https://www.dcode.fr/vigenere-cipher). I can use the password `hello` to encrypt a message, `this is a message`. First, convert `hello` in to the corresponding numbers of the letters that make up password: `h,e,l,l,o` is `8,5,12,12,15`. Then rotate the message by the corresponding numbers to the right
```
msg: t  h  i  s    i  s    a    m  e  s  s  a  g  e
ROT: 8  5 12 12   15  8    5   12 12 15  8  5 12 12
out: a  l  t  d    w  z    e    x  p  g  z  e  r  p
```
so `this is a message` encrpyted with the password `hello` is `altd wz e xpgzerp`. To decrypt, rotate each character in the encrypted message to the left by the corresponding number of the password.

Like skip ciphers, there are many variants, and some times brute force approaches are necessary.

#### Substitution: Atbash Cipher
Another common substitution method is to flip the order of the alphabet. `a` becomes `z`, `b` becomes `y`, etc. This is known as the **Atbash Cipher** [https://en.wikipedia.org/wiki/Atbash](https://en.wikipedia.org/wiki/Atbash)

### Common encoding techniques
Above we saw that **encryption** uses ciphers to change the order of characters or substitute one character for another. Below we'll show techniques where you can use different **encoding** methods to represent a message using different symbols or meanings behind the characters. You can therefore represent a message by changing the encoding of the message. Think of it as changing the character set from standard letters and numbers (a-z A-Z 0-9, or 62 different characters) to something else, or the same characters that mean something else (e.g., in hexadecimal, `A` means "ten"). There are many, many ways to do this, but here are some common ones:

#### Morse Code
Morse code is an extremely common way of representing letters and numbers as dots, dashes, and spaces [https://www.dcode.fr/morse-code](https://www.dcode.fr/morse-code)

#### ASCII Code
There is a standard way or representing letters in binary so computers can understand them called "ASCII". This represents every character as a number [https://en.wikipedia.org/wiki/ASCII](https://en.wikipedia.org/wiki/ASCII) [http://www.asciitable.com/](http://www.asciitable.com/). Once you have that number, you can represent that number many different ways: as a binary number, decimal number, octal number, or hexadecimal number. For example `a` is `91` in decimal, which is `61` in hexadecimal (hex), `141` in octal, and `01100001` in binary. There are plenty of online tools to encode and decode for you, for example: [https://multidec.web-lab.at/mc.php](https://multidec.web-lab.at/mc.php) [https://tools.decodeingress.me/#/basic](https://tools.decodeingress.me/#/basic).

How do you recognize an ASCII code in a particular base?
* Decimal: number values ranging from 32 to 126 are "printable" ASCII characters. `hello` is `104 101 108 108 111`
* Hex: Are two-character sequences consisting of a digit and a letter from A-F. Printable characters have the first digit in the range of 2-7. (i.e, `30` is corresponds to the number 0). `hello` is `68 65 6c 6c 6f`
* Octal: 3 digit numbers consisting of the digits 0-7. Printable characters start at 040 and end at 176. `hello` is `150 145 154 154 157`
* Binary: Groups of 7 digit or 8 digit sequence of 1s and 0s. If 8 digit sequence, the first digit is a 0. `hello` is `01101000 01100101 01101100 01101100 01101111`


#### A1Z26 Coding

You can represent every letter in the alphabet with the number of the order of the alphabet. For example, the first letter is `a` and the 26th is `z`, so the character `a` gets the number 1 and `z` gets the number 26. The word `hello` is therefore encoded as `8 5 12 12 15`.  [https://www.dcode.fr/letter-number-cipher](https://www.dcode.fr/letter-number-cipher)

#### Base64 (and other BaseN) coding
Any string of binary numbers can be represented as "printable" characters using base64 encoding. This is a great trick encoders use to convert almost anything with two characters in to readable text [https://en.wikipedia.org/wiki/Base64](https://en.wikipedia.org/wiki/Base64). A common use of base64 is to take an ASCII sequence of characters, encode it as a binary sequence of 1s and 0s, and convert that in to base64. All of this can easily be handled by many online tools, such as [https://tools.decodeingress.me/#/basic](https://tools.decodeingress.me/#/basic).

How to recognize base64?
* Consists of lower and uppercase letters a-z, A-Z, numbers 0-9, plus sign and slash + /, and equal sign =
* If the last characters are equal signs, it is almost always base64 (or base32, see below).
* Example: `hello!` is `aGVsbG8=`


There are many other variants of baseN that encodes 1s and 0s (or the ASCII binary 1s and 0s) in to other characters. It is good to research and get familiar with those on cyberchef, cryptii, and dcode.fr. What characters are used with which? For example, base32 uses only capital letters A-Z, numbers 2-7, and the equal sign =. [https://www.dcode.fr/base-32-encoding](https://www.dcode.fr/base-32-encoding)

## Steps to decode/decrypt a message
Now that we get the "building blocks" for encoding, we can approach decoding!
1. Do you have characters in the format you expect? For daily codes the game Ingress, your final code will be of the format: aaa##keyword###aa, that is 5 digits and the rest letters. So do you have 5 numbers and the rest letters? If so, use the **cipher** decryption methods above to translate and substitute until you have the solution. You may need a **password** to use some decryption methods (e.g., Vigenere), which may be hidden somewhere else.
1. If you don't have the right/expected characters, you can try decoding the message using the **coding** schemes listed above. Manipulating it should give you something which characters and numbers expected.
1. Go to step 1 until there is a solve.

### Example
Let's check out `IXRuZW1uZXRoZ2lsbkUgZWh0IG5pb0o=` from our intro paragraph.
1. It is unrecognizable text, but it consists only of a-z, A-Z, 0-9, and ends in an equal sign - so maybe it's base64 **coding**! Use dcode.fr's base64 decoder and see what happens.
1. Now I have something with punctuation, spaces, lower case letters, and one upper case letter - like a sentence! But the order seems wierd - the punctiation is at the front and the capital letter is in the back. This looks like the reverse **cipher**! Use dcode.fr or other tool to help you reverse it!

## Conculsion and Summary
Now you can see the building blocks of solving these puzzles: use combinations of **ciphers** and **coding schemes** to manipulate one message to get another. **Ciphers** change the order of characters or substitute one character for another, **coding schemes** change the representation of one set of characters or symbols in to another set of characters or symbols. There are many, many ways of doing it, this just presented a few common ones to get the reader started, so now it's good to explore and learn as many as you can - both what they do and how they work!
