# DAY 9 - 資安社團與資訊社團攻略：組織有效的社團會議 & 社團系統：會議紀錄功能 


## 如何組織有效的社團會議

社團要順利運作，一場有組織的會議絕對不可少。要開得好，得注意幾個關鍵步驟：

### 1. 明確會議目的
每次開會，首先要確定的就是：這場會議要達到什麼目的？是要討論活動計劃，還是要解決某個突發問題？

### 2. 事前派發議程
讓大家提前知道這次會議要聊什麼，也能提前做點準備，這樣會議時才不會手忙腳亂。

### 3. 掌握會議時間
長篇大論不是好事，確保會議能夠在預定的時間內結束，這樣大家才會更願意參與。

### 4. 鼓勵成員參與討論
每個人都是社團的一份子，他們的意見和建議都很重要，所以要確保每位成員都有發言的機會。



## 會議的前中後，都得做些什麼？

### 會前：
- 確認主題：不只是目的，還要知道會議要達成的具體行動。
- 準備資料：相關的文件、資料，或是過去的紀錄，都得事先準備好。
- 確認參與者：看看是不是每個該來的人都知道，而且時間都沒問題。

### 會中：
- 選一位主持人：他的任務是確保會議進行順利，並按照議程來。
- 重點記錄：討論的內容、決定的事情都得記錄下來。
- 注意時間：別跑偏太遠，也要確保每個議題都能夠被討論到。

### 會後：
- 整理會議紀錄：這是給未來參考，或是給缺席的成員看的。
- 分派工作：確定誰要做什麼，並確認他們都知道自己的任務。
- 定期追踪：看看大家的進度如何，需要協助的地方要提前知道。
- 詢問反饋：找出這次會議的好與壞，下次就能做得更好。


## 社團系統：會議紀錄功能

1. 使用 Django 開發會議紀錄功能

### Models

首先，我們需要定義一個 `Meeting` 的 model：

```python
from django.db import models

class Meeting(models.Model):
    title = models.CharField(max_length=200)
    date = models.DateField()
    notes = models.TextField()

    def __str__(self):
        return self.title
```

### Views

建立一個 view 來顯示所有的會議：

```python
from django.shortcuts import render
from .models import Meeting

def list_meetings(request):
    meetings = Meeting.objects.all()
    return render(request, 'meetings/list.html', {'meetings': meetings})
```

### Templates

在 `meetings/list.html`，我們可以列出所有的會議:

```html
{% extends "base.html" %}

{% block content %}
    <h2>會議紀錄</h2>
    <ul>
    {% for meeting in meetings %}
        <li>{{ meeting.date }} - {{ meeting.title }}</li>
    {% endfor %}
    </ul>
{% endblock %}
```

完成上述步驟後，有了一個簡單的會議紀錄功能，可以用來記錄和查看社團的所有會議。
