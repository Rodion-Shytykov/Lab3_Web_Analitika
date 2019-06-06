# Lab3_Web_Analitika

Telegram Bot виконує пошук за вказаним ключовим словом та виконує аналіз настроїв твітів. 

Для оцінки настрою використовується Google’s score range:  

Картинка
Джерело:https://cloud.google.com/natural-language/

Пошук твітту:   
```
today_datetime = datetime.today().now()
    yesterday_datetime = today_datetime - timedelta(days=1)
    today_date = today_datetime.strftime('%Y-%m-%d')
    yesterday_date = yesterday_datetime.strftime('%Y-%m-%d')
    api = authentication(CONS_KEY,CONS_SECRET,ACC_TOKEN,ACC_SECRET)
    search_result = tweepy.Cursor(api.search,
                                  q=keyword,
                                  since=yesterday_date,
                                  result_type='recent',
                                  lang='en').items(total_tweets)
```

Оцінка настрою:  
```
if final_score <= -0.25:    status = 'NEGATIVE | ❌'elif final_score <= 0.25:    status = 'NEUTRAL | 🔶'else:    status = 'POSITIVE | ✅' 
```

Використано: python 3.6, tweepy, nltk,Google Natural Language API, python-telegram-bot.

****Процес встановлення:****

Встановлення необхідних бібліотек:   
pip3 install tweepy nltk google-cloud-language python-telegram-bot

Сконфігуруймо шлях:   
export GOOGLE_APPLICATION_CREDENTIALS='[PATH_TO_CREDS.JSON]'

Cконфігуруйте наступні токены у файлі third.py:   
```
ACC_TOKEN = 'YOUR_ACCESS_TOKEN'
ACC_SECRET = 'YOUR_ACCESS_TOKEN_SECRET'
CONS_KEY = 'YOUR_CONSUMER_API_KEY'
CONS_SECRET = 'YOUR_CONSUMER_API_SECRET_KEY'
```

Запуск:   
python3 third.py

Результат роботи:

