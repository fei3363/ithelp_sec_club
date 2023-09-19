# day4

社團經營當中，總是在學校的下學期找到一個接班人，但更多時候其實從擔任社長開始就需要開始準備傳承的內容。


![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/f6e3cc5d-006d-49cd-b8ff-bbdd06dc1cfb)

## 常見問題
1. 你是否已經遇到了找不到下一屆幹部的問題
2. 你辛辛苦苦經營的社團，但沒有接班人
3. 你是新手社長，所以你不知道有這個挑戰

## 逢甲黑客社經驗分享

### 說明
以黑客社的來說，主要核心幹部是大三擔任，但每一間學校都不太一樣，因此可以根據社團的組成來思考應對方法。
每一個解決方案都不同，當初以儲備幹部計畫，來展開，從大一開始培養，分成行政與技術，寒假與暑假都有幹部訓練。

### 儲備幹部
1. 利用面試的方法找到新的對社團經營有興趣、熱情的學弟妹
2. 設計儲備幹部讀書會，每週上台練習十分鐘分享內容
3. 共同一起讀書，協助學弟妹在學業上也可以提供幫助

## 傳承要點
1. 確定傳承的核心內容：需要確定想傳承什麼知識或經驗。
2. 選擇合適的接班人：找到合適的人選來傳承知識和經驗。
3. 資料收集：確保已充分利用各種資源並進行了資料收集。
4. 資料歸納：將收集的資料整理和歸納，以方便將來的使用。
5. 資料分析：分析現有資料以提供深入洞見和解決問題的方案。
6. 設計傳承方案：考慮傳承方案是一次性活動還是系列訓練(每週)。

### 電子化傳承
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/42758293-d422-4328-9755-f5d328593408)

1. 平台可以參考
  - 可以選擇 Google drive 來統整以往的 PPT
  - hackMD 或自架 CodiMD
2. 分類
  - 活動類型：社團籌備會/行前會/活動共筆/檢討會/社課
  - 資料類型：照片/程式碼/設計檔案/海報/心得回饋

## 台科資安社經驗分享
因為擔任社長的時候，對台科的受眾不太熟悉，因此第一年偏向自己講課、找學弟妹講課、找外部講師講課，決定先了解整個學校對於社團的態度。
陸陸續續認識學弟妹之後，先找到幾個有興趣繼續經營社團的學弟妹，鼓勵他們自己討論對應的內容，之後擔任顧問的角色，讓學弟妹自由發揮。

![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/81b564b8-9e13-4ac6-a8d7-dc5ca2bb6bfb)





## 社團系統: 歷屆幹部功能

### 資料庫的設計

#### 幹部資訊
1. 幹部名稱
2. 暱稱
3. 屆數
4. 任期時間
5. 任期結束
6. 照片
7. 說明

```
class Executive(models.Model):
    name = models.CharField(max_length=30, null=True, blank=True)
    nickname = models.CharField(max_length=30, null=True, blank=True)
    session = models.PositiveIntegerField(help_text="屆數")
    tenure_start = models.DateField()
    tenure_end = models.DateField()
    position = models.CharField(max_length=100)
    photo = models.ImageField(upload_to='executives/photos/', null=True, blank=True)
    biography = models.TextField(null=True, blank=True)
    
    def __str__(self):
        return f"{self.first_name} {self.last_name}"
```

### 於介面新增
1. 新增 Member
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/f532dee1-a846-44a6-a22d-c4ec551e2cc5)
2. 新增 Executive
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/1ea76802-7c50-4b86-b9de-3d857fbd0e5d)
3. 新增欄位(根據上面的內容將欄位新增完畢)
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/997c5e1b-97d5-4e84-83ce-160a2f9f583e)
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/05d89611-0f31-4676-aaff-60c9296ade25)
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/4888dc06-95e3-42b3-add8-77eed4473cec)
4. 下載後，記得更新之前的 APP 內容
5. 執行資料庫 migrate
`python3 manage.py makemigrations`
`python3 manage.py migrate`
6. 啟動伺服器
`python3 manage.py runserver`
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/aba21a88-7ebd-4ef5-9898-18e89e82470b)

### 操作
1. 進入瀏覽器
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/a75c7835-fa1f-4c6b-970d-982893960760)
2. 點選 Executive
3. 新增幹部
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/7c59ab44-af5c-4892-b98c-32cad4077978)
4. ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/2c87aaef-11ee-4f95-9e01-7c21a0846e2d)



