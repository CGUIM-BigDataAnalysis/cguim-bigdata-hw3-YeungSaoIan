長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
library(rvest) ##第一次使用要先安裝 install.packages("rvest")
```

    ## Loading required package: xml2

``` r
library(xml2)
library(XML)
```

    ## 
    ## Attaching package: 'XML'

    ## The following object is masked from 'package:rvest':
    ## 
    ##     xml

``` r
##read_html
a<-"https://www.ptt.cc/bbs/LoL/index.html"
b<-"https://www.ptt.cc/bbs/LoL/index7183.html"
c<-"https://www.ptt.cc/bbs/LoL/index7182.html"
d<-"https://www.ptt.cc/bbs/LoL/index7181.html"
e<-"https://www.ptt.cc/bbs/LoL/index7180.html"
f<-"https://www.ptt.cc/bbs/LoL/index7179.html"

vec<-c(a,b,c,d,e,f)
result<-NULL
for(i in vec)
{
##PTTLOL<-"https://www.ptt.cc/bbs/LoL/index.html"
LOLContent<-read_html(i)
##html_nodes
##html_text
post_title <- LOLContent %>% html_nodes(".title") %>% html_text()
push_num <- LOLContent %>% html_nodes(".nrec") %>% html_text()
post_author <- LOLContent %>% html_nodes(".author") %>% html_text()

testpost_output <- data.frame(testtitle = post_title, testpushnum = push_num, testauthor = post_author)
result<-rbind(result,testpost_output)
next
}
LOL_posts<-result
```

爬蟲結果呈現
------------

``` r
#這是R Code Chunk
knitr::kable(
    LOL_posts[1:100,c("testtitle","testpushnum","testauthor")]) ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| testtitle                                           | testpushnum | testauthor   |
