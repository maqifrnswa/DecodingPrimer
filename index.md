# So you want to decode...

This is an intro on how one can start getting in to decoding games. While there are plenty of helpful tools and walkthroughs on the internet, many new decoders can easily become overwhelmed figuring out which tools to use or where to even start when presented with something like `IXRuZW1uZXRoZ2lsbkUgZWh0IG5pb0o=`. This primer will walk through "how to strategize" when presented with a decoding problem with examples. In the end, you'll have the basic understanding of what's happening that you can then use to try out and learn their vast number of decoding tools available on the internet. How we'll do it:

1. Learn the two ways encrypted/encoded messages are created.
   1. "Encrypting"
   1. "Encoding"
1. Recognize/guess starting points when you find an encrypted/encoded message
1. Give starting points for what to do when it is not clear

## How to encrypt/encode a message

To figure out how to decode, you first have to know how a messages are encoded in the first place. To make things easier, you can think of encoding as some combination of the following 2 processes:

* **Encrypting** is taking the message and rearranging or substituting the characters to hide a message. In other words, encrypting keeps the same _character set_ (e.g., ASCII characters a-z A-Z and arabic numerals 0-9) but changes their meaning or order. For example, reversing the order of characters would encrypt `hello` as `olleh` 
*  **Encoding** is kind of the converse of encrypting in that it keeps the message the same, just represents it in a different way. For example, Morse code would encode `hello` as `.... . .-.. .-.. ---`

That's basically it! To create an encoded/encrypted message, you do some combination of one or more of the above. To decrypt, you just do the opposite. The game then becomes, "how do I recoginize if I need to decrypt or decode, and which do I use?" To do that, we first can learn about common encryption and encoding techniques

### Common encryption techniques

### Common

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
