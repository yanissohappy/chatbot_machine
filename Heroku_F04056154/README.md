# 2018 計算理論期末專題 TOC final project based on Heroku

### Topic:[超展開奇片式自助餐有限狀態機](https://www.facebook.com/Yans-TOC-robot-571247746672227/)

A Facebook messenger bot based on a finite state machine


## Finite State Machine
![fsm](./fsm.png)

## Motivation
原本是想要做單純的推薦食物名單，可是不知怎地做著做著就超展開了。(惡搞魂覺醒)

## Finished Part
- [x] 所有的base requirement 
- [x] Sending images 
- [x] 用Heroku部署FB Chatbot

## Usage
The initial state is set to `user`.

Every time `user` state is triggered to `advance` to another state, it will `go_back` to `user` state after the bot replies corresponding message.

:octocat: 建議您一開始輸入`使用說明`方便了解一開始輸入甚麼，每一個reply都會用[]給予回答的提示<3

* user
	* Input: "使用說明"
		* Reply: "遊戲的一開始，請您輸入想吃的自助餐，[吃大八]？[吃海港]？[吃香格里拉]？或是輸入[故事情節]了解故事走向。"
		* Reply: ![為甚麼你不問神奇海螺呢](https://img.moegirl.org/common/thumb/7/7b/SpongeBob_SquarePants.jpg/250px-SpongeBob_SquarePants.jpg)
		* Next State: state1/state2/state12/state3

	* Input: "吃大八"
		* Reply: "你走進去了大八，詢問：「請問[自助餐]/[牛排館]有開嗎？」"
		* Next State: state1
		
	* Input: "吃香格里拉"
		* Reply: "NOOOO!!!!!海港海港海港海港海港海港海港...(洗腦中)你被洗腦了，並且你口中喊著：「[是]」然後你走出香格里拉，邁向海港。"
		* Next State: state12

	* Input: "吃海港"
		* Reply: "您真是會選擇，好吃的自助餐在海港，猜猜看好吃的時段是甚麼時候？[下午茶]或[晚餐]？"
		* Next State: state2	
* state1
	* Input: "自助餐"
		* Reply: "服務生：「有呀，請讓我帶領您前往那兒。您今天幾人用餐？[4人]/[1人]」"
		* Next State: state1_1

	* Input: "牛排館"
		* Reply: "服務生：「有呀，請讓我帶領您前往那兒。您今天幾人用餐？[4人]/[1人]」"
		* Next State: state1_2
* state1_1
	* Input: "4人"
		* Reply: "服務生：「4不吉利耶，我們公司拒絕您用餐哦。」"
		* Reply: "服務生："
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state1_3→user

	* Input: "1人"
		* Reply: "服務生：「（murmur）好可憐喔...一個人吃東西。」你聽到了，說：「你們甚麼爛公司！我要走人了。」"
		* Reply: "服務生："
		* Next State: state1_4→user
* state1_2
	* Input: "4人"
		* Reply: "服務生：「4不吉利耶，我們公司拒絕您用餐哦。」你聽到了：「（攻擊服務生HP-10000）」"
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state1_5→user

	* Input: "1人"
		* Reply: "服務生：「（murmur）好可憐喔...一個人吃東西。」你聽到了，說：「（攻擊服務生）別小看邊緣人！」"
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state1_6→user
		
* state2
	* Input: "下午茶"
		* Reply: "叭叭！！！！下午茶很難吃捏！打沒！掰掰！"
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state4→user

	* Input: "晚餐"
		* Reply: "對呀，選晚餐就對了，從現在開始您可以跟食物來個美好的邂逅，你要選擇[生魚片]還是[剩魚片]？"
		* Next State: state5
* state3
	* Input: "故事情節"
		* Reply: "作者:呵呵呵...故事您要自己玩出來的唷(姨母笑)這個bot是很逗趣(?)的，但是可能會玩到很生氣~請別玩到高血壓哦。(超讓人生氣)"
		* Next State: state13→user
* state5		
	* Input: "生魚片"
		* Reply: "經理走過來，說：「您吃的鮭魚生魚片來自濁水溪，是個不可多得的珍貴食材！你[知道]或[不知道]濁水溪有鮭魚？」"
		* Next State: state6

	* Input: "剩魚片"
		* Reply: "孟婆：「嘻嘻您吃了剩魚片所以拉到壞掉，重新輪迴，喝杯孟婆湯吧。（強灌）」"
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state7→user		
* state6
	* Input: "知道"
		* Reply: "經理：「這位客人，您不但懂吃，還懂地理，[要]或[不要]明天跟我去環遊世界，探查地理？」"
		* Next State: state9

	* Input: "不知道"
		* Reply: "經理：「濁水溪有鮭魚！我說得算！給我滾出去！海港不要有你這種客人！」"
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state8→user
* state9		
	* Input: "要"
		* Reply: "吃一次海港，寫成了亙股雋永的淒美愛情故事，所以請大家多多支持海港（按：海港與作者沒有任何關係）"
		* Reply: <img src="https://sayingimages.com/wp-content/uploads/Lily-the-Swim-Pup-Love-You.jpg" width = "300" height = "220"/>
		* Next State: state11→user

	* Input: "不要"
		* Reply: "經理：「不要？給我滾出去！海港不要有你這種客人！」"
		* Reply: <img src="https://i.imgflip.com/13jurj.jpg" width = "300" height = "220"/>
		* Next State: state10→user	

* state12		
	* Input: "是"
		* Reply: "您真是會選擇，好吃的自助餐在海港，猜猜看好吃的時段是甚麼時候？[下午茶]或[晚餐]？"
		* Next State: state2
	

* **state1_3** or **state1_4** or **state1_5** or **state1_6** or  **state4** or **state7** or **state8** or **state10** or **state11** or **state13**
	* Next State: user		
		