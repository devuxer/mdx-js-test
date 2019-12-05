Attempting to get mdx-js to work with Create React App and craco.

Unfortunately, doesn't work (yet).

If I `npm start`, I get:

---

> Failed to compile
>
> ```
> ./src/hello.mdx
> SyntaxError: C:\Users\Dan\Documents\Temporary\Working\CRA > EJECT\mdx-js-test\src\hello.mdx: Unexpected token (10:9)
>
>    8 | const makeShortcode = name => function MDXDefaultShortcode(props) {
>    9 |   console.warn("Component " + name + " was not imported, exported, or provided by > MDXProvider as global scope")
> > 10 |   return <div {...props}/>
>      |          ^
>   11 | };
>   12 |
>   13 | const layoutProps = {
> ```

---

Note, all my testing has been on a Windows 10 machine.

I've also tried overriding the default babel settings, but I continued to get the same error.

Suggestions/hunches/pull requests from the community welcome 🙏
