# ð¢chat-ranch
###èªåã®è¶£å³ãæ©ã¿ãªã©ãªãã§ããã®chat-ranchã«æ¸ãè¾¼ãã§äººããç¹ãã£ã¦ãããããããªã¨æãããä½æããã¢ããªã±ã¼ã·ã§ã³ã§ãã

![toppage]
(https://gyazo.com/e3763050f4e43d1db19fc84dfd37af29)

#æ¦è¦
### èªåã®chatroomãä½ãäºãã§ãã
å¥½ããªã ãchatroomãä½ãäºãã§ãè©±ãããè©±é¡ãã¨ã«chatroomãä½æããå±éã®è©±é¡ã«ã¤ãã¦ã¿ããªã§chatãããã¨ãã§ããã

# ðApp URL
### **https://chat-ranch.herokuapp.com/**

#ãå©ç¨æ¹æ³
#### ããããã¼ã¸ããæ°è¦ç»é²ããµã¤ã³ã¤ã³
(https://gyazo.com/ccd3e88f543b7abf3d7842f73879266b)
(https://gyazo.com/279f4374cad7d908ba8c63043ea28e42)
#### ãã£ãããä½æããããæ¼ããã£ããã«ã¼ã ãä½æ
#### ãã¼ã¸ä¸é¨ã«ããæç¨¿ãã©ã¼ã ããæç¨¿
#### roomåãã¯ãªãã¯ããã¨ã¯ãªãã¯ããroomã«å¥å®¤ã§ãã
#### ãã£ãããçµäºããããã¯ãªãã¯ã§chat-roomã®åé¤ãçµäºã¨ãªã

# æ©è½ä¸è¦§
ã¦ã¼ã¶ã¼ç®¡çæ©è½ï¼æ°è¦ç»é²ã»ã­ã°ã¤ã³ã»ã­ã°ã¢ã¦ãæ©è½ï¼
ãã£ããã«ã¼ã ç®¡çæ©è½ï¼ãã£ããã«ã¼ã ã®æ°è¦ä½æã»åé¤æ©è½ï¼
ã¡ãã»ã¼ã¸ç®¡çæ©è½ï¼ãã­ã¹ãæç¨¿ã»ç»åæç¨¿æ©è½ï¼

# è¿½å ãããæ©è½
ã¦ã¼ã¶ã¼ã®ãã©ã­ã¼æ©è½è¿½å 
åç»æç¨¿æ©è½ã®è¿½å 

# éçºç°å¢
- VScode
- Ruby 2.6.5
- Rails 6.0.0
- mysql2 0.4.4
- gem 3.0.3
- heroku 7.47.7

# ãã¼ãã«è¨­è¨

## users ãã¼ãã«

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms ãã¼ãã«

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users ãã¼ãã«

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages ãã¼ãã«

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user