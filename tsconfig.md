---
title: ts config
---  
```json
{
  "extends": "./node_modules/gts/tsconfig-google.json",
  "compileOnSave": false,
  "compilerOptions": {
    "baseUrl": "./",
    "outDir": "./dist/out-tsc",
    "strict": true,
    "module": "es6",
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": false,
    "experimentalDecorators": true,
    "noUnusedParameters": true,
    "noUnusedLocals": true,
    "noPropertyAccessFromIndexSignature": true,
    "noImplicitOverride": true,
	"noUncheckedIndexedAccess": true,
    "importHelpers": true,
    "target": "es2022",
    "lib": ["es2020", "dom"],
    "useDefineForClassFields": false
  },
  "angularCompilerOptions": {
    "strictTemplates": true
  },
  "exclude": ["node_modules"]
}
```
