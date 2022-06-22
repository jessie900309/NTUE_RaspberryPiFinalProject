# NTUE_RaspberryPiFinalProject

###### tags: `NTUE_SchoolNote`

#### 國立台北教育大學 110學年度 嵌入式系統 期末專題

:::spoiler Contents
[TOC]
:::



---

## 小組成員

[佩瑩](https://github.com/winnielin17) & [妤婕](https://github.com/jessie900309)



---

## Medicine Control System專題目的

<img width="500px" src="https://i.imgur.com/EF0hJdS.jpg" />

因應近年來的肺炎風波，醫藥問題也隨之受到重視，Medicine Control System提供一個可以遠距監控存藥倉庫的方法，讓員工可以利用IOT概念實現人與藥物零接觸的工作環境。

如圖所示，Medicine Control System主要分為兩個部分，分別是Server端的【存藥倉庫】，和Client端的【遠端辦公室】。

Server負責監測存藥環境的溫度與溼度，並判斷當下環境是否符合藥物存放的標準，如果溫度與溼度兩項皆符合標準則亮起綠色LED，若其中一項未符合標準則亮起黃色LED，而兩項皆未符合標準則亮起紅色LED。
用戶需先使用setup.php建立資料庫後，再執行Server.py程式檔，即可透過LogRecord_GET.php將監測的時間、溫度、溼度及燈號資料傳送至資料庫，以提供用戶進行後續的資料應用。

Client負責擷取遠端資料庫的資料並將其轉為DataFrame結構，再以Matplotlib套件將資料視覺化，最後輸出為折線圖。
Client.py提供用戶可在執行python檔後，按下0結束程式；按下1，透過網頁瀏覽的方式得知倉庫的環境狀態變化(showChart.php、showColumn.php)；按下2，執行上述功能，並在有七段顯示器及按鈕時，直接讓七段顯示器顯示最新的溫度，而用戶可透過按下按鈕切換為顯示溼度。



---

## 硬體線路圖

| Server | Client |
|:--------:|:--------:|
|   接線圖   |   接線圖   |
|<img width="250px" src="https://i.imgur.com/LGc9gWe.png" />|<img width="250px" src="https://i.imgur.com/SZCcUeE.png" />|
|硬體線路圖(電路圖)|硬體線路圖(電路圖)|
|<img width="250px" src="https://i.imgur.com/OwPiT0g.jpg" />|<img width="250px" src="https://i.imgur.com/yN3Lvk2.jpg" />|



---

## 程式說明

[程式碼說明](https://hackmd.io/xMYWkNDvQEOiVJVaydRgng)



---

## 專題DEMO

* DEMO影片
    |                           Server                            |                           Client                            |
    |:-----------------------------------------------------------:|:-----------------------------------------------------------:|
    |          [demo link](https://youtu.be/kleWXTKR9NI)          |          [demo link](https://youtu.be/CdhzDdGlTBA)          |
    | <img width="250px" src="https://i.imgur.com/7u816EA.jpg" /> | <img width="250px" src="https://i.imgur.com/g1G1zX6.png" /> |
* Client Shell
    * : 0 結束程式
    <img width="250px" src="https://i.imgur.com/ESBjOvp.png" />
    * : 1 僅擷取資料並更新網頁圖片 / : 2 擷取資料並更新網頁圖片、可監聽按鈕切換七段顯示器顯示溫溼度
    <img width="250px" src="https://i.imgur.com/EhHlkJ2.png" /><img width="250px" src="https://i.imgur.com/by16CVI.png" />
    * : 1 或 : 2 的圖片輸出
    <img width="250px" src="https://i.imgur.com/53DEVHc.jpg" /><img width="250px" src="https://i.imgur.com/cAk6xzg.jpg" />


