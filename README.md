# Selenium_yamol

# 技術文件：使用 Selenium 自動化抓取網頁題目和答案

## 目錄

1. [簡介](#簡介)
2. [先決條件](#先決條件)
3. [環境設置](#環境設置)
4. [程式碼詳解](#程式碼詳解)
   - [初始化 WebDriver](#初始化-webdriver)
   - [登錄並導航](#登錄並導航)
   - [抓取題目和選項](#抓取題目和選項)
   - [儲存結果](#儲存結果)
5. [執行腳本](#執行腳本)
6. [常見問題](#常見問題)
7. [結論](#結論)

## 簡介

本技術文件旨在指導如何使用 Selenium 來自動化抓取網頁上的題目和答案，並將抓取的資料儲存為 CSV 檔案。這對於需要大量手動操作來收集資料的情況非常有用，可以顯著提高工作效率。

## 先決條件

在開始之前，請確保已經安裝以下軟體和庫：

1. Python 3.8.10
2. Selenium 4.21.0
3. Chrome 瀏覽器
4. ChromeDriver

## 環境設置

1. **安裝 Selenium：**

```
pip install selenium
```

下載並安裝 ChromeDriver：

下載對應你 Chrome 瀏覽器版本的 ChromeDriver，並將其添加到系統 PATH 中。

程式碼詳解
以下是完整的程式碼和各部分的詳細說明。

初始化 WebDriver
python
複製程式碼
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options

# 設置 Chrome 瀏覽器選項
chrome_options = Options()
chrome_options.add_argument("--headless")  # 啟用無頭模式
chrome_options.add_argument("--disable-gpu")

# 設置 ChromeDriver 的路徑
driver_path = 'chromedriver.exe'  # 替換為你的 chromedriver 路徑
service = Service(driver_path)

# 初始化 WebDriver
driver = webdriver.Chrome(service=service, options=chrome_options)
python
import time
import re

# 載入網頁
```
url = 'https://app.yamol.tw/exam/24548'  # 替換為你的目標 URL
driver.get(url)
```
# 等待網頁加載完成
time.sleep(5)  # 視情況調整等待時間

# 抓取題目和選項

i = 1 # 預設是從第一頁開始抓取


執行腳本
確保所有依賴項都已安裝並配置正確。

將上述程式碼儲存為一個 Python 檔案，例如 scraper.py。

在命令行中運行該腳本：

完成後，題目和答案將被儲存到 topic.csv 中。
***csv預覽畫面

![image](https://github.com/tn00627974/Selenium_yamol/assets/139155210/75b6e332-a98d-42d8-a233-1e089a10b364)


常見問題
問題：腳本無法找到某些元素
**解決方案：**檢查 XPATH 或 CSS 選擇器是否正確，並確保頁面已完全加載。在需要等待的地方可以適當增加 time.sleep() 的時間。

問題：抓取的選項數量不足
**解決方案：**使用程式碼補足選項數量，確保每組題目有五個選項。

結論
通過本技術文件，你應該能夠設置並運行一個自動化腳本，從網頁中抓取題目和答案並儲存為 CSV 檔案。這可以大大提高資料收集的效率，特別是在處理大量資料時。

如果有任何問題或改進建議，歡迎隨時聯繫我tn00627974@gmail.com。
