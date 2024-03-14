# Data-mining
資料探勘
## Lab 1
運用python嘗試連線Azure OpenAI做出推薦系統
```python
import requests
import json

# 設定 Azure OpenAI 端點 URL
url = "https://ntnu-ml.openai.azure.com/openai/deployments/ntnu-ml-gpt4-32k/chat/completions?api-version=2024-02-15-preview"

# 設定 API 金鑰
api_key = "YOUR_API_KEY"

# 設定請求中的 JSON 數據
payload = {
    "messages": [
        {"role": "system", "content": "根據 `` 中提供的 rating.csv 資料，用協同過濾的概念推薦餐廳給使用者 ，請以 json array 格式回答\n\`\ncustomerId,restaurantId,rating\nc1,r2,3\nc1,r3,1\nc1,r5,3\nc1,r6,2\nc2,r1,3\nc2,r3,1\nc2,r5,1\nc2,r6,1\nc3,r4,3\nc3,r5,3\nc3,r6,3\nc4,r1,1\nc4,r4,1\nc4,r5,3\nc5,r2,1\nc5,r3,2\nc5,r4,3\nc6,r2,3\nc6,r3,3\nc6,r5,3\nc7,r2,3\nc7,r3,3\nc7,r4,1\nc8,r1,2\nc8,r2,1\nc8,r5,1\nc8,r6,2\n`"},
        {"role": "user", "content": "c1"}
    ],
    "max_tokens": 800,
    "temperature": 0.5,
    "frequency_penalty": 0,
    "presence_penalty": 0,
    "top_p": 0.95,
    "stop": None
}

# 設定請求頭
headers = {
    "Content-Type": "application/json",
    "api-key": api_key
}

# 發送 POST 請求
response = requests.post(url, headers=headers, json=payload)

# 打印回應
print(response.json())
```
