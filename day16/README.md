# DAY 16 資安社團與資訊社團攻略：CTF 學習策略 & 社團系統：Write up 管理工具

## 前言
很多人常常會詢問一定學 CTF 嗎？或是社團的課程一定要安排 CTF 嗎？
我的答案是不一定，因為 CTF（Capture The Flag）雖然是資安領域的一個重要競賽，能鍛鍊資安相關技能和增加團隊協作的技巧，但每個社團或每一個人目標可能有所不同。

比如我在台科大資安研究社擔任社長的時候，評估下來之後以「業界需要的資訊安全」為主題，因此反而 CTF 的課程就比較少。

## 什麼是 CTF

CTF，全名為 Capture The Flag，代表「抓取 Flag」。一種資安競賽，參賽者必須解決出題者出的各種資安、漏洞、甚至是特別難的問題，解答之後會拿到「Flag」，進而取得分數。

CTF 通常分為三大類型：

1. Jeopardy-style CTF：參賽者選擇不同類型和難度的題目來解答，例如 Web 安全、密碼學、數位鑑識、逆向工程、Pwnable 。
2. Attack-defense style CTF：每個隊伍有自己的伺服器和服務，必須同時進行攻擊其他隊伍和防禦自己的伺服器。
3. King of the Hill：參賽者必須在限定時間內，佔領伺服器。誰在結束時控佔領這個伺服器越久，誰就是 King！

白話文版本
1. Jeopardy-style CTF：就像遊戲中選關卡那樣，參賽者可以自由選擇他們想挑戰的問題，有的問題可能跟網站有關，有的可能是解碼，或者是找電腦上的秘密。
  - 比較是百萬小學堂、百萬富翁的那種遊戲可以選題目（但在時間內都可以重複挑戰）
2. Attack-defense style CTF：想像一下，每個隊伍都有自己的「城堡」，要保護自己的城堡不被其他隊伍攻破，同時還要試著去攻打其他人的城堡。
3. King of the Hill：玩搶地盤的遊戲，大家都想控制一個地方，誰能夠在遊戲結束前佔領那個地方最久，誰就是亡者！

## WarGame

除了 CTF 之外，還有 WarGame 也可以練習資安相關技能

WarGame 這個玩法可以想像成一系列的電腦遊戲闖關模式。

就像你玩一些手機遊戲，每過一關都會更難，每一關都設有不同的挑戰和障礙需要繞過。

在 WarGame 中，這些「關卡」其實是各種資訊安全的問題和挑戰。

跟 CTF 不同的是，WarGame 更像是單人遊戲，讓你自己在解題的過程中學習和進步。

你不需要在短時間內與其他人競爭，而是可以慢慢地、在自己的節奏下解題。

所以 WarGame 特別適合初學者或是那些想深入研究某一特定技能的人。

有一個蠻受歡迎的 WarGame 網站叫做「overthewire」，裡面有很多系列的闖關遊戲，適合從新手到高手的人挑戰。

