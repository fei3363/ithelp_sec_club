# DAY 10 - 資安與資訊社團攻略：資安實戰 & 社團系統開發：最近活動功能


## 前言
在資安領域中，實戰經驗是最好的學習方法。

「你可能此時此刻迷惘自己還沒有進步，但你可先開始行動。」
​
▋ 關於魚的故事
​
以前在社團的時候，學長跟我分享了「給他魚吃，不如教他釣魚！」
來自於《老子》「授人以魚不如授人以漁」，
雖然後來看到一系列討論魚跟魚桿的問題[1]（不過那是後話了）
Ref: [1] 翟本喬：給魚？給釣竿？都錯了！
https://www.gvm.com.tw/article/53305


​
▋ 如何在資訊/資安進步
​
「實作最快。」
在我自己學習路上，最有印象的經驗：
​
大概大學時用一個月從需求到開發一個網站出來。
​
壓力很大，但學得非常快。
但建議大家做好自己的時間管理和壓力管理。

​
▋ 網路該怎麼學
​
一直以來我對網路也不是非常了解，
沒有自己的機房，對路由器也沒有太大的喜好。
​
但突然看到學弟寫的這篇鐵人賽[2]，也印證了「實作最快」的這件事。

[2] 誒，想不到有一天搞懂網路是因為宿舍學長逼我的QQ！30天的宿舍網路架設
https://ithelp.ithome.com.tw/users/20132118/ironman/6872
​
如果你想在宿舍搞網路可以參考這系列的鐵人賽，但如果你想看學弟吐槽學長也是可以看這系列的。

## 資安實戰
資安的學習不應只停留在理論，更要透過實戰來學習。

### 實戰列表

1. 模擬真實環境攻擊：模擬真實世界的網站、應用或系統，並要求社員試圖找出和利用其漏洞。
2. 逆向工程：提供一些惡意軟體，讓社員試圖理解其運作原理並找出其弱點。
3. 網頁滲透測試：網站漏洞，如 SQL注入、XSS、CSRF等。
4. 無線網路測試：無線網路的安全，例如 Wi-Fi 密碼破解、中間人攻擊等。


### 實體挑戰

- 硬體攻防：學習如何對物聯網裝置、無線設備等進行安全分析和攻擊。
  - 鎖的挑戰：學習傳統的鎖和現代電子鎖的鎖具技術，試圖不破壞的情況下開鎖。
  - RFID 技術分析：透過硬體和軟體工具學習 RFID 卡片的弱點和如何複製。
- 密室脫逃：設計一間資安主題的逃脫房間，讓成員在限定時間內解開謎題，體驗真實的駭客場景。
  - 資安密室脫逃 https://hitcon.org/hackdoor/
 
### 線上挑戰

- CTF競賽：在模擬的環境中，進行 Capture The Flag 比賽，挑戰各種資安問題。
- 模擬駭客攻擊：在虛擬環境中模擬真實的駭客攻擊，學習防禦技巧。


### 舉例與分析
1. 基礎的網路概念與工具使用
   - 如何實戰：利用工具如ping、traceroute、Wireshark來學習基本的網路概念。
   - 可以學到什麼：了解網路的基本工作方式、協議和流量分析。
   - 為什麼要學：網路是資安的基石，了解其運作原理有助於後續的資安學習。

2. 簡單的密碼破解
   - 如何實戰：使用攻擊工具
		- 如 John the Ripper 或 Hashcat 
		- 目標：破解常見密碼雜湊值
		- 使用 cmd5 破解密碼網站
   - 可以學到什麼：學習不同的密碼原理與儲存方法、hash 演算法和駭客如何破解。
   - 為什麼要學：常見密碼弱點，跟大家分享強密碼的重要性。

3. 基礎的 Web 安全
   - 如何實戰：透過 WebGoat 或 DVWA 這類的模擬網站來學習。
   - 可以學到什麼：知道 SQL 注入原理、跨站腳本攻擊。
   - 為什麼要學：因為網站比較好入門，雖然中間會有門檻。

4. 社交工程基礎
   - 如何實戰：模擬一些簡單的釣魚攻擊或其他社交工程攻擊。
   - 可以學到什麼：了解人類心理的弱點，學習如何防範這些攻擊。
   - 為什麼要學：技術攻擊常常起始於成功的社交工程，了解其策略能提高防禦能力。

