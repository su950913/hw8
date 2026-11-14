# 測試一：原始資料

```python
# 1. 原始資料：保留文字資料，另外建立整理後的變數。
event_name = "  WEEKEND DINNER  "
meal_amount = " NT$1,200 "
people = "4"

service_rate = 0.10
discount = 100
budget_per_person = 300

# 2. 整理聚餐名稱。
clean_event_name = event_name.strip().lower()

# 3. 清理餐費文字，再轉換餐費與人數的型別。
clean_meal_text = meal_amount.replace("NT$", "").replace(",", "").replace(" ", "")
meal_value = float(clean_meal_text)
people_count = int(people)

# 4. 先按原始餐費計算服務費，再扣除折價券。
service_fee = meal_value * service_rate
total_amount = meal_value + service_fee - discount
amount_per_person = total_amount / people_count

# 5. 比較結果直接保存為 bool。等於預算時不算超過。
is_over_budget = amount_per_person > budget_per_person

# 6. 輸出時才將金額格式化為兩位小數。
print(f"聚餐名稱：{clean_event_name}")
print(f"原始餐費：{meal_value:.2f} 元")
print(f"服務費：{service_fee:.2f} 元")
print(f"折價券：{discount:.2f} 元")
print(f"應付總額：{total_amount:.2f} 元")
print(f"分攤人數：{people_count} 人")
print(f"每人費用：{amount_per_person:.2f} 元")
print(f"每人預算：{budget_per_person:.2f} 元")
print(f"是否超過預算：{is_over_budget}")
```

# 測試二：只將人數改成 5 人

```python
# 1. 原始資料：保留文字資料，另外建立整理後的變數。
event_name = "  WEEKEND DINNER  "
meal_amount = " NT$1,200 "
people = "5"

service_rate = 0.10
discount = 100
budget_per_person = 300

# 2. 整理聚餐名稱。
clean_event_name = event_name.strip().lower()

# 3. 清理餐費文字，再轉換餐費與人數的型別。
clean_meal_text = meal_amount.replace("NT$", "").replace(",", "").replace(" ", "")
meal_value = float(clean_meal_text)
people_count = int(people)

# 4. 先按原始餐費計算服務費，再扣除折價券。
service_fee = meal_value * service_rate
total_amount = meal_value + service_fee - discount
amount_per_person = total_amount / people_count

# 5. 比較結果直接保存為 bool。等於預算時不算超過。
is_over_budget = amount_per_person > budget_per_person

# 6. 輸出時才將金額格式化為兩位小數。
print(f"聚餐名稱：{clean_event_name}")
print(f"原始餐費：{meal_value:.2f} 元")
print(f"服務費：{service_fee:.2f} 元")
print(f"折價券：{discount:.2f} 元")
print(f"應付總額：{total_amount:.2f} 元")
print(f"分攤人數：{people_count} 人")
print(f"每人費用：{amount_per_person:.2f} 元")
print(f"每人預算：{budget_per_person:.2f} 元")
print(f"是否超過預算：{is_over_budget}")
```

# 測試三：恢復 4 人，折價券改成 220 元

```python
# 1. 原始資料：保留文字資料，另外建立整理後的變數。
event_name = "  WEEKEND DINNER  "
meal_amount = " NT$1,200 "
people = "4"

service_rate = 0.10
discount = 220
budget_per_person = 300

# 2. 整理聚餐名稱。
clean_event_name = event_name.strip().lower()

# 3. 清理餐費文字，再轉換餐費與人數的型別。
clean_meal_text = meal_amount.replace("NT$", "").replace(",", "").replace(" ", "")
meal_value = float(clean_meal_text)
people_count = int(people)

# 4. 先按原始餐費計算服務費，再扣除折價券。
service_fee = meal_value * service_rate
total_amount = meal_value + service_fee - discount
amount_per_person = total_amount / people_count

# 5. 比較結果直接保存為 bool。等於預算時不算超過。
is_over_budget = amount_per_person > budget_per_person

# 6. 輸出時才將金額格式化為兩位小數。
print(f"聚餐名稱：{clean_event_name}")
print(f"原始餐費：{meal_value:.2f} 元")
print(f"服務費：{service_fee:.2f} 元")
print(f"折價券：{discount:.2f} 元")
print(f"應付總額：{total_amount:.2f} 元")
print(f"分攤人數：{people_count} 人")
print(f"每人費用：{amount_per_person:.2f} 元")
print(f"每人預算：{budget_per_person:.2f} 元")
print(f"是否超過預算：{is_over_budget}")
```

