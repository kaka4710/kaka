# 爬取笔趣阁小说  阴山道士笔记
'''
    import json
    import requests
    from requests.exceptions import RequestException
    import re
    import time
    from bs4 import BeautifulSoup


    def get_one_page(url):
        try:
            headers = {
                    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.97 Safari/537.36'
                }
            response = requests.get(url, headers = headers)
            response = response.content
            response_doc = str(response,"utf-8")
            return response_doc
        except RequestException:
            return None


    def parse_one_page(html):
        soup = BeautifulSoup(html,"html.parser")
        items = soup.find('div',{'id':'content'})
        return items.get_text()


    #for m in soup.find_all('div',{'id':'content'}):
    #    print(m.get_text())

    def write_to_file (content):
        with open('result.txt', 'a', encoding = 'utf-8') as f:
            f.write(content+ '\n')

    '''
        html = get_one_page(url)
        print(html)
        soup1 = parse_one_page(html)
        for string in soup1:
            print(repr(string))
        write_to_file(soup)
    '''

    for i in range(310):
        url = 'https://www.biquke.com/bq/58/58725/{}.html'.format(i+7846665)
        html = get_one_page(url)
        time.sleep(5)
        print(html)
        soup = parse_one_page(html)
        print(soup)
        write_to_file(soup)
        i += 1
'''
