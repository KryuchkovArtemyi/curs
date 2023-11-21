# curs
Телеграм бот по парсингу сайта spo13 с выводом последних новостей в телеграме

Код программы:

import requests
import telebot
from bs4 import BeautifulSoup as b

URL = 'https://spo-13.mskobr.ru/novosti'
API_KEY = 'Здесь ваш токет от BotFather'
r = requests.get(URL)
soup = b(r.text, 'html.parser')
data = soup.find_all('div', class_='kris-news-data')
title = soup.find_all('div', class_='kris-news-tit')
opis = soup.find_all('div', class_='kris-news-body')
prod = soup.find_all('a', class_='link_more')
def list(list): return [c.text for c in list]
def link(list): return [c.get('href') for c in list]
dl = list(data)
tl = list(title)
ol = list(opis)
pl = link(prod)
def split(text):
    get = text.strip().split('''
                        

                                                                                                            


                                    ''')
    return get[0]
bot = telebot.TeleBot(API_KEY, parse_mode='HTML')
@bot.message_handler(commands=['start'])

def hello(message):
    bot.send_message(message.chat.id, 'Здравствуйте, чтобы узнать новости нашего колледжа введите любую цифру:')

@bot.message_handler(content_types=['text'])
def jokes(message):
    if message.text.lower() == '1':
        bot.send_message(message.chat.id, f'<b>{dl[0].strip()}\n\n{tl[0].strip()}</b>\n\n{split(ol[0])}\n\n<a href="https://spo-13.mskobr.ru{pl[0]}">Подробнее</a>')
    elif message.text.lower() == '2':
        bot.send_message(message.chat.id, f'<b>{dl[1].strip()}\n\n{tl[1].strip()}</b>\n\n{split(ol[1])}\n\n<a href="https://spo-13.mskobr.ru{pl[1]}">Подробнее</a>')
    elif message.text.lower() == '3':
        bot.send_message(message.chat.id, f'<b>{dl[2].strip()}\n\n{tl[2].strip()}</b>\n\n{split(ol[2])}\n\n<a href="https://spo-13.mskobr.ru{pl[2]}">Подробнее</a>')
    elif message.text.lower() == '4':
        bot.send_message(message.chat.id, f'<b>{dl[3].strip()}\n\n{tl[3].strip()}</b>\n\n{split(ol[3])}\n\n<a href="https://spo-13.mskobr.ru{pl[3]}">Подробнее</a>')
    elif message.text.lower() == '5':
        bot.send_message(message.chat.id, f'<b>{dl[4].strip()}\n\n{tl[4].strip()}</b>\n\n{split(ol[4])}\n\n<a href="https://spo-13.mskobr.ru{pl[4]}">Подробнее</a>')
    elif message.text.lower() == '6':
        bot.send_message(message.chat.id, f'<b>{dl[5].strip()}\n\n{tl[5].strip()}</b>\n\n{split(ol[5])}\n\n<a href="https://spo-13.mskobr.ru{pl[5]}">Подробнее</a>')
    elif message.text.lower() == '7':
        bot.send_message(message.chat.id, f'<b>{dl[6].strip()}\n\n{tl[6].strip()}</b>\n\n{split(ol[6])}\n\n<a href="https://spo-13.mskobr.ru{pl[6]}">Подробнее</a>')
    elif message.text.lower() == '8':
        bot.send_message(message.chat.id, f'<b>{dl[7].strip()}\n\n{tl[7].strip()}</b>\n\n{split(ol[7])}\n\n<a href="https://spo-13.mskobr.ru{pl[7]}">Подробнее</a>')
    elif message.text.lower() == '9':
        bot.send_message(message.chat.id, f'<b>{dl[8].strip()}\n\n{tl[8].strip()}</b>\n\n{split(ol[8])}\n\n<a href="https://spo-13.mskobr.ru{pl[8]}">Подробнее</a>')
    elif message.text.lower() == '10':
        bot.send_message(message.chat.id, f'<b>{dl[9].strip()}\n\n{tl[9].strip()}</b>\n\n{split(ol[9])}\n\n<a href="https://spo-13.mskobr.ru{pl[9]}">Подробнее</a>')

    else:
        bot.send_message(message.chat.id, 'Введите любую цифру:')
bot.polling()




Описание кода:

«import requests
import telebot
from bs4 import BeautifulSoup as b»
В данном блоке происходит объявление всех используемых библиотек 

«URL = 'https://spo-13.mskobr.ru/novosti'» 
Здесь вставляем ссылку на сайт который будем «парсить», а конкретнее ссылку сайта Политехнического колледжа им. П.А. Овчинникова

«API_KEY = 'Здесь ваш токет от BotFather'»
На данном этапе мы обращались к BotFather и получили «токен» для создания своего телеграм бота

