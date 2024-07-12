---
title: "CSS in JSを理解する"
emoji: "👩‍🎤"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ['react', 'css', 'emotion']
published: false
---

## 背景

## コード
lint-stagedとhuskyを利用して、ファイル名の命名規則を強制する方法を紹介します。

1. ファイル名を確認するJSコードを書く

requireが必要なので、Node.jsで動作するコードを書きます。

```javascript
const fs = require('fs')
const path = require('path')

function getFileList(dir) {
  let files = []

  const dirContents = fs.readdirSync(dir)

  const ignoredFiles = ['.DS_Store']

  dirContents.forEach((item) => {
    const itemPath = path.join(dir, item)

    if (ignoredFiles.includes(item)) {
      return
    }

    if (fs.statSync(itemPath).isDirectory()) {
      files = files.concat(getFileList(itemPath))
    } else {
      files.push(itemPath)
    }
  })

  return files
}

const imageFiles = getFileList('./src')

const filesWithInvalidNames = imageFiles.filter((imageFile) =>
  /[^a-z0-9\-_.\/]/.test(imageFile)
)

if (invalidImageFiles.length > 0) {
  console.error(
    'Error: The following image files contain invalid characters:',
    filesWithInvalidNames
  )
  process.exit(1)
}

```

1. lint-stagged.config.jsに追加

```bash
