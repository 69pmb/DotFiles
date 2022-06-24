## NPM

- Find new package versions (all or by level):

```
npx --yes npm-check-updates -i
npx --yes npm-check-updates -i -t <latest, newest, greatest, minor, patch>
```

- Clean cache:  
  `npm cache clean --force`
- Use cache:  
  `npm ci --cache .npm --prefer-offline`
- Install in another directory:  
`npm i --prefix projects/my-lib`
- Update _projects_ library's folder:  
`pwd | grep -o "[^/]*$" |  xargs -I % npm update --prefix projects/%`
- Save peer dependency:  
`npm i pck@version --save-peer`
- Save exact version:  
`npm i pck@version -E`