«r = requests.get(URL)
soup = b(r.text, 'html.parser')
data = soup.find_all('div', class_='kris-news-data')
title = soup.find_all('div', class_='kris-news-tit')
opis = soup.find_all('div', class_='kris-news-body')
prod = soup.find_all('a', class_='link_more')
def list(list): return [c.text for c in list]
def link(list): return [c.get('href') for c in list]
dl = list(data)
tl = list(title)
ol = list(opis)
pl = link(prod)»

здесь происходит объявление основных переменных.


«def split(text):
    get = text.strip().split('''
                        

                                                                                                            


                                    ''')»
Данная функция служит решением, которое при выводе новости с сайта колледжа, убирала ссылку на фотографию прикрепленную к новости.

«bot = telebot.TeleBot(API_KEY, parse_mode='HTML')
@bot.message_handler(commands=['start'])»

Эти строчки моего кода используются для начала(запуска) телеграм бота 

«def hello(message):
    bot.send_message(message.chat.id, 'Здравствуйте, чтобы узнать новости нашего колледжа введите любую цифру:')»

Функция def hello(message): здоровается с пользователем, который запустил моего бота
   
«def jokes(message):
    if message.text.lower() == '1':
        bot.send_message(message.chat.id, f'<b>{dl[0].strip()}\n\n{tl[0].strip()}</b>\n\n{split(ol[0])}\n\n<a href="https://spo-13.mskobr.ru{pl[0]}">Подробнее</a>')»
эта функция отвечает за вывод новости в телеграм боте, а точнее вывода самой последней новости размещённой на сайте колледжа, при вводе единицы. Так же имеется сслыка подробнее, при нажатие на которую вас перенаправит на сайт этой новости 

«elif message.text.lower() == '2':
        bot.send_message(message.chat.id, f'<b>{dl[1].strip()}\n\n{tl[1].strip()}</b>\n\n{split(ol[1])}\n\n<a href="https://spo-13.mskobr.ru{pl[1]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не первой, а второй новости колледжа

«elif message.text.lower() == '3':
        bot.send_message(message.chat.id, f'<b>{dl[2].strip()}\n\n{tl[2].strip()}</b>\n\n{split(ol[2])}\n\n<a href="https://spo-13.mskobr.ru{pl[2]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не второй, а третей новости колледжа

    «elif message.text.lower() == '4':
        bot.send_message(message.chat.id, f'<b>{dl[3].strip()}\n\n{tl[3].strip()}</b>\n\n{split(ol[3])}\n\n<a href="https://spo-13.mskobr.ru{pl[3]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не третей, а четвертой новости колледжа

    «elif message.text.lower() == '5':
        bot.send_message(message.chat.id, f'<b>{dl[4].strip()}\n\n{tl[4].strip()}</b>\n\n{split(ol[4])}\n\n<a href="https://spo-13.mskobr.ru{pl[4]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не четвертой, а пятой новости колледжа

    «elif message.text.lower() == '6':
        bot.send_message(message.chat.id, f'<b>{dl[5].strip()}\n\n{tl[5].strip()}</b>\n\n{split(ol[5])}\n\n<a href="https://spo-13.mskobr.ru{pl[5]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не пятой, а шестой новости колледжа

    «elif message.text.lower() == '7':
        bot.send_message(message.chat.id, f'<b>{dl[6].strip()}\n\n{tl[6].strip()}</b>\n\n{split(ol[6])}\n\n<a href="https://spo-13.mskobr.ru{pl[6]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не шестой, а седьмой новости колледжа

    «elif message.text.lower() == '8':
        bot.send_message(message.chat.id, f'<b>{dl[7].strip()}\n\n{tl[7].strip()}</b>\n\n{split(ol[7])}\n\n<a href="https://spo-13.mskobr.ru{pl[7]}">Подробнее</a>')»

эта функция так же отвечает за вывод новости с сайта, но уже не седьмой, а восьмой новости колледжа

   « elif message.text.lower() == '9':
        bot.send_message(message.chat.id, f'<b>{dl[8].strip()}\n\n{tl[8].strip()}</b>\n\n{split(ol[8])}\n\n<a href="https://spo-13.mskobr.ru{pl[8]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не восьмой, а девятой новости колледжа

   « elif message.text.lower() == '10':
        bot.send_message(message.chat.id, f'<b>{dl[9].strip()}\n\n{tl[9].strip()}</b>\n\n{split(ol[9])}\n\n<a href="https://spo-13.mskobr.ru{pl[9]}">Подробнее</a>')»
эта функция так же отвечает за вывод новости с сайта, но уже не девятой, а десятой новости колледжа

   «else:
        bot.send_message(message.chat.id, 'Введите любую цифру:')
bot.polling()»
если  пользователь вводит другое значение или число, то бот выдает сообщение: 'Введите любую цифру:
