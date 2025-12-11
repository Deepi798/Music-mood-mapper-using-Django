**#models.py**

&nbsp;

from django.db import models



class MoodEntry(models.Model):

&nbsp;   text = models.TextField(blank=True, null=True)

&nbsp;   mood = models.CharField(max\_length=50)

&nbsp;   created\_at = models.DateTimeField(auto\_now\_add=True)





**# mood/views.py**



from django.shortcuts import render

from textblob import TextBlob

from .spotify\_utils import get\_song\_link\_by\_mood



def mood\_home(request):

&nbsp;   mood\_result = ""

&nbsp;   song\_recommendation = ""

&nbsp;   song\_link = ""



&nbsp;   if request.method == "POST":

&nbsp;       text = request.POST.get("text", "")

&nbsp;       text\_lower = text.lower()



&nbsp;       if any(word in text\_lower for word in \["love", "romance", "heart", "crush"]):

&nbsp;           mood\_result = "Love"

&nbsp;       elif any(word in text\_lower for word in \["breakup", "sad", "cry"]):

&nbsp;           mood\_result = "Breakup"

&nbsp;       elif any(word in text\_lower for word in \["melody", "calm", "peace", "soft"]):

&nbsp;           mood\_result = "Melody"

&nbsp;       elif any(word in text\_lower for word in \["family", "amma", "appa"]):

&nbsp;           mood\_result = "Family"

&nbsp;       elif any(word in text\_lower for word in \["friend", "bro", "bestie"]):

&nbsp;           mood\_result = "Friendship"

&nbsp;       elif any(word in text\_lower for word in \["vibe", "dance", "party"]):

&nbsp;           mood\_result = "Vibe"

&nbsp;       elif any(word in text\_lower for word in \["mass", "item", "beat"]):

&nbsp;           mood\_result = "Item"

&nbsp;       else:

&nbsp;           mood\_result = "Neutral"



&nbsp;       # Get Spotify embed playlist URL

&nbsp;       song\_link = get\_song\_link\_by\_mood(mood\_result)

&nbsp;       song\_recommendation = f"Play {mood\_result} Playlist on Spotify 🎧"



&nbsp;   return render(request, 'mood/home.html', {

&nbsp;       'mood': mood\_result,

&nbsp;       'song': song\_recommendation,

&nbsp;       'song\_link': song\_link

&nbsp;   })

**#mood\\urls.py**



from django.urls import path

from . import views



urlpatterns = \[

&nbsp;   path('', views.mood\_home, name='mood\_home'),  # home page

]



**#settings.py**



INSTALLED\_APPS = \[

&nbsp;   'django.contrib.admin',

&nbsp;   'django.contrib.auth',

&nbsp;   'django.contrib.contenttypes',

&nbsp;   'django.contrib.sessions',

&nbsp;   'django.contrib.messages',

&nbsp;   'django.contrib.staticfiles',

&nbsp;   'mood',

]



**#musicmood\\urls.py**



from django.contrib import admin

from django.urls import path, include



urlpatterns = \[

&nbsp;   path('admin/', admin.site.urls),

&nbsp;   path('', include('mood.urls')),  # connect app URLs

]