總額為 `1200 + 120 - 220 = 1100` 元，平均分給 4 人，每人 275 元，沒有超過 300 元預算。

# 三組測試摘要

| 測試 | 人數 | 折價券 | 服務費 | 應付總額 | 每人費用 | 超過每人預算 |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| 第一組 | 4 | 100 元 | 120 元 | 1,220 元 | 305 元 | `True` |
| 第二組 | 5 | 100 元 | 120 元 | 1,220 元 | 244 元 | `False` |
| 第三組 | 4 | 220 元 | 120 元 | 1,100 元 | 275 元 | `False` |

# 程式逐步說明

```markdown
## 程式逐步詳細說明

本程式透過 Python 進行資料整理、數學運算與邏輯判斷。以下為程式執行的詳細步驟拆解：

### 步驟 1：原始資料輸入與宣告
在每組測試的開頭，我們定義了原始的文字與數值變數。為了模擬真實世界中非格式化的資料輸入（例如前後有空格或帶有貨幣符號），部分變數是以字串形式儲存：
* `event_name`: 包含前後多餘空格且為大寫的聚餐名稱（例如 `"  WEEKEND DINNER  "`）。
* `meal_amount`: 包含貨幣符號、千分位逗號與空格的餐費字串（例如 `" NT$1,200 "`）。
* `people`: 字串型態的分攤人數。
* `service_rate` / `discount` / `budget_per_person`: 分別為服務費率（10%）、折價券金額及個人預算（300 元）。

### 步驟 2：文字資料清理與格式標準化
* **名稱標準化**：使用 `event_name.strip().lower()` 去除前後空格並轉換為小寫，確保輸出為統一格式（`weekend dinner`）。
* **金額字串清洗**：利用 `.replace()` 鏈式操作，將 `meal_amount` 中的 `"NT$"`、逗號 `","` 和空格全部移除，只留下純數字字串。

### 步驟 3：資料型態轉換
由於清洗完後的餐費與人數仍為字串型態，無法直接進行數學運算，因此：
* 使用 `float(clean_meal_text)` 將餐費轉為浮點數（`1200.0`）。
* 使用 `int(people)` 將人數轉為整數。

### 步驟 4：核心商業邏輯與費用計算
費用的計算順序至關重要：
1. **服務費計算**：依據原始餐費計算服務費：
   $$\text{服務費} = \text{原始餐費} \times \text{服務費率 (0.10)} = 120.0\text{ 元}$$
2. **應付總額計算**：將原始餐費加上服務費，再扣除折價券折抵金額：
   $$\text{應付總額} = \text{原始餐費} + \text{服務費} - \text{折價券}$$
   * 測試一、二（折價券 100 元）：$1200 + 120 - 100 = 1220.0\text{ 元}$
   * 測試三（折價券 220 元）：$1200 + 120 - 220 = 1100.0\text{ 元}$
3. **個人分攤費用**：
   $$\text{每人費用} = \frac{\text{應付總額}}{\text{分攤人數}}$$
   * 測試一（4人）：$1220 / 4 = 305.0\text{ 元}$
   * 測試二（5人）：$1220 / 5 = 244.0\text{ 元}$
   * 測試三（4人）：$1100 / 4 = 275.0\text{ 元}$

### 步驟 5：預算超支邏輯判定
* 透過比較運算子 `>` 判斷每人分攤費用是否大於個人預算（`300.0`）。
* 判斷結果會直接以布林值（`True` 或 `False`）儲存於 `is_over_budget` 變數中。
* 規則設定：若每人分攤費用精確等於預算時，不屬於「超過」，故不使用 `>=`。

### 步驟 6：格式化輸出與綜合比較
* 在各測試儲存格中，使用 f-string 的格式化語法 `:.2f}` 將所有金額數值限制在小數點後兩位輸出，兼顧精準度與易讀性。
* 最後，我們利用 `pandas` 套件將這三組測試的輸入與計算結果收集在一個字典中，並建立 DataFrame（綜合比較表），提供清晰且結構化的最終總覽。
```

# 兩題問答參考答案

# 問題一：為什麼 "4" 要先轉成數字？

在 Python 等程式語言中，將代表人數的 "4"（包含引號的字串，String）轉換為整數 4（Integer）是必要的步驟，原因如下：

