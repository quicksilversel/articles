## QuickType

## json-schema-to-typescript

```js
import { compile, compileFromFile } from 'json-schema-to-typescript'

if (!fs.existsSync('./src/libs/aem/types/zozoLpArchive.d.ts')) {
  compile(data, 'Schema').then((ts) => {
    fs.writeFileSync('./src/type.d.ts', ts)
  })
}

```

## GraphQL-CodeGen