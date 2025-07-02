# 7-2
# 匯入函式庫
import openai
from google.colab import userdata

# 安全地讀取 API 金鑰（請先在 Colab 的 🔑 Secrets 設定 OPENAI_API_KEY）
openai.api_key = userdata.get('OPENAI_API_KEY')

# 設定要傳送給 AI 的提示
prompt = "請幫我寫一段 Python 最好的入門方法"

# 發送請求到 ChatGPT 模型
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",  # 你有 GPT-4 的話也可以改成 "gpt-4"
    messages=[
        {"role": "system", "content": "你是一位資深 Python 教學助理"},
        {"role": "user", "content": prompt}
    ]
)

# 取出 AI 的回應內容
answer = response.choices[0].message.content

# 印出回應內容
print("AI 回覆：\n", answer)

# 將回應寫入檔案
with open("ai_response.txt", "w", encoding="utf-8") as f:
    f.write(answer)
