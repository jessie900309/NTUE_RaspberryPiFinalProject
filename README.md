# NTUE_RaspberryPiFinalProject

###### tags: `NTUE_SchoolNote`

#### 國立台北教育大學 110學年度 嵌入式系統 期末專題

:::spoiler Contents
[TOC]
:::



---

## 一、小組分工與討論

直接約在學校圖書館一樓電腦教室討論OuO!
[佩瑩](https://github.com/winnielin17)負責Server端的程式撰寫、資料庫建立及用戶創建、手繪硬體線路圖；[妤婕](https://github.com/jessie900309)負責Client端的程式撰寫、用fritzing畫接線圖、用Google簡報畫系統方塊圖、書面報告整合。全程都在圖書館一起完成，有問題也可以馬上發現討論解決方法。



---

## 二、Medicine Control System專題目的

<img width="500px" src="https://i.imgur.com/EF0hJdS.jpg" />

因應近年來的肺炎風波，醫藥問題也隨之受到重視，Medicine Control System提供一個可以遠距監控存藥倉庫的方法，讓員工可以利用IOT概念實現人與藥物零接觸的工作環境。

<!-- //慘了我掰不下去了www 沒事沒事w 這樣就可以了OuO -->

如圖所示，Medicine Control System主要分為兩個部分，分別是Server端的【存藥倉庫】，和Client端的【遠端辦公室】。

Server負責監測存藥環境的溫度與溼度，並判斷當下環境是否符合藥物存放的標準，如果溫度與溼度兩項皆符合標準則亮起綠色LED，若其中一項未符合標準則亮起黃色LED，而兩項皆未符合標準則亮起紅色LED。
用戶需先使用setup.php建立資料庫後，再執行Server.py程式檔，即可透過LogRecord_GET.php將監測的時間、溫度、溼度及燈號資料傳送至資料庫，以提供用戶進行後續的資料應用。

Client負責擷取遠端資料庫的資料並將其轉為DataFrame結構，再以Matplotlib套件將資料視覺化，最後輸出為折線圖。
Client.py提供用戶可在執行python檔後，按下0結束程式；按下1，透過網頁瀏覽的方式得知倉庫的環境狀態變化(showChart.php、showColumn.php)；按下2，執行上述功能，並在有七段顯示器及按鈕時，直接讓七段顯示器顯示最新的溫度，而用戶可透過按下按鈕切換為顯示溼度。



---

## 三、硬體線路圖

| Server | Client |
|:--------:|:--------:|
|   接線圖   |   接線圖   |
|<img width="250px" src="https://i.imgur.com/LGc9gWe.png" />|<img width="250px" src="https://i.imgur.com/SZCcUeE.png" />|
|硬體線路圖(電路圖)|硬體線路圖(電路圖)|
|<img width="250px" src="https://i.imgur.com/OwPiT0g.jpg" />|<img width="250px" src="https://i.imgur.com/yN3Lvk2.jpg" />|



---

## 四、程式說明

[程式碼說明](https://hackmd.io/xMYWkNDvQEOiVJVaydRgng)



---

## 五、專題DEMO

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



---

## 六、心得

<!-- //我看老師給的word檔還有心得的部分QQ -->
<!-- (啊啊啊啊我忘了QuQ) -->

佩瑩：
經過兩次上傳資料庫的作業練習，在建立資料庫與上傳資料時沒有出現太大的問題，皆能夠順利完成，而在Client端要連結Server端時才發現沒有想像中的容易。一開始以為只需設定Client端就好，在和妤婕一起上網搜尋資料後，得知Server端與Client端都需要進行安裝套件與多個設定步驟(防火牆)，還需要登入資料庫中使用SQL語法進行用戶創建的設定。使用這些不熟悉的指令時感覺有些複雜，也經歷了幾次連結失敗後再上網尋找解決方法的狀況，不過最後還是成功地讓Client端連上資料庫了。
完成了期末專題後，除了將上課時學到的素材加以運用之外，亦學到了許多課堂上沒有提到的內容，感覺十分充實，也很開心修了這門課，能夠學到有關樹莓派與各種電子材料的使用方法及應用。

妤婕：
這次卡關最久的就是資料庫連線問題，php只要知道帳號密碼就可以了，但python如果要連線就必須先由管理員註冊帳號給予權限(說是保護機制，不能直接用root登入)；再來就是網頁不能顯示圖片，因為多年前也有不少人在討論nginx伺服器網頁的```<img>```標籤錯誤，我們起初也認為應該是一樣的原因，改設定檔、重新執行、改變路徑都嘗試了一番卻都沒有成效，最後才發現是html的相對圖片路徑與web-jesse的相對圖片路徑不同，總之兩個問題最後都一起解決了，可喜可賀可口可樂 ˊ uˋ)



---

## 七、參考資料

* [How to enable Remote access to your MariaDB/MySQL database on Ubuntu Bionic or MariaDB < v10.6](https://webdock.io/en/docs/how-guides/database-guides/how-enable-remote-access-your-mariadbmysql-database) / Webdock(2022)
* [MariaDB/MySQL常用指令操作與語法範例](https://www.jinnsblog.com/2017/08/mysql-mariadb-sample.html) / 魏子靖(2017)
* [How to connect Python programs to MariaDB](https://mariadb.com/resources/blog/how-to-connect-python-programs-to-mariadb/) / MariaDB(2020)
