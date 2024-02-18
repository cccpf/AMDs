# AMDs
AMDs是基于智能体框架的中文医疗问答系统，通过结合不同的知识包括知识图谱以支持多轮医疗对话。希望AMDs的出现能够促进多轮医疗对话系统的开发研究和应用，让更多的人享受到便捷的医疗咨询服务。

## 介绍
与现有的其他对话系统相比,AMDs使用基于Agent框架的改进架构使其更易于扩展并能更好的结合知识图谱等进而处理复杂的多轮医疗对话任务，此外多种知识的结合使用能更好的提升模型生成过程的可解释性以及最终结果的准确性。

您可以通过[huggingface](https://huggingface.co/cpf99/AMDs/tree/main)，或是[百度云网盘(提取码2024)](https://pan.baidu.com/s/1OEJL65F-fJil3ib8RaXKrA)获得AMDs完整代码及模型权重。

## 效果演示
https://github.com/cccpf/AMDs/assets/46877660/9da577b4-bc92-4e75-af12-3be6bb647acd

https://github.com/cccpf/AMDs/assets/46877660/faa7f2b0-79bd-406f-9fb4-6d05197d4d18

## 部署方式 
### 1、下载[chatglm3](https://huggingface.co/THUDM/chatglm3-6b/tree/main)，创建文件夹./chatglm3,并将下载文件导入，该文件夹位置为项目文件同级。例如，./root/chatglm3与./root/AMDs

### 2、创建conda环境，python版本选择3.8
`conda create -n api python=3.8`

### 3、进入该环境
`conda activate api`

### 4、安装有关依赖，进入./api目录安装包。
`cd ./api`
<br>
`pip install -r requirements.txt`

### 5、在该python环境下运行服务。
`python manage.py runserver 8000`

### 6、创建另一个conda环境，python版本选择3.9
`conda create -n dialogsystem python=3.9`

### 7、进入该环境
`conda activate dialogsystem`

### 8、安装有关依赖，进入./agents目录安装包。
`cd ./agents`
<br>
`pip install -r requirements.txt`

### 9、安装依赖
`pip install fastapi`
<br>
`pip install "uvicorn[standard]"`

### 10、进入./agents/example目录，运行demo。
`python run.py`

## API部署
### 进入./agents/example目录，运行程序
`python run_backend.py`

### 默认部署在本地的 8080 端口，通过 GET 方法进行调用
```json
{
  "query": "前1周有脖子处淋巴结肿大。发烧",
  "history":[["小孩5岁，从6月至今，总是间接性咳嗽，偶尔有痰，不思饮食，中间吃过头孢克洛，阿莫西林，止咳糖浆，盐酸溴索口服液，利巴韦林喷剂	等药，总是时好时犯，请问怎么办，谢谢医生", "这个孩子除了咳嗽以外，还有其他的症状吗？"]],
}
```
### 得到结果
```json
{
  "target": "那这个孩子是不是嗓子发炎了？嗓子红不红",
}
```

## 计算资源需求
模型的微调过程中在一张V100显卡上进行了训练，显存占用在16G左右。模型仅推理情况下，占用显存在14G左右。预计在3090/4090显卡及以上显卡可以较好支持，根据显存大小来调整batch_size可降低要求。

## 问题
### 1. 报错packaging.version.InvalidVersion: Invalid version: '0.10.1,<0.11'：
`pip install packaging==21.3`
   
## 声明
本项目仅供学术研究之用，严禁用于商业用途。使用涉及第三方代码的部分时，请严格遵循相应的开源协议。模型生成的内容受模型大小、计算、随机性和量化精度损失等因素影响，本项目无法对其准确性作出保证。模型生成结果，即使符合某些医学事实，也不能被用作实际医学诊断的依据。对于模型输出的任何内容，本项目不承担任何法律责任，亦不对因使用相关资源和输出结果而可能产生的任何损失承担责任。
<br><br>