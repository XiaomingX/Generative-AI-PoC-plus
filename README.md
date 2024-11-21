### 打开容器开发环境

[![远程容器中打开](https://img.shields.io/static/v1?label=远程容器&message=打开&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/XpiritBV/Generative-AI-PoC)

---

### 术语定义

- **聪明 (Smart)**  
  指对某个主题了解很多，但缺乏实际操作经验的人。

- **智慧 (Wise)**  
  指不仅对某个主题了解很多，还具备将知识应用到实际生活中的经验的人。

- **Ctrl + F 模型**  
  类似“Ctrl + F”的模型只具备“聪明”的特点，但不够“智慧”。它像一本书中的关键词检索，没有实际的上下文。

---

### PoC v1 范围

- **目标**  
  我们的第一个目标是创建一个类似“Ctrl + F”的原型（PoC），通过检索实现简单的知识应用。数据集将选用一本PDF格式的书。

- **不包括的内容**  
  - 我们不会花太多时间在数据预处理上。

---

### 技术细节

![嵌入式数据库示意图](https://user-images.githubusercontent.com/7449547/235882195-766d157f-90e7-4f1f-abaa-08131b36cef4.jpg)  
[图片来源](https://bdtechtalks.com/2023/05/01/customize-chatgpt-llm-embeddings/)  

- **技术方向**  
  我们将使用 Azure 提供的服务来实现这个原型。

---

### 应用场景

PoC v1 可以为用户提供哪些实用价值？  
探索这一模型如何简化大数据集的检索。

---

### 注意事项

1. Azure OpenAI 服务目前只支持英文内容处理。
2. OpenAI 嵌入式 API 的单次调用限制为 2048 个 token（约2-3页文本）。

---

### 调查方向

为了让大数据集可以被大语言模型（LLM）高效处理，同时不超过 token 限制，我们有以下假设：

- **操作流程**  
  以一本书为例：
  1. 为书中的内容生成嵌入向量（使用模型 `text-embedding-ada-002`）。
  2. 确保文本分块不超过2048个 token（2-3页文本）。
  3. 将段落中的换行替换为空格，生成的嵌入向量存储在一个向量数据库中（数据库选择尚未确定）。

- **问答机制**  
  当用户提出问题时，模型可以根据问题生成向量，从数据库中找到匹配的部分，并将这些相关内容作为上下文添加给 LLM，以提供准确回答。

--- 

### 总结  
我们通过这种方式，实现了在 token 限制内，利用嵌入向量高效检索大型数据集的能力，从而为用户问题提供更精准的答案。