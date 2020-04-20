# So you want to decode...

This is an intro on how one can start getting in to decoding games. While there are plenty of helpful tools and walkthroughs on the internet, many new decoders can easily become overwhelmed figuring out which tools to use or where to even start when presented with something like `IXRuZW1uZXRoZ2lsbkUgZWh0IG5pb0o=`. This primer will walk through "how to strategize" when presented with a decoding problem with examples. In the end, you'll have the basic understanding of what's happening that you can then use to try out and learn their vast number of decoding tools available on the internet. How we'll do it:

1. Learn the two ways encrypted/encoded messages are created.
   1. "Encrypting"
   1. "Encoding"
1. Recognize/guess starting points when you find an encrypted/encoded message
1. Give starting points for what to do when it is not clear

## How to encrypt/encode a message

To figure out how to decode, you first have to know how a messages are encoded in the first place. To make things easier, you can think of encoding as some combination of the following 2 processes:

* **Encrypting** is taking the message and rearranging or substituting the characters to hide a message. In other words, encrypting keeps the same _character set_ (e.g., ASCII characters a-z A-Z and arabic numerals 0-9) but changes their meaning or order. For example, reversing the order of characters would encrypt `hello` as `olleh`. These methods are called **ciphers**
*  **Encoding** is kind of the converse of encrypting in that it keeps the message the same, just represents it in a different way. For example, Morse code would encode `hello` as `.... . .-.. .-.. ---`. These methods are called **codings**

That's basically it! To create an encoded/encrypted message, you do some combination of one or more of the above. To decrypt, you just do the opposite. The game then becomes, "how do I recoginize if I need to decrypt or decode, and which do I use?" To do that, we first can learn about common encryption and encoding techniques

### Common encryption techniques

The following is a quick summary of a few of the basic techniques. Encryption can generally be thought of as one of two techniques: (a) some sort of rearranging of the order and (b) substituting letters for others. Given a message, you can hide its meaning by doing things like:

#### Rearranging: Reversing the order of characters
`hello` as `olleh`

#### Rearranging: Skip Characters
In a **skip cipher** you write the message every _n_ characters. So id _n_=4: `abcdefgh` becomes `aebfcgdh` How to easily encrypt: write you message on mulitiple lines, each with _n_ characters. So, with _n_=4:
```
abcd
efgh
```
Then read the columns, from left to right: `ae` `bf` `cg` `dh`. To decode, write your message in rows and read down the columns. Here you may have to try different combinations to get it to work, or use something like https://multidec.web-lab.at/skip.php to do it for you for many combinations at once. For example: `aebfcgdh` is written as:
```
ae
bf
cg
dh
```
Then reading the columns: `abcdefgh`

#### Rearranging: Variants of Skip
There are plenty of variants to skip that play games with how many to skip at a time, which is why you'll see many online. For example, you can use a passcode to change _n_ after each character, you have a **transposition cipher** https://www.dcode.fr/transposition-cipher. You also can change _n_ in a clever way using a  **rail fence cipher** https://en.wikipedia.org/wiki/Rail_fence_cipher. Also, you don't always have to go from left to right, top to bottom, but the direction can change as well as in a **route/path cipher** https://www.dcode.fr/route-cipher. And there are many, many, more. The point here is that you may need to brute force trying different techniques until one "clicks." Luckily, there are many online tools to try out.

#### Substitution: Rotating number of characters
You can encrypt a message by "rotating" a certain number of characters. Here, "rotating" means exchange every letter for one _n_ letters away on the alphabet. For example, recalling Arthur C. Clarke & Stanley Kubric, the letters `HAL` can be rotated 1 letter to give us `IBM`. The letter after `h` is `i`, and so one. The letter after `z` is `a`. This is called a **ROT cipher** https://www.dcode.fr/rot-cipher, the most common being **ROT13** or **Ceasar cipher**. Decrypting and encrypting  are the same, it's just that the decrypting and encrypting rotations have to equal 26. So **ROT1** encoding can be docded with **ROT25**. That's why **ROT13** is popular - it is encorypted and decrypted in the same way. Alternatively, you can encrypt a message by rotating _n_ to the left then decode by rotating _n_ to the right.

#### Substitution: Variants on ROT ciphers
You can change the _n_ of the substitution with every character. For example, if you have a password, you can use that to 
encrypt and decrypt a message. This is called **viginere cipher** https://www.dcode.fr/vigenere-cipher. I can use the password `hello` to encrypt a message, `this is a message`. First, convert `hello` in to the corresponding numbers of the letters that make up password: `h,e,l,l,o` is `8,5,12,12,15`. Then rotate the message by the corresponding numbers to the right
```
msg: t  h  i  s    i  s    a    m  e  s  s  a  g  e
ROT: 8  5 12 12   15  8    5   12 12 15  8  5 12 12
out: a  l  t  d    w  z    e    x  p  g  z  e  r  p
```
so `this is a message` encrpyted with the password `hello` is `altd wz e xpgzerp`. To decrypt, rotate each character in the encrypted message to the left by the corresponding number of the password.

Like skip ciphers, there are many variants, and some times brute force approaches are necessary.


### Common encoding techniques
You can represent a message by changing the encoding of the message. Think of it as changing the character set from standard letters and numbers (a-z A-Z 0-9, or 62 different characters) to something else. There are many, many ways, but here are some common ones:

#### Morse Code
Famous way of representing letters and numbers as dots, dashes, and spaces. https://www.dcode.fr/morse-code

#### ASCII Code
There is a standard way or representing letters in binary so computers can understand them called "ASCII". This represents every character as a number https://en.wikipedia.org/wiki/ASCII http://www.asciitable.com/. Once you have that number, you can represent that number many different ways: as a binary number, decimal number, octal number, or hexadecimal number. For example `a` is `91` in decimal, which is `61` in hexadecimal (hex), `141` in octal, and `01100001` in binary. There are plenty of online tools to encode and decode for you, for example: https://multidec.web-lab.at/mc.php.

How do you recognize an ASCII code in a particular base?

* Decimal: number values ranging from 32 to 126 are "printable" ASCII characters.
* Hex: Are two-character sequences consisting of a digit and a letter from A-F. Printable characters have the first digit in the range of 2-7. (i.e, `30` is corresponds to the number 0.
* Octal: 3 digit numbers consisting of the digits 0-7. Printable characters start at 040 and end at 176.
* Binary: 7 digit or 8 digit sequence of 1s and 0s. If 8 digit sequence, the first digit is a 0.


#### A1Z26

#### Base64 (and other BaseN) coding


## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/maqifrnswa/DecodingPrimer/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/maqifrnswa/DecodingPrimer/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
