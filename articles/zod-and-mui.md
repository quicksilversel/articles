---
title: "CSS in JSを理解する"
emoji: "👩‍🎤"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ['react', 'css', 'emotion']
published: false
---

# ZodとMUIのTextFieldを利用して入力フォーム

## 初めに

[Zod](https://zod.dev/)とは、TypeScript向けのスキーマ宣言とデータ検証のためのライブラリです


## 準備

Nextを使って進めていきます

```bash
npx create-next-app@latest
```

```jsx
// inputのコンテキスト
const { inputValue, setInputValue } = useContext(context)

const [hasError, setHasError] = useState(false)
```

```jsx
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
  const input = parseInt(e.target.value)

  if(isNaN(input)) return

  const result = priceSchema.safeParse({
    priceFrom: input,
    priceTo: context.priceTo,
  })

  if (!result.success) setHasError(true)
  else {
    setHasError(false)
    setInputValue({ priceFrom: input, ...rest })
  }
}
```

MUI

```jsx
import { TextField } from '@mui/material'

<TextField
  label={
    hasError
      ? `入力内容が間違っています`
      : '価格（から）'
  }
  type="number"
  onChange={handleChange}
  error={hasError}
/>
```
