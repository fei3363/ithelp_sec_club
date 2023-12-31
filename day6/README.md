## 如果找不到資源

前一篇文章我們提到可以利用許多學校、公司的資源。
但如果真的很不幸，社團遇到資源不足的問題時，
最常面臨的是金錢和講師的問題。

![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/dc82b0c2-4e7a-45ac-a01e-12e5a9fe1858)

以下針對這兩個方面進行常見的解決方案與說明：

![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/1a7ca50d-ed8a-49b5-8062-a699ab101564)

### 講師

因為沒有相關的經費可以聘請講師時，可以從以下方向尋找：

- 現有幹部：從幹部中挑選合適的講師，只要之前有學習的經驗，就可以還是訓練分享的技巧，目前還是入門，但可以教超入門的方法。
  
- 學長姊：大三、大四的學長姐或是已經畢業的學長姊，之前已經有擔任過講師的經驗值，可以請學長姐來跟社員分享，或是帶實際操作的課程。甚至可以請學長姐直接回來教導如何「教學」。
  
講師教學方式：一個講師可以選擇很多教學的方式，常見的方法包含學校的講述式也可選擇互動式的課程。

- 講述式課程：準備簡報，上台報告與教學的方法。
- 互動式教學：透過問答，底下的同學互動。有些講師會利用分組討論的方式，使學員更容易理解與吸收。
- 實作課程：以實際操作的工作坊的方式，可以加強學員的實踐能力。

### 金錢

針對除了申請經費之外的方法就是社費，

- 社費：許多社團的資金來源，可以根據社團的需求和規模設定不同的金額，甚至可以祭出給予社員的禮物。

常見的社費的收取方式：
- 定期收費：例如每學期或每學年收取。
- 活動收費：針對特定的活動或課程收費，如果真的希望某一個講師來演講，可以酌收一點入場費用，除了限制入場人數，也可以保證有講師費給講師。

### 講師與金錢的關係
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/b4335373-b7d2-4f29-b214-8b757e523771)


如果選擇利用社團的幹部擔任講師，幹部的授課品質會直接影響到學員的滿意度，有可能進而影響社團的口碑和社費的收入。

因此，確保講師的品質是非常重要的。

## 不會教學，也不敢收錢
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/fad9bb8a-dec0-429c-bef9-5df0ed657d4d)


許多幹部可能會面對到社團無法收費被限制的問題，或是說完全沒有可以分享的人力，建議大家可以成立學習型社團，改變現有講課有講師的方式。

**宗旨：學習型讀書會**

社團的價值在於提供場地與討論方向，每週設定一個對應的研究主題並且設定實作或報告的知識點內容之，讓參與的學員自行分享研究的知識和經驗。

讀書會方向：
1. 不管是一本書還是一系列的文章。
2. 參加外部課程或工作坊，回來後分享所學習到的內容。
3. 與其他社團或組織合作，交換講師或共同舉辦活動。


如何培養校內的技術能力：
1. 定期舉辦內部幹部訓練，邀請有經驗的學長姊或外部講師分享。
2. 建立知識資料庫或資源平台，整理各種學習資料和教學影片，供學員自學。


## 社團系統目前功能盤點
- 友站連結功能
- 社團章程功能
- 課程管理功能
- 歷屆幹部功能
- 歷史計劃書功能

## 社團系統: 新增社團活動相簿功能

### 資料庫設定

```
from django.db import models

class Album(models.Model):
    title = models.CharField(max_length=200)  # 活動名稱
    date = models.DateField()  # 日期
    session = models.PositiveIntegerField()  # 屆數

class Photo(models.Model):
    album = models.ForeignKey(Album, related_name='photos', on_delete=models.CASCADE)
    image = models.ImageField(upload_to='albums/photos/')  # 照片
    caption = models.TextField(blank=True, null=True)  # 照片的描述或標題
```

### 建立

1. 新增 app Album
- ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/47e84201-dab9-4a05-8f01-4e2c460226c6)
2. 新增 models Album
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/4e198a46-87f2-4f81-b544-5ad2bb2e1c0a)
3. 新增欄位
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/3e89702b-ee23-49e2-a8bb-153e98393f8e)
4. 新增 models Album
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/435c0264-2316-4b8a-a5df-84f55b9a4eb0)


### 部署
`python3 manage.py makemigrations`
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/9388cd85-9cd1-4490-9b1f-7cf7eaad004a)

`python3 manage.py migrate`
![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/452ddc1e-249a-4e8e-bdf2-c99f9d166a7d)


![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/70f919e9-5f52-4d32-a544-7b9ed1f9a034)


### 建立
- 新增相簿
  - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/990b1b75-784c-4984-9b73-b6a6bdde2c4a)
- 新增照片
  - ![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/17747020-4a3f-4607-81fc-87903ef31a2a)


