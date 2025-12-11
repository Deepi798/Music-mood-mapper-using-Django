# Music-mood-mapper-using-Django

# 🎵 MusicMood Mapper

A simple Django web application that detects **Happy** or **Sad** mood from the text you type and plays the correct Spotify playlist.

---

## 📌 Overview

MusicMood Mapper analyzes the text entered by a user (like *“I feel very happy today”*) and identifies whether the mood is:

* **Happy**
* **Sad**
* **Neutral** (if no keywords match)

Based on the detected mood, it displays an embedded **Spotify playlist**.

---

## 🌟 Features

* Detects mood from user input text
* Supports **Happy**, **Sad**, and **Neutral (default)**
* Shows Spotify playlist for each mood
* Django-based clean webpage
* Easy to customize mood keywords or playlist URLs

---

## 😀 Supported Moods

| Mood        | Keywords Detected     | Playlist Returned      |
| ----------- | --------------------- | ---------------------- |
| **Happy**   | happy, joy, excited   | Happy Hits Playlist    |
| **Sad**     | sad, cry, heartbroken | Sad/Emotional Playlist |
| **Neutral** | anything else         | Neutral Happy Hits     |

---

## 🧠 Mood Detection Flow

1. User enters text in the text field
2. Django checks for keywords in the text
3. Mood is identified
4. Matching Spotify playlist is shown via iframe

---

## 🎧 Spotify Playlists Used

### **Happy Songs Playlist**

```
https://open.spotify.com/embed/playlist/37i9dQZF1DXdPec7aLTmlC
```

### **Sad Songs Playlist**

```
https://open.spotify.com/embed/playlist/37i9dQZF1DWVV27DiNWxkR
```

### **Neutral (Default) Playlist**

```
https://open.spotify.com/embed/playlist/37i9dQZF1DX7KNKjOK0o75
```

---

## 🛠️ Technologies Used

* **Python 3.x**
* **Django**
* **HTML & CSS**
* **Spotify Embed Player**

---

## 📁 Project Structure

```
MusicMoodMapper/
│── mood/
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── templates/mood/home.html
│   ├── spotify_utils.py
│── musicmood/
│   ├── settings.py
│   ├── urls.py
│── manage.py
```

```
http://127.0.0.1:8000/



