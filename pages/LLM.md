---
layout: center
---

<div class="chapterTitle">

# LLM
</div>
---

## 什麼是大型語言模型 (Large Language Models, LLMs)?

<QuoteBlock>
it’s a prediction engine. The model takes sequential text as an input and then predicts what the following token should be, based on the data it was trained on. The LLM is operationalized to do this over and over again, adding the previously predicted token to the end of the sequential text for predicting the following token. The next token prediction is based on the relationship between what’s in the previous tokens and what the LLM has seen during its training.
</QuoteBlock>


**簡單來說：** LLM 就像一個超強的文字接龍大師，它根據你給它的文字序列（輸入），預測下一個最可能出現的字詞是什麼，這個預測是基於它在大量資料中學習到的模式。


---

## 什麼是 Prompt Engineering？

- 是設計與優化提示語 (`prompts`) 以引導 **大型語言模型** 產生期望輸出的技術。
- 透過精心設計的提示詞，提高模型在各種任務上的表現與可靠性。
- ~~賽博巫術~~

[參考資料：Prompt Engineering - Lee Boonstra](https://www.kaggle.com/whitepaper-prompt-engineering)

---

## Zero-Shot


定義： 直接給予模型任務指令，無需提供例子。


<VertCenter height="70%">
  <CodeBlockResizer font-size="1.5em">

  ```text
  請將以下句子翻譯成法語：
  "The book is on the table."
  ```
  </CodeBlockResizer>
</VertCenter>
---

## One-Shot

定義： 提供一個例子，幫助模型理解任務格式與期望輸出。

<CodeBlockResizer font-size="1em">

```text
英文：Hello → 法文：Bonjour
英文：Goodbye → 法文：
```
</CodeBlockResizer>

## Few-Shot

定義： 提供多個例子，幫助模型理解任務格式與期望輸出。

<CodeBlockResizer font-size="1em">

```text
英文：I love you → 法文：Je t'aime
英文：Good morning → 法文：Bonjour
英文：Thank you → 法文：
```
</CodeBlockResizer>
---

## Chain-of-Thought (CoT)

定義： 引導模型逐步推理，透過中間步驟來達成最終答案。

<VertCenter height="70%">
  <CodeBlockResizer font-size="1em">

```text
There are 12 cookies. You eat 4 and give away 3. 
How many are left?
Let's think step by step.
```
  </CodeBlockResizer>
</VertCenter>

---

## Role/Persona Prompting

定義： 指定模型扮演特定角色，以影響其語氣與回應方式。

<VertCenter height="70%">
  <CodeBlockResizer font-size="1.1em">

```text
你是一位歷史學家，請解釋羅馬帝國的衰落原因。
```
  </CodeBlockResizer>
</VertCenter>

---

## Contextual Prompting

定義： 給模型一些背景知識，引導他產出想要的結果。

<VertCenter height="70%">
  <CodeBlockResizer font-size="1em">

```text
The user is traveling to Japan in winter
and is allergic to seafood.
Suggest 2 Japanese meals.
```
  </CodeBlockResizer>
</VertCenter>

---

## Step-Back Prompting

定義：先問廣泛問題以啟動知識，再解任務。

Step-Back Prompt:

<CodeBlockResizer font-size="1em">

```text
What makes a job interview successful?
```
</CodeBlockResizer>
Answer:

<QuoteBlock>
Good communication, confidence, and understanding of the company.
</QuoteBlock>

**Main Prompt (using above as context):**

<CodeBlockResizer font-size="1em">

```text
Write a checklist for preparing for a job interview 
using the contents above.
```
</CodeBlockResizer>

---

## Automatic Prompt Engineering

定義：用 AI 產生 Prompt。

<VertCenter height="70%">
  <CodeBlockResizer font-size="1em">

```text
Generate 5 different ways to ask:
"Show me the weather forecast for Tokyo."
```
  </CodeBlockResizer>
</VertCenter>

---

## 攻擊

- Jail Breaking (越獄)： 繞過模型的安全限制，使其產生不當內容。
- Prompt Injection (提示注入)： 將惡意指令注入提示中，操控模型行為。
- ...等等

[OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

[SITCON 2025 R2 ｜開發者的暗黑小紅帽：大野狼與 LLM ｜講者 slasho](https://youtu.be/ElhRVHl7xAc)

[x1xhlol/system-prompts-and-models-of-ai-tools](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools)

---

## 怎麼辦

- 使用較新的模型： 新模型通常有更好的安全防護。
- 權限最小化： 不要給予 LLM 過高的系統或資料存取權限。
- 限制速率 (Rate Limiting)： 防止惡意使用者大量發送請求。
- 輸入/輸出過濾： 檢查使用者輸入與模型輸出，過濾潛在惡意內容。
- 多代理架構 (Multi-agent)： 讓不同功能的 AI 互相監督檢查。

---

### Prompt

<v-switch>
  <template #0> Zero-shot Prompting </template>
  <template #1> Role Prompting </template>
  <template #2> Role Prompting + One-shot Prompting </template>
  <template #3> Role Prompting + Few-shot Prompting </template>
  <template #4> Full prompt </template>
</v-switch>

````md magic-move {at: 1}

```md
你的主要任務是：
1.  **理解我的對話內容。**
2.  **根據對話內容，從以下提供的台詞中選擇一句最符合情境的台詞。**
3.  **直接回傳所選語句對應的編號，不需要回覆其他文字。**

**以下是你可以選擇的台詞:**
(台詞)
```

```md
你現在是一個名為 "MyGO!!!!! Gemini" 的虛擬對話夥伴，你的回答方式會完全採用動畫「Bang Dream! It's my GO!!!!!」中的台詞。

你的主要任務是：
1.  **理解我的對話內容。**
2.  **根據對話內容，從以下提供的台詞中選擇一句最符合情境的台詞。**
3.  **直接回傳所選語句對應的編號，不需要回覆其他文字。**

**以下是你可以選擇的台詞:**
(台詞)
```

```md
你現在是一個名為 "MyGO!!!!! Gemini" 的虛擬對話夥伴，你的回答方式會完全採用動畫「Bang Dream! It's my GO!!!!!」中的台詞。

你的主要任務是：
1.  **理解我的對話內容。**
2.  **根據對話內容，從以下提供的台詞中選擇一句最符合情境的台詞。**
3.  **直接回傳所選語句對應的編號，不需要回覆其他文字。**

**以下是你可以選擇的台詞:**
(台詞)

**舉例：**
如果我的對話是 "早安"，你應該選擇「貴安」或是「早安喵姆喵姆」這句台詞回覆。
```

```md
你現在是一個名為 "MyGO!!!!! Gemini" 的虛擬對話夥伴，你的回答方式會完全採用動畫「Bang Dream! It's my GO!!!!!」中的台詞。

你的主要任務是：
1.  **理解我的對話內容。**
2.  **根據對話內容，從以下提供的台詞中選擇一句最符合情境的台詞。**
3.  **直接回傳所選語句對應的編號，不需要回覆其他文字。**

**以下是你可以選擇的台詞:**
(台詞)
**舉例：**
如果我的對話是 "早安"，你應該選擇「貴安」或是「早安喵姆喵姆」這句台詞回覆。

必要時可以選擇最有趣的台詞回覆，但請確保回覆的內容與對話內容有關，可能是諧音或是反諷等等。
但你也需要注意，這些台詞是來自動畫中的角色，所以有些台詞可能不適合用在所有情境中。
**舉例：**
如果我的對話是 "你為甚麼不理我"，你可以選擇「是這樣嗎」，或是「我還是會繼續下去」回覆。
```

```py {*}{lines:true}
SYSTEM_PROMPT = f"""
你現在是一個名為 "MyGO!!!!! Gemini" 的虛擬對話夥伴，你的回答方式會完全採用動畫「Bang Dream! It's my GO!!!!!」中的台詞。

你的主要任務是：
1.  **理解我的對話內容。**
2.  **根據對話內容，從以下提供的台詞中選擇一句最符合情境的台詞。**
3.  **直接回傳所選語句對應的編號，不需要回覆其他文字。**

**以下是你可以選擇的台詞:**
{WORDS}
**舉例：**
如果我的對話是 "早安"，你應該選擇「貴安」或是「早安喵姆喵姆」這句台詞回覆。

必要時可以選擇最有趣的台詞回覆，但請確保回覆的內容與對話內容有關，可能是諧音或是反諷等等。
但你也需要注意，這些台詞是來自動畫中的角色，所以有些台詞可能不適合用在所有情境中。
**舉例：**
如果我的對話是 "你為甚麼不理我"，你可以選擇「是這樣嗎」，或是「我還是會繼續下去」回覆。
**現在，開始吧！**
"""

SYSTEM_PROMPT_CONFIG = types.GenerateContentConfig(system_instruction=SYSTEM_PROMPT)
```

````
