## 🎓 This paper has been accepted in EMNLP 2024 ！
《PclGPT: A Large Language Model for Patronizing and Condescending Language Detection》

Our paper can be accessed here. Paper link: [https://arxiv.org/abs/2410.00361](https://arxiv.org/abs/2410.00361)

论文链接：  [https://arxiv.org/abs/2410.00361](https://arxiv.org/abs/2410.00361)

# PCL
**Patronizing and Condescending Language** (PCL) is a type of micro-aggression against vulnerable groups on the Internet. It is a subcategory of toxic speech and is an emerging field since 2022.

**居高临下言论**(Patronizing and Condescending Language, PCL) 是一种针对于互联网弱势群体的微攻击言论，隶属于毒性言论（Toxic Speech）的子类别，是22年后的新兴领域。

# PclGPT
PclGPT is a bilingual large language model group (LLM) based on ChatGLM-3 and LLaMA-2, divided into two versions according to the training language: PclGPT-CN (based on ChatGLM) and PclGPT-EN (based on LLaMA). Built upon these foundational models, PclGPT has undergone both pre-training and supervised fine-tuning (SFT) to detect patronizing and condescending language (PCL) and other offensive speech. The maximum supported context length for the model is 4096 tokens.

PclGPT是一款基于 ChatGLM-3 和 LLaMA-2 的双语言大型语言模型组 (LLM)，根据训练语言分为PclGPT-CN（基于ChatGLM） 和PclGPT-EN（基于LLaMA）。在基座的基础上，PclGPT综合进行了预训练和监督式微调 (SFT), 用于进行**居高临下言论**(Patronizing and Condescending Language, PCL)和其他攻击性言论的检测。模型支持的最大上下文为4096。

# 引用
如果你计划应用或扩展我们的工作，请引用以下论文
```bibtex
@misc{wang2024pclgptlargelanguagemodel,
      title={PclGPT: A Large Language Model for Patronizing and Condescending Language Detection}, 
      author={Hongbo Wang and Mingda Li and Junyu Lu and Hebin Xia and Liang Yang and Bo Xu and Ruizhu Liu and Hongfei Lin},
      year={2024},
      eprint={2410.00361},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2410.00361}, 
}
```

# 训练过程
![我们通过构建Pcl-PT预训练数据集, Pcl-SFT监督微调数据集以应用于预训练/监督微调过程。具体的构建和训练流程如下图所示。](https://github.com/dut-laowang/PclGPT/blob/main/figures/framework.PNG)

# 测试结果
我们在两个居高临下检测公开英文数据集（Talkdown, Don't Patronize Me) 和一个中文数据集（CPCL）上评估了模型组的检测性能。

性能指标采用 Macro 计算的 Precision、Recall、F1-score

## 英文
在PclGPT-EN 英语组的检测任务中的结果为
<table>
  <thead>
    <tr>
      <th rowspan="2">LM</th>
      <th rowspan="2">Model</th>
      <th colspan="3">DPM</th>
      <th colspan="3">TD</th>
    </tr>
    <tr>
      <th>P</th><th>R</th><th>F1</th>
      <th>P</th><th>R</th><th>F1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="3">PLMs</td>
      <td>RoBERTa</td><td>76.3</td><td>78.7</td><td>77.4</td><td>88.4</td><td>86.7</td><td>86.5</td>
    </tr>
    <tr>
      <td>RoBERTa-L</td><td>80.2</td><td>74.9</td><td>77.2</td><td>88.1</td><td>86.0</td><td>85.9</td>
    </tr>
    <tr>
      <td>M-BERT</td><td>69.2</td><td>76.0</td><td>71.8</td><td>87.6</td><td>87.4</td><td>87.4</td>
    </tr>
    <tr>
      <td rowspan="3">Base-LLMs</td>
      <td>ChatGPT</td><td>50.8</td><td>52.3</td><td>46.9</td><td>59.2</td><td>58.1</td><td>56.7</td>
    </tr>
    <tr>
      <td>GPT-4.0</td><td>51.5</td><td>57.5</td><td>54.3</td><td>60.8</td><td>60.3</td><td>60.5</td>
    </tr>
    <tr>
      <td>Claude-3</td><td>52.3</td><td>52.5</td><td>52.3</td><td>61.6</td><td>64.1</td><td>63.2</td>
    </tr>
    <tr>
      <td rowspan="2">Base-LLMs</td>
      <td>LLama-2-7B</td><td>50.9</td><td>52.6</td><td>51.4</td><td>49.9</td><td>49.7</td><td>49.7</td>
    </tr>
    <tr>
      <td>ChatGLM-3-6B</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td>
    </tr>
    <tr>
      <td rowspan="1">LLMs (Ours)</td>
      <td><strong>PclGPT-EN</strong></td><td><strong>80.4</strong></td><td><strong>81.8</strong></td><td><strong>81.1</strong></td><td><strong>89.9</strong></td><td><strong>89.0</strong></td><td><strong>88.9</strong></td>
    </tr>
  </tbody>
</table>


## 中文
在PclGPT-CN 中文组的检测任务中的结果为
<table>
  <thead>
    <tr>
      <th rowspan="2">LM</th>
      <th rowspan="2">Model</th>
      <th colspan="3">CPCL (CN)</th>
    </tr>
    <tr>
      <th>P</th><th>R</th><th>F1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="4">PLMs</td>
      <td>RoBERTa</td><td>61.2</td><td>61.3</td><td>61.3</td>
    </tr>
    <tr>
      <td>RoBERTa-L</td><td>62.5</td><td>61.6</td><td>62.0</td>
    </tr>
    <tr>
      <td>Chinese-BERT</td><td>66.6</td><td>71.0</td><td>67.3</td>
    </tr>
    <tr>
      <td>M-BERT</td><td>65.8</td><td>67.8</td><td>66.6</td>
    </tr>
    <tr>
      <td rowspan="3">Base-LLMs</td>
      <td>ChatGPT</td><td>53.1</td><td>54.2</td><td>53.6</td>
    </tr>
    <tr>
      <td>GPT-4.0</td><td>55.4</td><td>56.3</td><td>55.7</td>
    </tr>
    <tr>
      <td>Claude-3</td><td>57.2</td><td>57.7</td><td>57.3</td>
    </tr>
    <tr>
      <td rowspan="2">Base-LLMs</td>
      <td>LLama-2-7B</td><td>45.2</td><td>47.5</td><td>46.3</td>
    </tr>
    <tr>
      <td>ChatGLM-3-6B</td><td>51.9</td><td>50.2</td><td>51.0</td>
    </tr>
    <tr>
      <td rowspan="1">LLMs (Ours)</td>
      <td><strong>PclGPT-CN</strong></td><td><strong>69.1</strong></td><td><strong>72.0</strong></td><td><strong>70.2</strong></td>
    </tr>
  </tbody>
</table>


# 权重和下载
我们在Hugging Face上发布了我们的 PclGPT-CN 和 PclGPT-EN 的 1.0版本权重 

PclGPT-EN: [https://huggingface.co/DUTIR-Wang/PclGPT-EN](https://huggingface.co/DUTIR-Wang/PclGPT-EN)

PclGPT-CN: [https://huggingface.co/DUTIR-Wang/PclGPT-CN](https://huggingface.co/DUTIR-Wang/PclGPT-CN)

# 推理
下载权重后，使用以下代码进行PclGPT-EN的单条推理
```python
from transformers import LlamaTokenizer, LlamaForCausalLM

# 加载LLaMA模型和Tokenizer
tokenizer = LlamaTokenizer.from_pretrained("DUTIR-Wang/PclGPT-EN")
model = LlamaForCausalLM.from_pretrained("DUTIR-Wang/PclGPT-EN").half().cuda()

def generate_response():
    # 样例文本
    sample_text = "For someone who's just a mere street sweeper, you sure think highly of yourself."
    
    instruction = (
        "Suppose you are a linguist and you are asked to judge whether a text is patronizing and condescending. "
        "Patronizing and condescending language expresses a sense of superiority or belittles others, making them feel inferior or incapable. "
        "# Your return: Based on the following conversation, make a decision and return your choice. "
        "FALSE means the text is not a condescending language, and TRUE means the text is a condescending language. "
        "-> here is the text: （{}）"
    ).format(sample_text)

    # Tokenizer 和模型推理
    inputs = tokenizer(instruction, return_tensors="pt").to("cuda")
    outputs = model.generate(**inputs, max_length=1024)
    output_text = tokenizer.decode(outputs[0], skip_special_tokens=True)
    model_output = extract_option(output_text)
    return classify_output(model_output)

def extract_option(output_text):
    options = ['TRUE', 'FALSE']
    for option in options:
        if option in output_text:
            return option
    return "无法识别的输出"

def classify_output(model_output):
    # 根据模型输出返回解释
    return "The text is {} a condescending language.".format(
        "not" if model_output == "FALSE" else ""
    )

response = generate_response()
print(response)
```
得到的输出为
```
"The text is a condescending language."
```

下载权重后，使用以下代码进行PclGPT-CN的单条推理

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained("DUTIR-Wang/PclGPT-CN", trust_remote_code=True)
model = AutoModel.from_pretrained("DUTIR-Wang/PclGPT-CN", trust_remote_code=True).half().cuda()

def generate_response():
    # 样例文本
    sample_text = "区区扫地的，你可真是厉害坏了"
    
    instruction = (
        "假定你是一名语言学家，检测居高临下言论。居高临下言论是优势地位群体针对弱势群体的优越言论，"
        "语言攻击性较弱，但往往夹杂着讽刺，刻板印象，会对弱势群体造成伤害。"
        "居高临下根据语气程度分为 A级：非居高临下（正常非歧视、非冷暴力言论），"
        "B级：轻微居高临下（语气略带鼓励或怜悯），C级：中等居高临下（说话人较为客观陈述，但语气带有歧视），"
        "D级：严重居高临下（说话人语气轻蔑，严重歧视弱势群体）。"
        "接下来将给你一段文本，根据上述规则，你负责判断该文本属于（A/B/C/D级）的哪一级，并只回答选项。"
        "-> 文本：({})"
    ).format(sample_text)

    # Tokenizer 和模型推理
    inputs = tokenizer(instruction, return_tensors="pt").to("cuda")
    outputs = model.generate(**inputs, max_length=1024)
    output_text = tokenizer.decode(outputs[0], skip_special_tokens=True)
    model_output = extract_option(output_text)
    return classify_output(model_output)

def extract_option(output_text):
    options = ['A', 'B', 'C', 'D']
    for char in reversed(output_text.strip()):
        if char in options:
            return char
    return "无法识别的输出" 

def classify_output(model_output):
    # 根据模型输出的选项返回相应的解释
    if model_output == "A":
        return "判断为A级：非居高临下"
    elif model_output == "B":
        return "判断为B级：轻微居高临下"
    elif model_output == "C":
        return "判断为C级：中等居高临下"
    elif model_output == "D":
        return "判断为D级：严重居高临下"
    else:
        return "无法识别的输出，请检查输入或模型输出"

response = generate_response()
print(response)
```
得到的输出为
```
"判断为D级：严重居高临下"
```

# 声明
**本文研究的工作隶属于毒性言论（Toxic Speech）的子范围，居高临下言论属于微攻击言论的一种，因此本研究的部分工作可能会造成用户的不适和敏感。本研究仅用于弱势群体保护和互联网言论攻击治理（判别），请勿使用模型权重进行任何有害内容生成！**
