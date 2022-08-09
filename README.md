# Id-instagram-
Bot Id instagram 
import telebot,requests
bot = telebot.TeleBot("2036853931:AAHBlMjZ6ltXztRngGrNLK9SIg7HhoNIba8")
@bot.message_handler(commands=["start"])
def login(message):
 first = message.from_user.first_name
 bot.send_message(message.chat.id,f"<strong>iH {first}, Sir \n- - - - - - - - - - -\nبوت استخراج sessionid ارسل حسابك الان user:pass </strong>",parse_mode="html")
@bot.message_handler(func=lambda message:True)
def login(message):
 messag = message.text
 username = messag.split(':')[0]
 password = messag.split(':')[1]
 url = 'https://www.instagram.com/accounts/login/ajax/'
 headers = {
 'accept':'*/*',
        'accept-language':'en-US,en;q=0.9',
        'content-length':'378',
        'content-type':'application/x-www-form-urlencoded',
        'cookie':'ig_nrcb=1; mid=Yf5pqwALAAEM7jkopysiKxhVu1Lk; ig_did=5BEF127B-7F5B-4A9F-84A6-F0890EAA2C11; csrftoken=h61zrEGl5Ap1QWAUT1KhkQ9aX4OUAzIr',
        'origin':'https://www.instagram.com',
        'referer':'https://www.instagram.com/',
        'sec-ch-ua':'" Not A;Brand";v="99", "Chromium";v="98", "Google Chrome";v="98"',
        'sec-ch-ua-mobile':'?0',
        'x-asbd-id':'198387',
        'user-agent': 'Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.99 Safari/537.36',
        'x-csrftoken':'h61zrEGl5Ap1QWAUT1KhkQ9aX4OUAzIr',
        'x-ig-app-id':'936619743392459',
        'x-ig-www-claim':'0',
        'x-instagram-ajax':'3bcc4d0b0733',
        'x-requested-with':'XMLHttpRequest',
        }
        
 data = {
 'username':username,
 'enc_password':'#PWD_INSTAGRAM_BROWSER:0:1643714074:'+password
 }
 req = requests.post(url,headers=headers,data=data)
 if ('userId') in req.text:
  cook = req.cookies['sessionid']
  bot.send_message(message.chat.id, f"<strong>SessionID The Account ✅\n- - - - - - - - - - - - - - - - - - - - - - -\nSessionID : {cook}\n- - - - - - - - - - - - - - - - - - - - - - -\n</strong>", parse_mode="html")
 else:
  bot.send_message(message.chat.id, f"<strong>Error The Account ..</strong>", parse_mode="html") 

print("تم التشغيل البيانات بنجاح")
print("Data playback completed successfully, Go to the bot and press / start")
bot.polling(True)
