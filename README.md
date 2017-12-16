#this markdown file is a literate program, run it like this: `sh README.md`. <!--
sed -n 's/^    //p' $0 | /usr/bin/env python; exit # -->

# Self-contained literate programs in Markdown

This file is an example of a [literate program](https://en.wikipedia.org/wiki/Literate_programming).

What's special about it is that it needs no special program to run it. Just pass it to a shell command like `sh` or `bash` like so:

```
sh README.md
```

Any line beginning with four spaces will be interpreted as Python code.

    print('Hi from my literate program!')

We can switch back between prose and code just as in a normal Markdown document.

    def is_prime(k):
        for i in range(2, k):
            if k % i == 0:
                return False
        return True

    for i in range(1, 20):
        if is_prime(i):
            print('{} is prime'.format(i))

The non-code blocks are simply discarded. This example uses Python, but any scripting language (i.e. any interpreter that can be used in a [shebang line](https://en.wikipedia.org/wiki/Shebang_(Unix)) should work.

## How it works

At the beginning of the document there is a markdown comment. It contains a shell script that uses `sed` to extract the lines that begin with four spaces, and pipe them to a Python process.