![image](https://github.com/fei3363/ithelp_sec_club/assets/82772249/db89cbdb-f981-4fee-b7b7-11e27e51b8aa)


### CTF vs WarGame

如果你想在一個較有競爭性的環境中測試自己的技能，可以參加 CTF。

但如果你希望更專注於學習，並在自己的節奏下逐步提升，那麼 WarGame 是個很好的選擇！

### CTF 類型

1. Web 網站：
   - 這個類型的題目跟網站有關。想像你在網上購物或上社交媒體時，有些網站可能有漏洞。這種題目要求你找出那些網站的安全漏洞，就像你找尋隱藏的寶藏一樣。

2. Pwnable 漏洞分析：
   - 這個是比較進階的，跟軟體的漏洞有關。有些程式或應用程式可能被寫得不太安全，容易被攻擊。這些題目會讓你像個偵探一樣，找出這些程式的弱點。

3. Reverse 逆向工程：
   - 你可以想像「逆向工程」就像是拆解一個機器玩具，然後嘗試理解它是怎麼運作的。在這種題目中，你會得到一些程式或軟體，然後嘗試找出它的運作原理或秘密。

4. Crypto 加解密：
   - 這是跟密碼學有關的題目。你知道當你在網上購物時，你的信用卡資料是如何被加密的嗎？這種題目讓你像個神秘的魔法師一樣，解開或製造那些加密的謎語。

5. Forensics 鑑識：
   - 這個類型的題目就像電視劇中的犯罪現場調查。有時候，電腦或手機中的資料會被刪除或隱藏，這些題目要求你像一名偵探，從這些機器中找回並分析那些資料。

## 過去 V.s. 現代的 CTF

過去和現在的 CTF 題目在許多方面都有所不同，主要的差異和發展趨勢：

### 過去的 CT

1. 基本的漏洞利用：早期的 CTF 挑戰經常涉及經典的漏洞利用技術，如緩衝區溢出和格式化字串漏洞。
2. 簡單的 Web 漏洞：這包括 SQL 註入、跨站腳本（XSS）和跨站請求偽造（CSRF）等基礎漏洞。
3. 密碼學的基礎：如簡單的替換加密和經典的密碼學挑戰。
4. 基於網路的挑戰：例如網路嗅探、流量分析等。
5. 基礎的系統鑑識：如日誌分析和基本的檔案恢復。

### 現在的 CTF

1. 現代 Web 技術：最新的 Web 框架和技術的安全性，例如 GraphQL、Websockets 和最新的身份驗證機制等。
2. 先進的二進制利用：除了基本的緩衝區溢出外，還包括更先進的保護技術繞過，如 ROP、Heap Spray和 Race Condition　等。
3. 雲和容器安全：雲端設定的錯誤、容器逃逸和相關的安全問題。
4. 物聯網（IoT）和移動安全：物聯網設備、家用電器和移動應用程式的漏洞。
5. 進階密碼學挑戰：現代的加密演演算法和協定，如後量子密碼學、零知識證明等。
6. 更真實的場景模擬：比如模擬真實的企業環境、工業控制系統等。
7. OSINT 和社交工程：使用公開信息和社交工程技巧進行資料收集和分析。

現代的 CTF 更加複雜和多樣，反映了目前安全領域的發展趨勢和威脅模型的變化。
過去的 CTF 則更多地聚焦於基礎和經典的安全概念和技術。

### CTFtime
- [CTFtime](https://ctftime.org/) 
  - 查看快發生和最近完成的 Capture The Flag (CTF) 賽事
  - 各種 CTF 賽事的日曆，並允許團隊註冊、提交分數、查看排名等

1. 查看最近的和即將到來的賽事：可以一起計畫和準備未來的賽事。
2. 查看團隊排名：這提供全球的 CTF 團隊排名，可以參考他們在各種賽事中的表現。
3. 查看賽事 Write-ups：許多參賽者和團隊在賽後會分享他們的解題策略和技術。這些 Write-ups 可以提供學習和研究的資源。
4. 討論和互動：網站還提供了一個討論區，供參賽者和團隊間互相交流。


### CTF WriteUp
打完 CTF 比賽可以在自己的部落格或 GitHub 寫下自己的解題思路
通常大家只會寫自己解出來的

#### 提升能力的方法
1. 找別人的 WriteUp
(1) 看自己有解出來的：有沒有不同思路，比對並學習不同的解法。
(2) 看自己沒解出來的：自己卡在哪裡
最後重新嘗試解題，補充於自己的 WriteUp 加強記憶。

### 打 CTF 一直卡住怎麼辦


1. 有比賽就打，持續進行 CTF 比賽
優點：一直有最新版的題目，可以增加自己的見聞
缺點：比賽結果很容易讓新手受挫和等不到適合的題目

2. 看考古題
優點：通常有別人的解題可以偷看，打不出來偷看小抄（Write UP）覺得簡單
缺點：沒有做筆記，或是造著打很容易忘記

※ 提升能力的方法：照著小抄試打，隔一週再打一次，看自己卡在那裡，是哪一個步驟自己忘記還是根本不會


4. 看前人的筆記去延伸
可以 Google：CTF Cheatsheet
優點：善用前輩的智慧，已經整理好的筆記或是技巧
缺點：單看的話很容易忘記


※ 提升能力的方法：
（1）單看筆記：了解原來這種程式語言有這種特性、弱點原理是什麼
（2）反向學習：從筆記找題目，從筆記中找到關鍵字+上 CTF 進行搜尋，從搜尋過程中去找題目來看，嘗試去解題，最後寫成自己的筆記。


5. 架設 CTF 題目
（1）自己創題：思考出給誰，希望考什麼點，從他人解題學習其他思路
（2）復刻題目：從別人的 github 或 Writeup 中 找到題目或題型，嘗試架設起來打打看，你會遇到架設不起來、架了打不穿，可能是環境、版本的問題，學習排查問題。

## 學習資源

從零開始學習資安的專業知識，需要有一定的基礎和大量的實際操作經驗。
網路上有許多優質的資源可以學習和練習。

### CTF（Capture The Flag）比賽學習

1. **PicoCTF by CMU**：由卡內基梅隆大學提供，適合初學者入門。
   - [PicoCTF](https://picoctf.org/)

2. **Hacker101 CTF by HackerOne**：由知名的資安公司 HackerOne 提供，包含多種安全挑戰。
   - [Hacker101](https://www.hacker101.com/)

3. **Hackme CTF by inndy**：由 inndy 提供，涵蓋多種資安挑戰。
   - [Hackme CTF](https://ctf.hackme.quest/)

### 特定領域的挑戰

如逆向工程和系統漏洞。

1. **逆向工程 Crackmes.one by sar**：提供了一系列軟體逆向工程的挑戰。
   - [Crackmes.one](https://crackmes.one/)

2. **Pwnable pwn.college**：重點在於系統安全和漏洞利用。
   - [pwn.college](https://pwn.college/)

### 臺灣資安相關課程


- **Awesome-Taiwan-Security-Course**：提供了一個臺灣各大學開設的資安相關課程清單。
   - [Github連結](https://github.com/fei3363/Awesome-Taiwan-Security-Course)

  - **臺灣大學**：計算機安全
  - **臺灣科技大學**：資訊安全實務
  - **交通大學**：程式安全

### 開始之前的建議：
在深入學習之前，建議先了解基礎網路和系統知識，如TCP/IP、作業系統原理等。
此外，程式設計知識也是不可或缺的，特別是 C 語言和 Python，
因為在資安領域中經常被使用。

最後，學習資安需要堅持和實踐，不斷的挑戰和學習才能不斷進步。


## 社團系統：Write up 管理工具

為了更有效地管理和分享 CTF 的 Write up，社團可以使用 Write up 管理工具：

1. 雲端儲存：使用如 Google Drive、Dropbox 等工具，儲存和分享 Write up。
2. 版本控制：使用 Git 或其他版本控制工具，追踪 Write up 的修改和更新。
3. 統一格式：設定統一的 Write up 模板，讓所有成員的格式保持一致。
4. 互相討論：設立討論機制，讓成員之間可以對 Write up 提供回饋和建議。
5. 公開分享：將品質高的 Write up 發布到社團的官方網站或社群媒體，提升社團的知名度和影響力。


### 1. 新增 app

新的 app 名為 `writeups`：

```bash
python manage.py startapp writeups
```

### 2. 新增 models

在 `writeups/models.py` 中，定義模型。

```python
from django.db import models
from django.contrib.auth.models import User

class WriteUp(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    author = models.ForeignKey(User, on_delete=models.CASCADE)
    event_date = models.DateField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

```

確保已經在 `settings.py` 的 `INSTALLED_APPS` 中加入 `writeups`


### 3. 新增 views

在 `writeups/views.py` 中，建立所需的 views。

```python
from django.shortcuts import render
from .models import WriteUp

def writeup_list(request):
    writeups = WriteUp.objects.all()
    return render(request, 'writeups/list.html', {'writeups': writeups})
```

### 4. 新增 template

在 `writeups/templates/writeups` 資料夾中，建立你的 templates。

```
{% extends "base.html" %}

{% block title %}Write-up 列表{% endblock %}

{% block content %}
    <h1>Write-up 列表</h1>
    <ul>
        {% for writeup in writeups %}
            <li>
                <h2>{{ writeup.title }}</h2>
                <p>作者：{{ writeup.author }}</p>
                <p>活動日期：{{ writeup.event_date }}</p>
                <p>更新時間：{{ writeup.updated_at }}</p>
                <div>{{ writeup.content }}</div>
            </li>
        {% empty %}
            <li>目前沒有任何 write-up。</li>
        {% endfor %}
    </ul>
{% endblock %}

```


### 5. 新增 urls

在 `writeups` 資料夾中建立一個 `urls.py`，然後定義 URL patterns。

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.writeup_list, name='writeup_list'),
]
```

確保你在 project 的 `urls.py` 中加入了這個 app 的 urls。

```python
from django.urls import include, path

urlpatterns = [
    path('writeups/', include('writeups.urls')),
]
```

### 6. 測試

```bash
python manage.py makemigrations writeups
python manage.py migrate
```


測試伺服器：

```bash
python manage.py runserver
```

打開瀏覽器，查看 `http://localhost:8000/writeups/` 
查看 Write up 列表