5. 系統設定與安全習慣
   - 如何實戰：建立一個簡單的服務，如 Web 伺服器，然後學習如何正確地設定和保護它。
   - 可以學到什麼：了解正確的安全設定、更新和修補程式。
   - 為什麼要學：許多攻擊來源於不當的設定，正確的設定可以大幅提高安全性。




## 社團系統：活動與最近活動

### 功能


1. 新增活動
   - 標題
   - 日期和時間
   - 地點
   - 活動說明
   - 活動類型 (例如: 工作坊、演講、社交活動等)


2. 查看活動
   - 顯示所有活動資訊
   - 最近的活動

---

### 資料庫設計

1. 活動表格：
   - 活動ID (主鍵)
   - 標題
   - 日期和時間
   - 地點
   - 描述
   - 活動類型
   - 新增者ID (外鍵)


---

### 實作


1. 模型設計（models.py）

```python
from django.db import models
from django.contrib.auth.models import User

class Event(models.Model):
    title = models.CharField(max_length=200)
    date_time = models.DateTimeField()
    location = models.CharField(max_length=200)
    description = models.TextField()
    event_type = models.CharField(max_length=50)
    created_by = models.ForeignKey(User, on_delete=models.CASCADE)

```

2. URL 設計（urls.py）

```python
from django.urls import path
from . import views

urlpatterns = [
    path('events/', views.event_list, name='event_list'),
    path('events/<int:event_id>/', views.event_detail, name='event_detail'),
    path('upcoming/', views.upcoming_events, name='upcoming_events'),
]
```

3.views.py

```python
from django.shortcuts import render, redirect
from .models import Event
from datetime import datetime

def event_list(request):
    events = Event.objects.all()
    return render(request, 'event_list.html', {'events': events})

def event_detail(request, event_id):
    event = Event.objects.get(pk=event_id)
    return render(request, 'event_detail.html', {'event': event})

def upcoming_events(request):
    now = datetime.now()
    events = Event.objects.filter(date_time__gt=now).order_by('date_time')
    return render(request, 'upcoming_event_list.html', {'events': events})

```

4. 模板（templates）

1. 新增 `base.html`（之前已經有範例）

2. 新增 `event_list.html` 和 `event_detail.html` 活動列表

在 `templates` 目錄下，新增 `base.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>社團活動日曆</title>
</head>
<body>
    <header>
        <h1>社團活動日曆</h1>
    </header>
    <main>
        {% block content %}
        {% endblock %}
    </main>
</body>
</html>
```

新增 `event_list.html`:

```html
{% extends 'base.html' %}

{% block content %}
    <h2>即將到來的活動</h2>
    <ul>
    {% for event in events %}
        <li>
            <a href="{% url 'event_detail' event.id %}">{{ event.title }} - {{ event.date_time|date:"Y-m-d H:i" }}</a>
        </li>
    {% endfor %}
    </ul>
{% endblock %}
```

新增 `event_detail.html`:

```html
{% extends 'base.html' %}

{% block content %}
    <h2>{{ event.title }}</h2>
    <p>日期時間: {{ event.date_time|date:"Y-m-d H:i" }}</p>
    <p>地點: {{ event.location }}</p>
    <p>說明: {{ event.description }}</p>
    <p>活動類型: {{ event.event_type }}</p>
    <p>由 {{ event.created_by.username }} 建立</p>
    
{% endblock %}
```


新增 `upcoming_event_list.html`
```
{% extends 'base.html' %}

{% block content %}
    <h2>即將到來的活動</h2>
    <ul>
    {% for event in events %}
        <li>
            <a href="{% url 'event_detail' event.id %}">{{ event.title }} - {{ event.date_time|date:"Y-m-d H:i" }}</a>
        </li>
    {% endfor %}
    </ul>
{% endblock %}
```

5. 設定和啟用

APP 加入到 `INSTALLED_APPS` 裡：

```python
INSTALLED_APPS = [
    ...
    '你的 APP 名稱',
    ...
]
```

執行變更到資料庫的指令

```bash
python manage.py makemigrations
python manage.py migrate
```
