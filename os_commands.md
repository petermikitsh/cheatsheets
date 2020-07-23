# Commands

## Delete directories by glob pattern

Useful for clearing unused folders on `gh-pages` branches.

```
find . -type d -name "*-canary-*" -exec rm -rf {} \;
```