1.字串不支援除法運算： 程式中的應付總額（例如 1220.0）是浮點數（數字），如果直接拿來除以字串 "4"，Python 會拋出型態錯誤（TypeError）：unsupported operand type(s) for /=: 'float' and 'str'。因為程式不認得如何將一個金額除以一段文字。

2.字串乘法與數值乘法的差異： 雖然有些運算子在字串中可以使用，但意義完全不同。例如 "4" * 3 在 Python 中會變成 "444"（字串重複三次），而不是數學上的 12。同樣地，除法在字串上完全沒有被定義。

因此，在計算每人分攤費用（應付總額 / 人數）之前，必須先透過 int("4") 將其轉換成數值型態的 4，才能進行正確的數學除法運算。

# 問題二解答：如果先扣折價券，再計算服務費？

果計算順序改為**「先扣除折價券，再計算服務費」**，將會對最終的服務費和應付總額產生以下影響：

1. 計算公式的改變：
原本的計算方式（先計服務費，再扣折價券）： $$\text{服務費} = 1200 \times 10\% = 120\text{ 元}$$$$\text{服務費} = 1200 \times 10\% = 120\text{ 元}$$ $$\text{應付總額} = 1200 + 120 - 100 = 1220\text{ 元}$$$$\text{應付總額} = 1200 + 120 - 100 = 1220\text{ 元}$$

改變後的計算方式（先扣折價券，再計服務費）： $$\text{計費基數} = 1200 - 100 = 1100\text{ 元}$$$$\text{計費基數} = 1200 - 100 = 1100\text{ 元}$$ $$\text{服務費} = 1100 \times 10\% = 110\text{ 元}$$$$\text{服務費} = 1100 \times 10\% = 110\text{ 元}$$ $$\text{應付總額} = 1100 + 110 = 1210\text{ 元}$$$$\text{應付總額} = 1100 + 110 = 1210\text{ 元}$$

2. 影響分析：
服務費減少：服務費從原本的 $120$$120$ 元減少為 $110$$110$ 元（減少了 $10$$10$ 元）。這是因為折價券折抵的 $100$$100$ 元在計算前就被扣除，導致計算服務費的基數變小了（少了 $100 \times 10\% = 10$$100 \times 10\% = 10$ 元的服務費）。
應付總額減少：應付總額也相應地由 $1220$$1220$ 元變為 $1210$$1210$ 元，顧客整體花費變得更便宜。
3. 商業實務背景：
在多數餐廳的實務中，服務費通常是依照「原價（折扣前）」來計算的。因此，原程式所寫的「先算原價的服務費，再扣除折價券」是最符合多數餐廳實際消費場景的邏輯。

## AI使用紀錄

### AI 使用紀錄

* **使用工具**：
  * Colab Copilot / Colab AI Composer
  * Python 3 (NumPy, Pandas, Matplotlib)

* **主要提示詞**：
  * *「請計算不同人數下的預算分攤表並繪製圖表」*
  * *「請完成以下三組測試，保留每一組的輸入與實際執行結果。每組都從題目原始資料出發，只修改表中指定的項目。請在筆記本中分別標示『測試一』『測試二』『測試三』。」*
  * *「將三次測試的結果整理成一個綜合比較表格」*
  * *「將三次測試的結果整理成一個程式逐步說明」*

* **修改或驗證**：
  * **文字清洗驗證**：在每組測試中，成功利用 `.strip().lower()` 將聚餐名稱 `"  WEEKEND DINNER  "` 轉換成標準的 `"weekend dinner"`，並使用 `.replace()` 鏈式處理排除貨幣符號 `NT$`、逗號與空格，將餐費正確轉為浮點數 `1200.0`。
  * **邏輯運算驗證**：
    * **測試一**：輸入人數 4、折價券 100 元 $\rightarrow$ 計算出應付總額 1220 元，每人分攤 305 元。因為 305 > 300，系統精確判定「超過每人預算」為 `True`。
    * **測試二**：輸入人數 5、折價券 100 元 $\rightarrow$ 每人分攤 244 元，精確判定「超過每人預算」為 `False`。
    * **測試三**：輸入人數 4、折價券 220 元 $\rightarrow$ 每人分攤 275 元，精確判定「超過每人預算」為 `False`。
  * **整合輸出**：透過 Pandas 建立綜合比較表（DataFrame），以及編寫逐步流程文字說明，確保所有測試數據一致，且計算路徑與實務商業邏輯（先加計原價之服務費再扣折價券）完全相符。
