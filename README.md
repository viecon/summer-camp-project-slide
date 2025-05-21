# 環境設定

* NodeJS
* npm

```
npm install
```

渲染:

```
npm run dev
```

# 官方文件

* https://sli.dev/

# 說明

## pages

編輯在 `pages` 裡面的 markdown 們

`slides.md` 彙整所有文件

## public

圖片放裡面

在 markdown 中插入圖片：

```md
![專案整體架構圖](/pics/whole_structure.png)

<img src="/pics/gemini_API_rate.png" />
```

## Components

### CodeBlockResizer.vue

調整 Code block 的大小

```md
 <CodeBlockResizer font-size="1em">

‵‵‵py
from google import genai
client = genai.Client(api_key="YOUR_API_KEY")

response = client.models.generate_content(
    model='gemini-2.0-flash',
    contents='講個冷笑話'
)
print(response.text)
‵‵‵

</CodeBlockResizer>
```

### InvertDark.vue

讓裡面的東西在暗色模式的顏色反轉

```md
<InvertDark>
  <img src="/pics/gemini_API_rate.png" />
</InvertDark>
```

### QRCode.vue

QRCode

```md
<QRCode
      value="https://youtu.be/4W5r_nTYQO0"
      :width="300"
      :height="300"
      color="aa55ff"
      darkColor="aa55ff"
      dot-type="rounded"
/>
```

### QuoteBlock.vue

忘記為什麼要寫它了

```md
<QuoteBlock>
it’s a prediction engine. The model takes sequential text as an input and then predicts what the following token should be, based on the data it was trained on. The LLM is operationalized to do this over and over again, adding the previously predicted token to the end of the sequential text for predicting the following token. The next token prediction is based on the relationship between what’s in the previous tokens and what the LLM has seen during its training.
</QuoteBlock>
```

### VertCenter.vue

讓裡面的東西垂直置中

不知道為什麼要調一下趴數

```md
<VertCenter height="70%">
  <CodeBlockResizer font-size="1.5em">

  ‵‵‵text
  請將以下句子翻譯成法語：
  "The book is on the table."
  ‵‵‵
  </CodeBlockResizer>
</VertCenter>
```


### 其他

要加自己加，記得在這裡更新

## styles

CSS

# 大家加油