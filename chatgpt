# ライブラリをインポートする
import requests
from bs4 import BeautifulSoup
import smtplib

# google patentsから前日の9時以降にpublishされた「potato」に関する特許文献を検索する
response = requests.get('https://www.google.com/patents/search?q=potato&date=after:2022-12-07+9:00&tbm=pts')
soup = BeautifulSoup(response.text, 'html.parser')

# 特許文献のタイトルを取得する
titles = []
for tag in soup.find_all('h3', {'class': 'title'}):
    titles.append(tag.text)

# メールを送信する
server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
server.login('ninjin@mail.com', '<password>')
server.sendmail('ninjin@mail.com', 'ninjin@mail.com', '\n'.join(titles))
server.quit()
