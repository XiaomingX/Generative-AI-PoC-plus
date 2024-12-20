#### **公司使用LLM（大型语言模型）回答关于数据的问题**
以 **辉瑞公司** 为例：
医生想了解一种新药的信息，传统方法需要阅读100页的文件。而使用LLM，可以直接通过提问得到答案，大幅提高效率。

---

#### **如何将公司的数据加入LLM**
1. **重新训练LLM**  
   - 重新训练模型以包含新的数据，但成本高昂，耗时长。如果数据变化频繁，不推荐。
   
2. **直接将数据加入问题的上下文**  
   - 把需要问的问题和相关数据打包一起输入，但LLM的上下文长度有限（例如GPT-3是5k词，GPT-2是1k词），即便更大的模型也不是广泛可用。

3. **RAG（检索增强生成）**  
   - 这是第2种方法的改进版，通过数学方法更高效地从数据中找到相关信息。

---

#### **什么是向量？**
向量是NLP（自然语言处理）中的一种数学表示，用于将文本转换成数值。我们可以通过向量计算找到与问题相关的段落，而不仅仅是关键词匹配，比如一个更智能的“Ctrl+F”工具。

---

#### **数据处理流程（Ingestion）**
1. **将文档转换为纯文本**  
   - 按章节、段落或句子分块（例如用Azure Form Recognizer）。
   
2. **生成向量**  
   - 用特定的LLM将文本块转化为向量。

3. **存储向量**  
   - 将这些向量存入数据库，以便后续查询。

---

#### **如何回答问题**
1. **匹配相关段落**  
   - 将问题也转化为向量，利用数学方法找到上下文最相关的内容，就像一个智能搜索工具。

2. **优化提问（Prompt Engineering）**  
   - 构建提问的格式，让LLM专注于人类对话和问题回答。
   - 例如：
     ```text
     你是医生专家。你的任务是帮助其他医生查询医疗指南。以下是医疗指南的片段：[1]  
     请仅根据这些片段回答问题，答案需清晰、有逻辑。如果不知道答案，请直接说“不知道”。
     ```

---

#### **云端实现**
虽然具体方法尚未明确，但可以尝试基于Azure等云服务构建系统（展示Azure架构图）。

---

#### **总结**
- 提供代码仓库和Slack频道链接。
- 代码主要是Python，虽然可以用C#实现，但不够完善。
- **注意隐私**：答案可能并不总是准确的。
