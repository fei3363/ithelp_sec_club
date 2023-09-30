## 社團可以嘗試的活動類型

## 閃電型活動：快閃、兩小時～三小時

1. 演講
  - 資安趨勢分享：討論目前的資安趨勢
  - 技術演講：資深資安工程師、專家利用 QA 回答問題
  - 經驗講座：邀請學長姐與業界的人來分享學習經驗
  - 一般社課：可以簡單帶實作讓學員體驗
2. 快閃
  - 下課在走廊快速宣傳一個活動、宣傳一個理念

### 集中型工作坊一天～兩天

1. 滲透測試工作坊坊：模擬真實的網路攻擊情境，學習如何發現和修復漏洞。
2. 資安資料分析挑戰賽：提供一組真實的資料，並挑戰在有限的時間內提供解決策略。

### 學期長計劃

1. 開源軟體貢獻計劃：選擇一個開源專案，學習並為其做出貢獻。
2. 深度學習研究小組：從基礎到實踐，進行深度學習的研究與應用。
3. 創業初創計劃：組隊，從點子到原型，最終可能有機會獲得真實的資金投資。
4. 技術部落格維護：鼓勵學生 regurlarly 發表技術文章，培養寫作和分享的習慣。
5. IoT 實驗室：探索物聯網技術，製作實用的智能設備的原型。

### 線上活動

1. 線上講座：邀請業界專家進行線上講座，可以吸引更廣泛的參與者。
2. 虛擬Hackathon：透過線上平台，組隊參加比賽。
3. 線上學習讀書會：針對特定主題進行深入學習和討論。

### 基於競賽的活動

1. 程式碼競賽：如 LeetCode 或 HackerRank 挑戰賽。
2. 安全Capture The Flag（CTF）比賽：參與者需找出藏起來的 Flag，通常涉及各種資訊安全技能。
3. 產品創新比賽：鼓勵創意思考，從點子到原型的創建。

### 休閒活動

1. 遊戲夜：組織成員一起玩桌遊或視頻遊戲，增強團隊凝聚力。
2. 電影夜：觀看與技術或科學相關的電影，之後進行討論。
3. 書籍俱樂部：選擇一本書進行集體閱讀，然後進行討論。

### 實地考察

1. 科技公司參訪：參觀當地的初創公司或大型科技公司，了解他們的運營方式。
2. 參加技術會議：作為團隊參加國內或國際的技術會議，擴展視野。
3. 參觀研究機構：瞭解前沿的研究和發展。


## 舉辦活動的優點
1. 提升知識能力
2. 提升團隊熟悉與活動
3. 增加實戰經驗
4. 增加人脈


## 舉辦的步驟

1. 確認活動主題與目的： 
- 資安社團可舉辦駭客松、網路安全演練或加密技術工作坊。
- 資訊社團可以選擇主題如：程式設計基礎、AI概論、Web開發等。

2. 選擇合適的日期與地點：
- 避免和其他大型學校活動撞期。
- 選擇交通便利、設備完善的場地。

3. 預算規劃：
- 預估場地、設備、食物和飲料等成本。
- 設定報名費用或尋求外部贊助以支援經費。

4. 推廣活動：
- 透過社群媒體、學校平台、寄信等方式廣發訊息。
- 設計吸引人的宣傳海報。

5. 準備物資：
- 確保場地有足夠的插座、投影機、麥克風等。
- 準備筆、筆記本、名牌等給參與者。

6. 活動當天：
- 早點到場做最後的確認和準備。
- 安排接待區以確認報名者身分。
- 在活動結束後，進行簡單的問卷調查，以收集回饋。

7. 組織團隊分工：
- 根據活動的規模和內容，明確劃分各個職責，如策劃、場地佈置、接待、技術支持等。
- 確保每位團隊成員都清楚自己的角色和職責。

8. 活動前的培訓：
- 若有特殊設備或軟體，提前為講師或使用者進行培訓，確保活動進行順暢。
- 針對志工或團隊成員進行簡單的服務態度和活動規範培訓。

9. 參與者互動：
- 利用破冰活動或團體遊戲促進參與者之間的互動。
- 提供平臺讓參與者分享自己的想法和經驗。

10. 跟進與改進：
- 除了問卷調查，還可以舉辦小型座談會，與參與者面對面交流。
- 根據回饋調整和優化未來的活動策劃。


## 社團系統：報名功能

### 新增 models

更新 models

```python
from django.db import models
from django.contrib.auth.models import User

class Event(models.Model):
    title = models.CharField(max_length=200)
    description = models.TextField()
    date = models.DateTimeField()
    venue = models.CharField(max_length=100)
    capacity = models.IntegerField()

    def __str__(self):
        return self.title

class Registration(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    event = models.ForeignKey(Event, on_delete=models.CASCADE)
    registration_date = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return f"{self.user.username} - {self.event.title}"
```

### 新增 views

在`event_registration/views.py`中
處理報名邏輯：

```python
from django.shortcuts import render, redirect
from .models import Event, Registration

def event_list(request):
    events = Event.objects.all()
    return render(request, 'event_list.html', {'events': events})

def register_event(request, event_id):
    if request.user.is_authenticated:
        event = Event.objects.get(pk=event_id)
        Registration.objects.create(user=request.user, event=event)
        return redirect('event_list')
    else:
        return redirect('login')
```

### 4. 新增 urls

在`event_registration/urls.py`中 定義URL

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.event_list, name='event_list'),
    path('register/<int:event_id>/', views.register_event, name='register_event'),
]
```



### 5. 新增 template

在`event_registration/templates`資料夾中，新增一個`event_list.html`

```html
{% for event in events %}
<h3>{{ event.title }}</h3>
<p>{{ event.description }}</p>
<a href="{% url 'register_event' event.id %}">Register</a>
{% endfor %}
```

### 6. 測試

資料庫更新
```bash
python manage.py makemigrations event_registration
python manage.py migrate
```

執行

```bash
python manage.py runserver
```
