#### 1.使用最新版模型

为获得最佳效果，建议使用最新、功能最强大的型号。 截至2022年11月，最佳选择是用于文本生成的"text-davinci-003"模型和用于代码生成的"code-davinci-002"模型。

#### 2.将指令放在提示符的开头，用###或"""分隔指令和上下文(背景)

错误示例

```
Summarize the text below as a bullet point list of the most important points.

{text input here}

```

正确示例

```
Summarize the text below as a bullet point list of the most important points.

Text: """  
{text input here}  
"""

```

### 3\. 对期望的背景、结果、长度、格式、风格等尽可能具体、描述和详细

错误示例

```
Write a poem about OpenAI. 

```

正确示例

```
Write a short inspiring poem about OpenAI, focusing on the recent DALL-E product launch (DALL-E is a text to image ML model) in the style of a {famous poet}

```

#### 4、通过示例（示例 1、示例 2）阐明所需的输出格式

错误示例

```
Extract the entities mentioned in the text below. Extract the following 4 entity types: company names, people names, specific topics and themes.

Text: {text}

```

正确示例

```
Extract the important entities mentioned in the text below. First extract all company names, then extract all people names, then extract specific topics which fit the content and finally extract general overarching themes

Desired format:  
Company names: <comma\_separated\_list\_of\_company_names>  
People names: -||-  
Specific topics: -||-  
General themes: -||-

Text: {text}

```

#### 5、从 zero-shot 开始，然后是 few-shot（示例），两者都不起作用，然后进行微调

```
Extract keywords from the corresponding texts below.

```

```
Text 1: Stripe provides APIs that web developers can use to integrate payment processing into their websites and mobile applications.  
Keywords 1: Stripe, payment processing, APIs, web developers, websites, mobile applications  
##  
Text 2: OpenAI has trained cutting-edge language models that are very good at understanding and generating text. Our API provides access to these models and can be used to solve virtually any task that involves processing language.  
Keywords 2: OpenAI, language models, text processing, API.  
##  
Text 3: {text}  
Keywords 3:

```

#### 6、减少“废话”和不精确的描述

错误示例

```
The description for this product should be fairly short, a few sentences only, and not too much more.

```

正确示例

```
Use a 3 to 5 sentence paragraph to describe this product.

```

#### 7、与其说不该做什么，不如说该做什么

错误示例

```
The following is a conversation between an Agent and a Customer. DO NOT ASK USERNAME OR PASSWORD. DO NOT REPEAT.

Customer: I can’t log in to my account.  
Agent:

```

正确示例

```
The following is a conversation between an Agent and a Customer. The agent will attempt to diagnose the problem and suggest a solution, whilst refraining from asking any questions related to PII. Instead of asking for PII, such as username or password, refer the user to the help article www.samplewebsite.com/help/faq

Customer: I can’t log in to my account.  
Agent:

```

#### 8、特定于代码生成 - 使用“引导词”将模型推向特定模式

错误示例

```
# Write a simple python function that  
# 1. Ask me for a number in mile  
# 2. It converts miles to kilometers

```

正确示例

```
# Write a simple python function that  
# 1. Ask me for a number in mile  
# 2. It converts miles to kilometers  
import

```

#### 模型参数设置

通常，我们发现模型和温度是改变模型输出的最常用参数。

1、model - 更高性能的模型更昂贵并且具有更高的延迟。  
2、temperat对于大多数事实用例，例如数据提取和如实问答，温度为ure - 衡量模型输出不太可能的标记的频率。 温度越高，输出越随机（并且通常具有创造性）。 然而，这与“真实”不同。  0 是最佳的。  
3、max_tokens（最大长度）- 不控制输出的长度，而是令牌生成的硬截止限制。 理想情况下，您不会经常达到此限制，因为您的模型会在它认为完成时或达到您定义的停止序列时停止。  
4、stop（停止序列）- 一组字符（标记），在生成时将导致文本生成停止。

#### 原文
https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api
