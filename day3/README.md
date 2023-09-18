# 社團如何設計課程
## 談談課程如何設計
第二個元素就是學術型社團會有的內容
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/f07083ce-2f99-43e3-8379-c5165df35111)


### 課程設計的要點
1. 符合社團的理念(新手入門、技術宣傳、解析技術)
2. 了解目前受眾的類型(科系、背景、過去修過什麼課程)
3. 設計課程(簡報、演講技巧)

## 行動方案

1. 找理念
2. 找客群
3. 設計課程
4. 規劃與行動

### Step 1. 找理念
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/f02c8803-83ca-40d3-86e8-064d7b995cfc)

#### 說明與舉例
- 確認社團的理念，也確認課程核心目標
  - 理念可以對應目的與方向
- 以黑客社為例
  - 動作: 推廣程式設計、資安概念與資訊議題
  - 目的: 提升資安意識和好奇心

#### 行動清單
- 從社團規範當中列下使命與願景
- 列出希望學員在課程中了解哪些知識


### Step 2. 找客群
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/d98a7c46-6ce6-4aa4-b9d2-d91d8e40f0f8)

#### 說明與舉例
- 動作：要知道你的客群背景、需求、興趣
- 目的：了解後，才可以設計對方所需要的課程

#### 行動清單
1. 口頭聊天、問卷調查了解目標受眾的背景
  - 什麼系
  - 幾年級
  - 為什麼來上課
2. 根據受眾背景和需求來定義課程的內容

### Step 3. 設計課程
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/d9eca12d-85d7-4e0d-a2af-7a8b6a1d9220)

#### 說明與舉例
- 設計課程了解目標受眾之後，會需要基於目標受眾去設計內容
  - 如：課程結構、課程框架
- 學員上手的難度 vs 講師講解的難度
  - 工作坊 > 經驗分享 > 純演講
 
#### 行動清單
1. 分析目標受眾需要哪一些課程
2. 確認課程主題與方向
3. 準備教學內容，如簡報與實作環境
4. 觀察別人教學，哪一些也是自己可以學習與嘗試


### Step 4. 規劃與行動
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/ffd673f9-a274-4c49-8d39-46e31c42c6c6)

#### 說明與舉例
- 開始課程，可以利用課前、課中、課後來思考。
  - 課前: 學員統計、學員預習內容
  - 課中: 觀察學員是否有皺眉頭
  - 課後: 追蹤與成效
    - 學員是否有跟上？
    - 學員在哪跟不上？
    - 學員為何跟不上？

#### 行動清單
1. 定期開會追蹤與了解成效
2. 根據開會內容調整社課內容與授課方式


## 社團系統：課程列表

### 規劃
以學校的社團來說通常會以年份與學期來區分課程，
每一個學期可能會有 12 堂的課程數量。

### User story
- 學員點選社課內容，會看到最新的課表
- 學員點選歷史列表，可以看到過去的課程
- 學員可以看到社課的日期、名稱、說明、講師
- 學員上完課之後，點選頁面可以看到社課的日期、名稱、說明、講師、簡報或 pdf

### 資料庫模型設計


#### Semester
- year (PositiveIntegerField): 學年度
- term (CharField): 學期，例如 "第一學期" 或 "第二學期"

#### Course
- semester (ForeignKey - Semester): 這門課程所屬的學期，與 Semester 模型有外鍵關聯
- date (DateField): 課程的日期
- name (CharField): 課程的名稱
- description (TextField): 課程的描述
- lecturer (CharField): 課程的講師

#### Resource
- course (ForeignKey - Course): 該資源所屬的課程，與 Course 模型有外鍵關聯
- resource_type (CharField): 資源的類型，例如 PPT, PDF, VIDEO 或 LINK
- link (URLField): 資源的路徑
- file(FileField): 上傳資源

#### 關係描述

1. Semester 與 Course
   - 一個 Semester 可以有多個 Course。
   - 關聯類型: 一對多

2. Course 與 Resource
   - 一門 Course 可以有多個 Resource。
   - 關聯類型: 一對多


每個 Course 都與一個特定的 Semester 關聯，並可以擁有多個與之相關的 Resource。此外，每個 Resource 都直接與一門特定的 Course 關聯。

### 步驟：利用昨天的工具
1. 新增 APP CourseManagement
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/7336d6f6-48d2-4338-b2f0-9e1e2acdc0b1)
2. 新增 Model Semester 與 欄位
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/18f85d50-cf7c-448c-b056-82be6f95a508)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/4b64ea08-9ea1-4cef-8b96-a3c50d4e8577)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/9594f158-d432-42ca-9d4a-92c302d50919)
3. 新增 Model
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/a7ea1bf1-a2e0-4a74-aedf-f198ec7fe59e)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/d023bd7c-99bc-4192-bb6b-773905a0fdab)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/30f47359-5378-4b41-826e-ea3202cd9b47)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/f4b29eae-dad8-4381-8e43-99e2c3f49990)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/2a030a3b-5342-4be5-a2cc-c3d473e6b8ef)
   - 注意加入關係需要點橘黃色的按鈕
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/b0a7e80c-8574-4d3f-b8f7-bed9cdf00c95)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/5b0f23f5-7ea7-41c3-a890-e373218f5ffa)
4. 新增 Model
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/7d254fb7-34d5-4437-95a9-59b215d23893)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/446376df-f085-4892-bb4c-db462cda3fe7)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/1bfbf15f-1b66-4092-b6ae-6ab8942412d7)
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/e31acd49-7b6b-4f5f-8788-4217fc372310)
5. 下載檔案
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/4217e3b0-76bf-4719-b398-2d86c737e84d)
   - 將昨天撰寫好的 Regulations 記得蓋到新專案
6. 更新內容
   - python3 manage.py makemigrations
      - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/d8eee274-23a1-40e2-96a3-4b31c3d0ebda)
   - python3 manage.py migrate
      - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/b7079b58-2c9c-4fc8-849e-3e3aa1c8c3ec)
   - server python3 manage.py runserver
      - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/e23a6694-4bd2-42bb-bdc5-e8572a02faba)
7. 開啟瀏覽器
   - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/d38c8228-9fe9-47cc-8fc5-9b9be2eaf40b)
8. 操作
   - 新增學期
      - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/2fb50283-4819-4753-8b91-7e7beb26f270)
   - 新增課程(這個學期是 1 代表 id 1)
      - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/643a2b35-e4b0-4444-bfc8-c04b2fefc37a)
   - 新增資源
      - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/1d3be8a4-d87d-44a0-b31a-4d0fc4836311)
 






