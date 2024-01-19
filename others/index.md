### 2021-4-2

#### 1.当 chrome 不允许打开无效证书的 https 网站时

```
鼠标放在页面上，然后键盘直接输入thisisunsafe，就可以解决
```

### 2024-1-19

#### 2.Python下载防盗链的图片

```python
import requests

from bs4 import BeautifulSoup

import os

# 图片网站
referer_url = 'https://demo.com'
# 具体图片地址
pic_url='https://demo.com/xxxxx.png'

headers = { "Accept":"text/html,application/xhtml+xml,application/xml;",

            "Accept-Encoding":"gzip",

            "Accept-Language":"zh-CN,zh;q=0.8",

            "Referer":referer_url,

            "User-Agent":"Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.90 Safari/537.36"

            }


res = requests.get(pic_url,headers=headers)

#同级目录
img_name = '图片.png'

#保存图片至本地

with open(img_name,'wb')as f:

 response = res.content

 f.write(response)

 f.close()
```