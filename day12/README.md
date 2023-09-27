# DAY 12 資安社團與資訊社團攻略：如何建立合作 & 社團系統：合作伙伴管理功能

## 什麼是合作

合作指的是兩個或多個社團為了達到共同的目的或目標，互相協助。
包含知識分享、技術交流、資源整合或共同開發專案等。

## 為什麼需要合作

1. 資源共享：很多社團資源有限，可以透過合作整合資源，讓經營事半功倍。
2. 知識互補：互補短處，一起成長。
3. 提高影響力：合作可以增加影響力，使得合作項目更具吸引力和說服力。
4. 拓展網路：合作可以擴大社團的影響範圍，有機會獲得更多的機會和資源。

## 什麼需要合作

1. 新成立的社團：可能想要快速成長和積累經驗，以尋找合作夥伴了解內容。
2. 索取專業知識的社團：例如，資安社團在物聯網領域缺乏經驗，可以考慮與相關領域的社團或企業合作。
3. 想要擴大影響力的社團：透過合作舉辦大型活動或競賽，可以吸引更多參與者和注意力。


## 合作的步驟

### 確定目標

在考慮合作之前，必須清晰定義期望從中獲得的利益，
以及思考可以為合作夥伴提供的價值。

舉個例子
假設社團希望舉辦一場大型的資訊安全研討會，但缺乏足夠的資金和場地。
主要目標可能是找到能夠提供場地或贊助資金的合作夥伴。
而社團可以提供工作人員與協助宣傳合作夥伴。

### 尋找潛在夥伴

基於確定的目標，
開始研究和篩選可能可以的合作夥伴。

舉個例子
資安社團可能會考慮與
1. 學校
2. 資工系/資管系/任何系
3. 系學會
4. 學校其他社團
5. 別間學校
6. 科技公司
7. 其他資訊相關的企業

### 初步接觸
當找到潛在的合作夥伴後，聯絡對方，提供希望合作什麼、怎麼合作。
建議撰寫一份完成的「合作/活動企劃書」

可以發一封正式的合作邀請信給科技公司，
提供研討會的概述、預期的參與者數量以及希望得到的支援。


### 明確合作細節
與夥伴達成初步共識後，
可以討論合作的細節，
比較嚴謹的話可簽合作合約。

合作合約可以列出，本次合作的內容，
雙方負責、活動的日期、場地提供情況、資金支援金額等。

### 執行和監控
合作開始後，需密切監控進度，以確保達到訂定的目標。

可以學習**專案管理**以及 PM 等技術，
籌備過程當中定期檢查活動的籌備進度、預算使用情況，
並與合作夥伴的代表保持聯絡，報告進度。

### 評估和調整：
在合作的某個階段或結束後，
雙方可以評估合作成果，
並根據實際情況調整後續的策略或行動。

比如研討會結束後，
資安社團和科技公司可能會舉行一次評估會議，
討論活動的成功之處、需要改進的地方，
以及是否有機會進行未來的合作。


## 合作需要注意什麼
1. 明確溝通：確保所有合作方都清楚自己的期望與合作方式。
2. 相互尊重：尊重合作夥伴的意見和決策，避免不必要的爭執。
3. 持續交流：定期與合作夥伴交流，確保合作進行順暢。
4. 定期評估：不要等到合作結束才進行評估，定期檢查和調整可以讓合作更為成功。
5. 面對困難：合作中可能會遇到問題或分歧，應該及時解決，避免影響合作的進行和結果。


## 社團系統：合作伙伴管理功能
### 1. 建立新的 app

在專案的根目錄下執行以下指令來建立新的 app：

```bash
python manage.py startapp partners
```



### 2. 定義模型（models.py）

在 `partners/models.py` 檔案中定義合作伙伴的資料模型：



```python

from django.db import models



class Partner(models.Model):

    name = models.CharField(max_length=255)
    description = models.TextField(blank=True)
    contact_email = models.EmailField()
    website = models.URLField(blank=True)
    logo = models.ImageField(upload_to='partners/logos/', blank=True)

    def __str__(self):
        return self.name

```



### 3. 建立表單（forms.py）



在 `partners` 資料夾中建立一個新的檔案 `forms.py`：



```python

from django import forms
from .models import Partner

class PartnerForm(forms.ModelForm):
    class Meta:
        model = Partner
        fields = ['name', 'description', 'contact_email', 'website', 'logo']

```



### 4. 建立檢視（views.py）



在 `partners/views.py` 檔案中加入以下檢視：



```python

from django.shortcuts import render, redirect
from .forms import PartnerForm


# 合作夥伴列表
def partner_list(request):
    partners = Partner.objects.all()
    return render(request, 'partners/partner_list.html', {'partners': partners})

# 新增合作夥伴
def partner_add(request):
    if request.method == 'POST':
        form = PartnerForm(request.POST, request.FILES)
        if form.is_valid():
            form.save()
            return redirect('partner_list')
    else:
        form = PartnerForm()
    return render(request, 'partners/partner_add.html', {'form': form})

```



### 5. 建立 templates
在 `partners` 資料夾中建立一個名為 `templates` 的資料夾，再建立一個 `partners` 子資料夾。接著，建立以下兩個 HTML 檔案：

- `partner_list.html`
- `partner_add.html`


#### 1. `partner_list.html`



顯示所有合作夥伴的清單。



```html

{% extends 'base.html' %}



{% block content %}

    <h2> 合作夥伴清單 </h2>

    <ul>

    {% for partner in partners %}

        <li>

            <h3>{{ partner.name }}</h3>

            <p>{{ partner.description }}</p>

            <a href="{{ partner.website}}"> 網站連結 </a>

        </li>

    {% endfor %}

    </ul>

    <a href="{% url 'partner_add' %}"> 新增新的合作夥伴 </a>

{% endblock %}

```



#### 2. `partner_add.html`


使用者輸入合作夥伴的資訊並新增到資料庫。



```html

{% extends 'base.html' %}



{% block content %}

    <h2> 新增新的合作夥伴 </h2>

    <form method="post" enctype="multipart/form-data">

        {% csrf_token %}

        {{ form.as_p }}

        <button type="submit"> 儲存 </button>

    </form>

    <a href="{% url 'partner_list' %}"> 查看合作夥伴清單 </a>

{% endblock %}

```





### 6. 定義 URL 路徑（urls.py）



在 `partners` 資料夾中建立 `urls.py`：

```python

from django.urls import path
from . import views

urlpatterns = [
    path('partners/', views.partner_list, name='partner_list'),
    path('partners/add/', views.partner_add, name='partner_add'),

]

```



### 7. 最後測試

1. 在 `INSTALLED_APPS` 中加入 `partners`。
2. 使用 `python manage.py makemigrations partners` 和 `python manage.py migrate` 更新資料庫。
3. 啟動伺服器並測試新功能。
