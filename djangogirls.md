| Post |
|--------|
| title |
| text |
| author |
| created_date |
| published_date|

'''
python manage.py startapp blog
'''

'''
from django.conf import settings
from django.db import models
from django.utils import timezone

"""
class Post(models.Model): – この行が今回のモデルを定義します (これが オブジェクト です)。

classはオブジェクトを定義してますよ、ということを示すキーワードです。
Post はモデルの名前で、他の名前をつけることもできます（が、特殊文字と空白は避けなければいけません）。モデルの名前は大文字で始めます。
models.Model はポストがDjango Modelだという意味で、Djangoが、これはデータベースに保存すべきものだと分かるようにしています。
"""
class Post(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(default=timezone.now)
    published_date = models.DateTimeField(blank=True, null=True)
    
    def publish(self):
        self.published_date = timezone.now()
        self.save()
        
    def __str__(self):
        return self.title

'''

totang8m@gmail.com
djangomatozaki