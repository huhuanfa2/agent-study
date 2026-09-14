# task00 环境配置

## 使用uv管理项目
```
# 在项目目录下初始化项目
mkdir hh
cd hh
uv init
```
## 安装依赖包
```
uv add requests
uv add tavily-python
uv add openai
uv add python-dotenv
```
## 配置模型api_key
```
TAVILY_API_KEY="tvly-dev-xxx"
LLM_API_KEY="ms-xxx"
LLM_BASE_URL='https://api-inference.modelscope.cn/v1'
LLM_MODEL_ID="deepseek-ai/DeepSeek-V4-Pro"
```
## 拷贝code/chapter1/FirstAgentTest.py，修改后运行
```
$ uv run python FirstAgentTest.py
用户输入: 你好，请帮我查询一下今天北京的天气，然后根据天气推荐一个合适的旅游景点。
========================================
--- 循环 1 ---

正在调用大语言模型...
大语言模型响应成功。
模型输出:
Thought: 首先需要查询北京的实时天气，以便根据天气推荐合适的旅游景点。

Action: get_weather(city="北京")

Observation: 北京当前天气：Sunny，气温27摄氏度
========================================
--- 循环 2 ---

正在调用大语言模型...
大语言模型响应成功。
模型输出:
好的，已经获得北京的天气数据。天气为晴天，气温27度，非常舒服。接下来需要基于这个天气信息，搜索北京适合晴天游玩的景点。

Action: get_attraction(city="北京", weather="Sunny")

Observation: Under sunny weather, Tiananmen Square, Temple of Heaven, and the Olympic Park are top picks for sightseeing in Beijing. These spots offer clear views and are easily accessible.
========================================
--- 循环 3 ---

正在调用大语言模型...
大语言模型响应成功。
模型输出:
Thought: 已获取北京天气（晴天，27°C）及推荐景点，可以给出最终推荐。
Action: Finish[今天北京天气晴朗，气温27°C，非常适合户外活动。推荐您前往天安门广场、天坛或奥林匹克公园，这些景点视野开阔、交通便利，非常适宜晴天游览。]

任务完成，最终答案: 今天北京天气晴朗，气温27°C，非常适合户外活动。推荐您前往天安门广场、天坛或奥林匹克公园，这些景点视野开阔、交通便利，非常适宜晴天游览。
```
