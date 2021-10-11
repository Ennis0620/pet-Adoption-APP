Android 寵物領養APP 
===


# Introduction
使用政府之流浪貓狗公開平台資料，透過Android Studio撰寫APP，讓使用者可以快速查詢所所想要領養的貓狗品種、樣貌、性別……，並可以快速撥打電話去收容所詢問。
# Detail
### 資料抓取&UI連結
使用AsyncTask的doInBackground處理抓取政府公開資料平台並解析json格式。

透過sharedpreference儲存所有抓取到的內容(離開APP後資料還會留存)。

建立另外一個doInBackground去下載動物照片。

用adapter將資料與自訂layout做連結(點選電話圖案可以撥打)。

</br>

### 條件查詢&收容所數量

使用Spinner做寵物的條件塞選。

用intent傳送塞選條件。

依據sharedpreference計算東北西南的收容所、待領養寵物數量。
### firebase
從AndroidStudio設定關鍵字搜尋資料連結至firebase。

# Demo
自繪layout，點選電話圖案可撥打

![](https://i.imgur.com/eHxJ6BG.png)

關鍵字搜尋、北中南東寵物收容所目前情況

![](https://i.imgur.com/GG12CYl.png)

連結至firebase

![](https://i.imgur.com/BBy70ih.png)




# Requirement
    java
    Android Studio
    firbase
# Package
    src
    │      ├─main
    │      │  │  AndroidManifest.xml
    │      │  │  
    │      │  ├─java
    │      │  │  └─com
    │      │  │      └─example
    │      │  │          └─pet_adoption
    │      │  │                  MainActivity.java   主頁面
    │      │  │                  MapMain.java        收容所地圖
    │      │  │                  Spinner_Main.java   條件塞選
    │      │  │                  splashscreen.java   載入動畫效果
    │      │  │                  
    │      │  └─res
    │      │      ├─drawable                         自繪素材
    │      │      │      
    │      │      │      
    │      │      ├─layout
    │      │      │      activity_main.xml           主頁面UI
    │      │      │      activity_map_main.xml       收容所地圖UI
    │      │      │      activity_spinner.xml        搜尋頁面UI
    │      │      │      activity_splashscreen.xml   載入動畫UI               
    │      │      │      my_layout.xml               下拉式itemList UI

# Problems
1.如何抓取網路資料

2.怎麼避免每次開起就要重新抓取公開資料

3.抓取網路圖片

# Solve

1.使用doInbackground的執行緒在背景跑

2.sharedpreference存取開載入時所抓取資料

3.改寫bitmap並另開doInbackground的執行緒抓取

