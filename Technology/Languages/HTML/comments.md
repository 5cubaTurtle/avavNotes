[doc](https://www.htmlhelp.com/reference/wilbur/misc/comment.html)
A _comment declaration_ starts with `<!`, followed by zero or more comments, followed by `>`. A _comment_ starts and ends with "`--`", and does not contain any occurrence of "`--`".
This means that the following are all legal SGML comments:
1. `<!-- Hello -->`
2. `<!-- Hello -- -- Hello-->`
3. `<!---->`
4. `<!------ Hello -->`
5. `<!>`
