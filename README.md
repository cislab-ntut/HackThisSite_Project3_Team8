# Project8-3_Hackthissite
Hack This Site --- Team8
李晨宇 1063514 Application1,2,3(外加)


---

# Application 1

先找尋屬於自己系統的OS，目前使用的是WINDOWS，所以就下載app1win.zip
![](https://i.imgur.com/olRptqx.png=60%px)

## Think?
![](https://i.imgur.com/i7Co9xV.png=60%px)

## We only get exe, so what’s the serial number?
* We need to know what’s inside the exe
* Binary editor or disassembler 
* Set it be hexadecimal=>byte


網路上得知要破解exe的方式有哪些方法?
https://ithelp.ithome.com.tw/questions/10014824
=>HxD

修改exe檔，選擇先用binary editor，不行的話再使用反組譯器，16位元看每個字(人看得懂的)，查詢SN，上下滑動查詢是否有相似的serial number
![](https://i.imgur.com/TFvrzTN.png)

## Enter the serial number =>correct
上下查找類似serial number格式的密碼，但因為他一開始要求的為SN:**********Authenticate 
所以我就以SN為關鍵字下去查詢果然在上下幾行就有看到類似serial number的一串密碼
![](https://i.imgur.com/xD6TYg8.png)


---

# Application 2
先找尋屬於自己系統的OS，目前使用的是WINDOWS，所以就下載app2win.zip
![](https://i.imgur.com/Qegz0BH.png)
## Think?
* The note: 
   you must connect to the internet
* you get the serial number information from the internet transmission
* network analysis tool ==> Wire shark ( capture the packet )

因為特別說需要網路(非常大的提示)，目前有再修計算機網路概論，平常作業就是用wireshark來擷取封包，馬上就想到用wireshark來進行破解，截取封包或查看內部內容
## Wireshark
![](https://i.imgur.com/C2mj3TE.png)
先開wireshark，網頁要全部關掉，之後打開app2.win，先不要輸入字串，按下wireshark開始節取封包，再app2.win輸入隨便一個字串，按authenticate，等個兩三秒就可以關掉封包截取，開始查看截取內容
## keys123.txt
看到info(Get) 這是程式向server拿取資訊，把那條點開查看裡面，在Hypertext 有很明顯的=>keys123.txt 在網路上搜索此url ![](https://i.imgur.com/mriHO0g.png=50%)

## Enter the address =>correct
![](https://i.imgur.com/wOBgmRW.png)
1.網址進去後，看到一連串的serial number，輸入後就能成功

2.OS版本問題會造成incorrect

3.因為失敗，嘗試過win 10, win 7都是敗，網路上查解答是在win xp(下通過的)，安裝win xp的虛擬機後並在上面運行還是失敗


---

# Application 3
因為application2可能有相容的問題，助教說可以做application3代替
The same concept of the application2
![](https://i.imgur.com/jsr91YC.png=50%px)
## Think?
* The note: you must connect to the internet
* you get the serial number information from the internet transmission network analysis tool ==> Wireshark ( capture the packet )
因為要求跟application2非常相似，一開始就用wireshark擷取封包，進行破解
## Wireshark get
![](https://i.imgur.com/x1iAYDu.png)
#### Get 可以發現hypertext url =>auth.php?key=1
## Address(Application3)+app3/auth.php?key=132
![](https://i.imgur.com/odRfTlN.png)
網頁式搜尋上面所述的網頁+php
#### you can see the "false" on the upper left

![](https://i.imgur.com/0kpUv04.png)
#### stuck in reading data
原本已為這是個讀取解答的過程，馬上又用了wireshark查看是否有其他資訊，沒有透漏任何資訊，打開原始網頁查看，仍沒有任何頭緒，卡住無從下手，這裡開始參考網路上的做法，進去修改app3 true or false 對調，隨便輸入字串(除非真的被你矇中XD)，get false 對於app3是true，因而得到正確解答
## HxD find true/false => exchange 
![](https://i.imgur.com/RlcSTCK.png)
因為他始終卡在Reading data，所以在HxD上就以這個為關鍵字作為查詢，在上下幾行就會看到True跟False
## Exchange each
![](https://i.imgur.com/jaH9b0V.png)
#### True false對調要很注意
不能自己增加字串，不然會造成錯誤，導致打不開，例如true 改成false，四個字元變五個字元，只能去修改後面的的點不能自己新增，在這邊卡超久，同理false改成true最後一個字元也不能動到，不然會產生錯誤，導致改完後的exe檔，點都點不開

application3 false，true對調解法方法資料來源:https://www.youtube.com/watch?v=C5SbCX24_Ug


**報告資料**:
https://drive.google.com/file/d/1DknbPq4XqV_uxf1G_zxSmKkgq6uorwnA/view


---
1051537康宇良 

# Application 7
題目中有兩個檔案
一個執行檔
一個加密後的檔案
![](https://i.imgur.com/nsgYDcJ.png)



開啟exe檔案後為下方的圖
![](https://i.imgur.com/fvIrM9s.png)
輸入錯誤會回傳Invalid Password
![](https://i.imgur.com/WvrhbKK.png)

原先是想直接打開執行檔
但想當然不行
![](https://i.imgur.com/dK3Fc0R.png)
enc檔則是完全打不開
最後直接看影片如何破解

看了影片中所使用的反組譯程式
![](https://i.imgur.com/4cajOQH.png)
剛開始的介面
![](https://i.imgur.com/KJa9QlH.png)

會用上的為左上角、右上角以及右下角的資訊
左上角為執行檔的組合語言
右上為用到的暫存檔位置
右下為儲存的位置以及值
![](https://i.imgur.com/HCjiA9v.png)

在檢查以及輸出是否輸入正確地這裡有個CMP(比較為一樣時回傳True)
故檢查這裡的值

![](https://i.imgur.com/8e073hf.png)

上面寫的儲存位置為EBP-18

![](https://i.imgur.com/kbXXbhW.png)

EBP=0x0019FF30

![](https://i.imgur.com/1yPTOXi.png)


儲存的位置是EBP-0x18
=0x0019FF30-0x18
=0x0019FF18
固執行完加密運算後
結果存在0x0019FF18

此圖為我輸入a後的值
![](https://i.imgur.com/g7bemBh.png)

開始試誤測規則
可以看得出數值會有一定規則的加減
最後測出輸入jjjjjjk後得
出0xDCA
為一開始CMP比較時
要的值
![](https://i.imgur.com/1Sx4X6A.png) ![](https://i.imgur.com/fanvGsG.png)

最後測試輸入後得出一串字
![](https://i.imgur.com/1HFmvlC.png)

參考影片:
https://www.youtube.com/watch?v=iAldYYgSgSc
