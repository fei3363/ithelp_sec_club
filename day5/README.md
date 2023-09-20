# Day5 經營社團的加速器

## 快速打造好一個學藝性的社團需要的元素
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/8f051ee1-d294-46b0-a372-aae80c61d5b6)

金錢與講師是兩個可以快速建立好社團的方法，但這個方法只限於讓「社團」可以活著，但如果沒有做好前幾天所介紹的行政、內部課程與傳承三個元素，社團可能會很容易夭折。

### 金錢
1. 通常用來舉辦資安/資訊相關的活動
2. 用來聘請講師的講師費用與交通費用
3. 購買必要的設備與工具
4. 行銷與宣傳社團

#### 申請經費與計畫書
許多時候學校可以為了支持社團因此可以跟學校的課外活動組（每一間學校的名稱都不太一樣）申請活動相關的經費。
在這個過程當中你可以就要學習如果撰寫計畫書。

1. 計畫主題
2. 計畫目的
3. 計畫內容
4. 計畫流程
5. 計畫有哪些人參與
6. 計畫預計花多少錢

#### 注意預算
1. 確認成本: 可以思考一個學生社團真的需要這麼多錢嗎
2. 是否有合作夥伴(資工系系辦、資管系系辦、學校)、贊助廠商(資安公司等)願意贊助
3. 社費花費，花到刀口上


### 講師
1. 希望邀請專業的講師來社團可以演講與分享業界的經驗
2. 希望有更好的課程品質

#### 講師從哪裡來
1. 歷屆的社團學長姐
2. 學界的老師（學校內部的教授、其他學校的教授）
3. 業界講師（在業界出社會多年）
4. 社群講師（許多社群都有支援講師，都可以問問看）

#### 如何邀請講師
1. 選擇講師: 根據社團內部所缺乏的能力或是預期想要邀請的講師
2. 邀請講師: 不管是寄信或其他的通訊軟體，都要記得**有禮貌**
  - 活動的目的和目標
  - 活動的時間和地點(地點注意是否電腦教室與網路)
  - 預期的參與人數
  - 講師的講課方式
  - 講師費用/交通費用
3. 隨時跟講師聯絡: 很多社團邀請完講師但都沒有更新後續
  - 可能會造成講師不清楚狀況(ex 活動取消)
4. 行前提醒講師
  - 時間/地點
5. 課前準備
  - 講師的水
  - 講師的領據
  - 講師的感謝狀
  - 課程的回饋表單
6. 課程過程中
  - 隨時注意講師有什麼需求
7. 課程結束
  - 給講師感謝狀
8. 課後
  - 給予講師回饋表單的內容


#### 課後的回饋
1. 收集講座的回饋內容
2. 跟講師聊社團的狀況


## 社團系統: 計劃書管理

### 資料庫
```
from django.db import models

class Project(models.Model):
    title = models.CharField(max_length=200)
    purpose = models.TextField()
    date = models.DateTimeField(auto_now_add=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    file = models.FileField(upload_to='projects/')
    session = models.PositiveIntegerField()

    def __str__(self):
        return self.title
```

### 說明
1. title:計畫的名稱。
2. purpose: 計畫的目的或說明。
3. date: 計畫日期。
4. created_at 和 updated_at: 新增與修改時間。
5. file: 計畫書的檔案。
6. session: 第幾屆

### 製作
1. 新增 Project 的 APP
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/7c934ce2-61bb-4236-8c87-26d0b19112a0)
2. 新增 Project 的 model
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/cb6268cd-f603-4a2b-90d3-0a2573767e55)
3. 新增欄位
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/cfba43b2-447c-494c-bbc7-d2a04aedea04)
4. 新增欄位
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/e0f7ab5b-a8df-4879-8ec3-0ac2b1fcd4a4)
5. 新增欄位
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/002cb4d9-075c-4876-8768-c70bff7a2735)
6. 新增欄位
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/23d7119f-5919-4c20-b4ff-1d7e74dfa0aa)
7. 新增欄位
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/25a14691-6ab9-425d-915a-1f5872ffb4eb)

### 更新
1. ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/a02e7f2f-1cf4-4857-a6bf-c92fa9f0b357)
2. ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/c7fb19b0-72d7-4ef5-b07b-19577044a5e5)
3. 開啟伺服器與瀏覽頁面
4. 新增活動
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/2c0d9ca9-3781-4659-9fc2-78d808719e38)
5. 確認新增成功
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/b3b21a68-efa0-4b09-a73f-7851adbcebc8)