|:----------------------------------------------------|:------------|:-------------|
| \[閒聊\] 汎如果可以多目標疊被動                     | 1           | Sasamumu     |
| \[情報\] 測試服改動：大量道具繼續調整！             | 5           | BRITAINCAT   |
| \[公告\] LoL║英雄 ┌──┐４月閒聊區┌→ 67               | rainnaw     | ind          |
| \[公告\] LoL║ 聯盟┘板規└─────┘                      | rainnawin   | d            |
| \[電競\] 近期賽事 （日期版）                        | 40          | fkc          |
| \[電競\] 近期賽事 （地區版）                        | 43          | superRKO     |
| \[實況\] 口口口口 / EDG Meiko                       |             | rosalic0423  |
| \[發錢\] 嚇死我惹                                   | 爆          | timblue0823  |
| \[閒聊\] 【滑新聞】台灣的學歷萬能論？國動：講什     | 35          | ALOVET       |
| \[閒聊\] 同人圖分享-cross                           | 11          | f222051618   |
| \[閒聊\] dinter 解析最新版本葛雷夫出裝天賦          | X1          | Comebuy      |
| \[實況\] owo ovo / Kusuri / WE xiye                 | 3           | iamwhoim     |
| \[公告\] LoL 板 開始舉辦樂透!                       | 15          | rainnawind   |
| \[實況\] 衰神型玩家李豪豪                           |             | kayamarai    |
| \[閒聊\] 選手排位代表甚麼                           | 1           | xbeyond      |
| \[問題\] 造型會影響攻速嗎？                         | 15          | ctgplayer    |
| \[問題\] S2的阿璃有多強?                            | 30          | jacktheone   |
| \[實況\] 咪咪蛋 / FW MMD                            | 10          | aiya0824     |
| \[閒聊\] 閃電狼不找挖ZIV做對了嗎                    | X1          | zindqq       |
| \[創作\] LMS word puzzle                            | 20          | lnsattaida   |
| Re: \[閒聊\] 【滑新聞】台灣的學歷萬能論？國動：講什 | 3           | fdfdfdfd51   |
| \[閒聊\] 請問選手怎麼保持遊戲的熱忱                 | 3           | e807761566   |
| \[實況\] 台南凳紫棋/厭世咪呀                        | 2           | strangelife  |
| \[心得\] 再訪LCK觀賽(X見面會(O心得                  | 22          | yuanhorn     |
| \[外絮\] MVP Ian:MVP最帥最愛撒嬌的就是我            | 11          | s80554       |
| \[心得\] 拉姆斯 神龜打野輕鬆上金牌                  | 11          | kai3368      |
| \[閒聊\] 帳號被賣掉後Garena效率太狂啦！             | 41          | john123524   |
| \[問題\] 4/9 ahq對fb ban角問題                      | 3           | Qoopy        |
| \[實況\] 口口口 口口 / SKT T1 Peanut(關）           | 13          | s80554       |
| \[閒聊\] 到底甚麼時候才會開放送禮功能??             | 1           | yugiboy      |
| \[實況\] SKT T1 Bang(關)                            | 8           | where1993    |
| \[實況\] 口口口口/SKT T1 Blank                      | 13          | ulrike1210   |
| \[實況\] SKT T1 WoIf                                | 5           | monangel     |
| (本文已被刪除) \[chulashiy\]                        | 2           | -            |
| \[閒聊\] 甘沁沁FB                                   | 23          | d86249       |
| Re: \[閒聊\] 阿璃是不是不太適合西門                 | 5           | ejywar       |
| \[實況\] SKT T1 口口口 / SKT T1 SKY(收              | 7           | jennytsai019 |
| \[實況\] 口 口 口口 口 / EDG Mouse                  | 3           | dinter9921   |
| \[問題\] 歐拉夫的召喚師技能                         | 10          | vankhub      |
| \[問題\] 玩操作型角色 真的需要天份嗎？              | 10          | GaryLeessang |
| \[外絮\] LCK春季季後賽-KT&MVP監督對明日之戰想法     | 21          | ubiqui       |
| \[閒聊\] 遠程角為什麼可以出兵捶                     | 14          | tigotigo5566 |
| \[閒聊\] 小熊好正                                   | X4          | s12457868    |
| (本文已被刪除) \[applepowpow\]                      |             | -            |
| (本文已被刪除) \[rabbitball19\]                     | 3           | -            |
| \[實況\] 性感荷官 上路慎 五排彈性 關台              | 8           | MRsoso       |
| Re: \[閒聊\]為什麼西門不能上場?                     |             | kingion      |
| Re: \[閒聊\] 貝克:當初想找丁特去ahq打將狗           | 12          | mark2010     |
| \[發錢\] 推 文 通 通 給 我 沁 起 來                 | 爆          | InnGee       |
| Re: \[閒聊\]為什麼西門不能上場?                     | 1           | vogue38      |
| \[問題\] 競時通多了一大堆外國人好友                 | 17          | tung3567752  |
| \[問題\] EU LCS FNC下路卡蜜兒 真的有搞頭?           | 3           | happyjames1  |
| \[閒聊\] AHQ e-Sports FB & 戰地報導                 | 10          | andy82116    |
| \[揪團\] 微低端午排彈性積分 滿惹唷                  | 2           | YaHiiiiiii   |
| Re: \[閒聊\] 老實講 女森開台牌位有很重要嗎          | 5           | Vicchiang    |
| \[實況\] 加藤鷹架 金牌場的極度暴躁                  |             | pepsihong10  |
| \[實況\] Nightblu3 萌萌打野NB3 揮霍登場             | 4           | dingo1214    |
| Re: \[閒聊\] 老實講 女森開台牌位有很重要嗎          | 1           | a58805082    |
| \[揪團\] 白金鑽石彈性 -1專職JG                      |             | mickeykiller |
| (本文已被刪除) \[jeffou1112\]                       |             | -            |
| \[實況\] 細雪緋悠 馬爾音樂台 (奧                    | 1           | gzzzneww     |
| Re: \[閒聊\] 貝克:當初想找丁特去ahq打將狗           | 9           | jeffou1112   |
| \[心得\] 二訪LCK現場心得文!!(圖多)                  | 27          | jean108p     |
| Re: \[閒聊\] 貝克:當初想找丁特去ahq打將狗           | 8           | DinterIsDog  |
| \[揪團\] 彈性積分 5缺2 彈性牌位需金牌以上           | 1           | NuClei       |
| Re: \[閒聊\] 貝克:當初想找丁特去ahq打將狗           | 8           | JuicyChen    |
| \[閒聊\] reddit H2K vs FNC                          | 20          | JEFF11503    |
| Re: \[閒聊\] Rami以後還會開台嗎？？                 | 6           | tom80727     |
| \[閒聊\] 老實講 女森開台牌位有很重要嗎              | 28          | tom80727     |
| \[閒聊\] 雷茲 Buff or 再重製?                       | 18          | hkr91511208  |
| Re: \[閒聊\] Rami以後還會開台嗎？？                 | 36          | kiga4ni      |
| \[閒聊\] 貝克:當初想找丁特去ahq打將狗               | 30          | z83420123    |
| \[問題\] 紅色符文 雙穿效益問題                      | 6           | Neverfor     |
| \[實況\] 噯卑彌呼，韓服Rank                         |             | Destinyandy  |
| \[實況\] 我在減肥只是看起來不大像/MiSTakE           | 6           | PibaoN       |
| (本文已被刪除) \[yiwangneko\]                       |             | -            |
| \[閒聊\] 2017 LMS春季聯賽Highlight Reel 第四集      | 2           | Comebuy      |
| \[實況\] 我要儲值我要支持佛心公司佛心公司           |             | InnGee       |
| \[閒聊\] 李星史詩造型中文語音                       | 18          | LIN6627      |
| \[閒聊\] \[統統動起來\*1\]逆轉肥宅真人版！          | 8           | jeff860109   |
| \[閒聊\] 墨菲特大招按牆壁可以撞很快                 | 37          | HydraQ       |
| \[外絮\] FW FB                                      | 62          | dinter9921   |
| \[情報\] 本週普羅精選英雄：04/11 ～ 04/14           | 7           | Waitaha      |
| \[閒聊\] 為什麼對LMS隊伍沒信心？                    | 2           | zindqq       |
| (本文已被刪除) \[fishpill\]                         | 91          | -            |
| Re: \[閒聊\] 韓服菁英場 內有西門 Faker Bang Smeb    |             | iamfenixsc   |
| \[問題\] 如果西門搭配上閃電狼後勤，是否可行?        |             | xup654z      |
| \[問題\] 韓服高端的埃爾文是哪兩流派                 | 23          | Manaku       |
| \[閒聊\] 為什麼LOL限制最多只能帶六個裝備 ？         | 19          | nicholas0406 |
| \[閒聊\] 關於專精                                   | 3           | chaselove610 |
| \[閒聊\] Reddit CLG vs FLY 賽後討論                 | 20          | cycling      |
| \[問題\] 請問FlyQuest是不是藏招大師                 | 21          | pentasy      |
| \[揪團\] 高端場五排彈性積分                         | 5           | Ayenix       |
| \[影片\] 國棟半夜開台怒噴吵到警察來                 |             | ss8901233    |
| \[閒聊\] 角逐最佳電競選手！台灣選手Karsa進入票      |             | pyooyp       |
| \[閒聊\] 湯米ＦＢ                                   | 10          | strangelife  |
| \[閒聊\] Rami以後還會開台嗎？？                     | 22          | nameibaby    |
| \[外絮\] SKT Huni：上路飛斯帶點燃的好處(非原標)     | 13          | where1993    |
| \[外絮\] 維持心理狀態的秘訣--SKT T1 Blank!          | 22          | ubiqui       |
| \[問題\] 2017ADC                                    | 9           | xaing1004    |

解釋爬蟲結果
------------

``` r
#Post的類型排名是：
#實況 22個
#問題 17個

#最多推文數的文章是
"[外絮] FW FB" #共62個
```

    ## [1] "[外絮] FW FB"

``` r
#另外有一個推文數很高的文章，但是被刪除了

#最活躍的作者是fdfdfdfd51，共發了4篇文章
```
