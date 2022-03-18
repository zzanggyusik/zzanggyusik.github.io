아래 내용은 모두 [Gorio Learning](https://greeksharifa.github.io/references/2020/10/30/python-selenium-usage/) 블로그를 참고해서 작성했습니다.

### 1.Installation Selenium


```python
!pip install Selenium
!apt-get update
```

    Collecting Selenium
      Downloading selenium-4.1.3-py3-none-any.whl (968 kB)
    [K     |████████████████████████████████| 968 kB 6.2 MB/s 
    [?25hCollecting urllib3[secure,socks]~=1.26
      Downloading urllib3-1.26.9-py2.py3-none-any.whl (138 kB)
    [K     |████████████████████████████████| 138 kB 44.4 MB/s 
    [?25hCollecting trio-websocket~=0.9
      Downloading trio_websocket-0.9.2-py3-none-any.whl (16 kB)
    Collecting trio~=0.17
      Downloading trio-0.20.0-py3-none-any.whl (359 kB)
    [K     |████████████████████████████████| 359 kB 48.1 MB/s 
    [?25hRequirement already satisfied: attrs>=19.2.0 in /usr/local/lib/python3.7/dist-packages (from trio~=0.17->Selenium) (21.4.0)
    Requirement already satisfied: sortedcontainers in /usr/local/lib/python3.7/dist-packages (from trio~=0.17->Selenium) (2.4.0)
    Collecting sniffio
      Downloading sniffio-1.2.0-py3-none-any.whl (10 kB)
    Collecting async-generator>=1.9
      Downloading async_generator-1.10-py3-none-any.whl (18 kB)
    Collecting outcome
      Downloading outcome-1.1.0-py2.py3-none-any.whl (9.7 kB)
    Requirement already satisfied: idna in /usr/local/lib/python3.7/dist-packages (from trio~=0.17->Selenium) (2.10)
    Collecting wsproto>=0.14
      Downloading wsproto-1.1.0-py3-none-any.whl (24 kB)
    Requirement already satisfied: PySocks!=1.5.7,<2.0,>=1.5.6 in /usr/local/lib/python3.7/dist-packages (from urllib3[secure,socks]~=1.26->Selenium) (1.7.1)
    Requirement already satisfied: certifi in /usr/local/lib/python3.7/dist-packages (from urllib3[secure,socks]~=1.26->Selenium) (2021.10.8)
    Collecting pyOpenSSL>=0.14
      Downloading pyOpenSSL-22.0.0-py2.py3-none-any.whl (55 kB)
    [K     |████████████████████████████████| 55 kB 2.5 MB/s 
    [?25hCollecting cryptography>=1.3.4
      Downloading cryptography-36.0.2-cp36-abi3-manylinux_2_24_x86_64.whl (3.6 MB)
    [K     |████████████████████████████████| 3.6 MB 40.8 MB/s 
    [?25hRequirement already satisfied: cffi>=1.12 in /usr/local/lib/python3.7/dist-packages (from cryptography>=1.3.4->urllib3[secure,socks]~=1.26->Selenium) (1.15.0)
    Requirement already satisfied: pycparser in /usr/local/lib/python3.7/dist-packages (from cffi>=1.12->cryptography>=1.3.4->urllib3[secure,socks]~=1.26->Selenium) (2.21)
    Collecting h11<1,>=0.9.0
      Downloading h11-0.13.0-py3-none-any.whl (58 kB)
    [K     |████████████████████████████████| 58 kB 3.8 MB/s 
    [?25hRequirement already satisfied: typing-extensions in /usr/local/lib/python3.7/dist-packages (from h11<1,>=0.9.0->wsproto>=0.14->trio-websocket~=0.9->Selenium) (3.10.0.2)
    Installing collected packages: sniffio, outcome, h11, cryptography, async-generator, wsproto, urllib3, trio, pyOpenSSL, trio-websocket, Selenium
      Attempting uninstall: urllib3
        Found existing installation: urllib3 1.24.3
        Uninstalling urllib3-1.24.3:
          Successfully uninstalled urllib3-1.24.3
    [31mERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
    requests 2.23.0 requires urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1, but you have urllib3 1.26.9 which is incompatible.
    datascience 0.10.6 requires folium==0.2.1, but you have folium 0.8.3 which is incompatible.[0m
    Successfully installed Selenium-4.1.3 async-generator-1.10 cryptography-36.0.2 h11-0.13.0 outcome-1.1.0 pyOpenSSL-22.0.0 sniffio-1.2.0 trio-0.20.0 trio-websocket-0.9.2 urllib3-1.26.9 wsproto-1.1.0
    Get:1 https://cloud.r-project.org/bin/linux/ubuntu bionic-cran40/ InRelease [3,626 B]
    Ign:2 https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease
    Get:3 https://cloud.r-project.org/bin/linux/ubuntu bionic-cran40/ Packages [80.4 kB]
    Ign:4 https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64  InRelease
    Get:5 https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Release [696 B]
    Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
    Hit:7 https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64  Release
    Get:8 http://ppa.launchpad.net/c2d4u.team/c2d4u4.0+/ubuntu bionic InRelease [15.9 kB]
    Get:9 https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Release.gpg [836 B]
    Hit:11 http://archive.ubuntu.com/ubuntu bionic InRelease
    Get:12 https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Packages [931 kB]
    Get:13 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
    Hit:14 http://ppa.launchpad.net/cran/libgit2/ubuntu bionic InRelease
    Get:15 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic InRelease [15.9 kB]
    Get:16 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
    Get:17 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [1,479 kB]
    Hit:18 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
    Get:19 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [3,067 kB]
    Get:20 http://ppa.launchpad.net/c2d4u.team/c2d4u4.0+/ubuntu bionic/main Sources [1,827 kB]
    Get:21 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [2,628 kB]
    Get:22 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [2,257 kB]
    Get:23 http://ppa.launchpad.net/c2d4u.team/c2d4u4.0+/ubuntu bionic/main amd64 Packages [936 kB]
    Get:24 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic/main amd64 Packages [45.2 kB]
    Fetched 13.5 MB in 7s (1,894 kB/s)
    Reading package lists... Done


##### 웹 드라이버 설치

- Google Chrome
- Microsoft Edge
- Apple Safari
- Firefox

나는 위 네 가지 중 구글 크롬을 이용했다.


```python
!apt install chromium-chromedriver
!cp /usr/lib/chromium-browser/chromedriver /usr/bin
```

    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following additional packages will be installed:
      chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra
    Suggested packages:
      webaccounts-chromium-extension unity-chromium-extension
    The following NEW packages will be installed:
      chromium-browser chromium-browser-l10n chromium-chromedriver
      chromium-codecs-ffmpeg-extra
    0 upgraded, 4 newly installed, 0 to remove and 63 not upgraded.
    Need to get 88.3 MB of archives.
    After this operation, 294 MB of additional disk space will be used.
    Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 chromium-codecs-ffmpeg-extra amd64 99.0.4844.51-0ubuntu0.18.04.1 [1,143 kB]
    Get:2 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 chromium-browser amd64 99.0.4844.51-0ubuntu0.18.04.1 [77.6 MB]
    Get:3 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 chromium-browser-l10n all 99.0.4844.51-0ubuntu0.18.04.1 [4,388 kB]
    Get:4 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 chromium-chromedriver amd64 99.0.4844.51-0ubuntu0.18.04.1 [5,092 kB]
    Fetched 88.3 MB in 10s (9,235 kB/s)
    Selecting previously unselected package chromium-codecs-ffmpeg-extra.
    (Reading database ... 155335 files and directories currently installed.)
    Preparing to unpack .../chromium-codecs-ffmpeg-extra_99.0.4844.51-0ubuntu0.18.04.1_amd64.deb ...
    Unpacking chromium-codecs-ffmpeg-extra (99.0.4844.51-0ubuntu0.18.04.1) ...
    Selecting previously unselected package chromium-browser.
    Preparing to unpack .../chromium-browser_99.0.4844.51-0ubuntu0.18.04.1_amd64.deb ...
    Unpacking chromium-browser (99.0.4844.51-0ubuntu0.18.04.1) ...
    Selecting previously unselected package chromium-browser-l10n.
    Preparing to unpack .../chromium-browser-l10n_99.0.4844.51-0ubuntu0.18.04.1_all.deb ...
    Unpacking chromium-browser-l10n (99.0.4844.51-0ubuntu0.18.04.1) ...
    Selecting previously unselected package chromium-chromedriver.
    Preparing to unpack .../chromium-chromedriver_99.0.4844.51-0ubuntu0.18.04.1_amd64.deb ...
    Unpacking chromium-chromedriver (99.0.4844.51-0ubuntu0.18.04.1) ...
    Setting up chromium-codecs-ffmpeg-extra (99.0.4844.51-0ubuntu0.18.04.1) ...
    Setting up chromium-browser (99.0.4844.51-0ubuntu0.18.04.1) ...
    update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
    update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
    Setting up chromium-chromedriver (99.0.4844.51-0ubuntu0.18.04.1) ...
    Setting up chromium-browser-l10n (99.0.4844.51-0ubuntu0.18.04.1) ...
    Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
    Processing triggers for hicolor-icon-theme (0.17-2) ...
    Processing triggers for mime-support (3.60ubuntu1) ...
    Processing triggers for libc-bin (2.27-3ubuntu1.3) ...
    /sbin/ldconfig.real: /usr/local/lib/python3.7/dist-packages/ideep4py/lib/libmkldnn.so.0 is not a symbolic link
    
    cp: '/usr/lib/chromium-browser/chromedriver' and '/usr/bin/chromedriver' are the same file


##### 웹 드라이버 설정
Selenium은 실행시 브라우저가 켜지는데, 나는 클라우드 환경(Colab)에서 실행하기 때문에 브라우저를 띄우지 않도록 설정해주었다.


```python
from selenium import webdriver

chrome_options = webdriver.ChromeOptions()

chrome_options.add_argument('--headless')
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')
```

### 1-1.WebDriver Option (Chrome)

위에서 브라우저가 열리지 않도록 설정해주었는데(Headless 설정) 이 밖에도 브라우저의 창 크기, 해당 기기의 정보 등을 설정할 수 있다.


```python
options = webdriver.ChromeOptions()

options.add_argument('headless')
options.add_argument('window-size=1920x1080')
options.add_argument('disable-gpu')

options.add_argument('start-maximized')
options.add_argument('disable-infobars')
options.add_argument('--disable-extensions')

options.add_experimental_option('excludeSwitches', ['enable-automation'])
options.add_experimental_option('useAutomationExtension', False)
options.add_argument('--disable-blink-features=AutomationControlled')

options.add_experimental_option('debuggerAddress', '127.0.0.1:9222')
```

### 2.URL Load


```python
driver = webdriver.Chrome('chromedriver', options=chrome_options)  # 웹 드라이버 로드
url = 'https://www.google.com/'
driver.get(url)
```

##### 현재 url 얻기


```python
print(driver.current_url)
```

    https://www.google.com/


##### 브라우저 닫기


```python
driver.close()
```

### 3.[Wait till Load Webpage](https://selenium-python.readthedocs.io/waits.html)
브라우저에서 웹 페이지를 로드하는데 시간이 걸린다. 따라서 모든 요소가 전부 준비될 때까지 기다려야 한다.

time.sleep(secs) 함수를 사용해 무조건 몇 초간 대기한다. 편리하긴 하지만 지양하도록 하자.


```python
import time

time.sleep(1)
```

##### Implicit Waits (암묵적 대기)
웹 드라이버에 영구적으로 작용하며 요소가 로드될 때까지 지정한 시간만큼 대기한다. 단위는 초이며, default 값은 0이다.


```python
driver.implicitly_wait(time_to_wait=5)
```

##### Explicit Waits (명시적 대기)

아래 코드는 로드한 최대 5초동안 로드한 웹 페이지에서 gLFyf인 element를 찾을 수 있는지 0.5초마다 시도한다.
EC(expected_conditions)가 만약 element를 찾으면 True를 그렇지 않으면 False를 반환한다.


```python
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome('chromedriver', options=chrome_options)
driver.get(url='https://www.google.com/')
try:
    element = WebDriverWait(driver, 5).until(
        EC.presence_of_element_located((By.CLASS_NAME , 'gLFyf'))
    )
finally:
    driver.quit()
```

until(method, message=' ') 함수는 method 반환값이 False인 동안 계속 method를 실행하고 <br>
until_not(method, message=' ') 함수는 True인 동안 실행한다.

element 외에도 다양한 조건을 사용할 수 있다. <br>

제목이 어떤 문자열인지, 어떤 문자열을 포함하는지, 특정 또는 모든 요소가 로드되었거나, 볼 수 있거나, 볼 수 없거나, 클릭 가능하거나 등등

- title_is
- title_contains
- presence_of_element_located
- visibility_of_element_located
- visibility_of
- presence_of_all_elements_located
- text_to_be_present_in_element
- text_to_be_present_in_element_value
- frame_to_be_available_and_switch_to_it
- invisibility_of_element_located
- element_to_be_clickable
- staleness_of
- element_to_be_selected
- element_located_to_be_selected
- element_selection_state_to_be
- element_located_selection_state_to_be
- alert_is_present

##### Custom Wait Conditions (커스텀 대기)
custom으로 대기 조건을 설정하는 것도 가능하다. __init__ 함수와 __call__ 함수를 구현한 클래스를 작성하면 된다.


```python
class element_has_css_class(object):
  """An expectation for checking that an element has a particular css class.

  locator - used to find the element
  returns the WebElement once it has the particular css class
  """
  def __init__(self, locator, css_class):
    self.locator = locator
    self.css_class = css_class

  def __call__(self, driver):
    element = driver.find_element(*self.locator)   # Finding the referenced element
    if self.css_class in element.get_attribute("class"):
        return element
    else:
        return False

# Wait until an element with id='myNewInput' has class 'myCSSClass'
wait = WebDriverWait(driver, 10)
element = wait.until(element_has_css_class((By.ID, 'myNewInput'), "myCSSClass"))
```

### 4.Locating Elemnts

크롤링을 하기 위해서는 해당 웹 페이지가 어떤 요소들로 구성돼 있는지 알아야 한다. <br>
요소를 확인하기 위해선 command + option + i 키로 개발자 도구를 켠다.

<img width="1624" alt="스크린샷 2022-03-17 오후 9 56 17" src="https://user-images.githubusercontent.com/76269316/158813085-981ed0d7-2bbb-4ce7-9eb8-d6bfc1918d8b.png">


왼쪽 위의 <img width="33" alt="스크린샷 2022-03-17 오후 9 45 43" src="https://user-images.githubusercontent.com/76269316/158811223-e18be2fb-9c16-4a5a-8eb3-a11ade995716.png">
 버튼을 누르고 웹 페이지의 요소를 클릭하면 해당 코드 부분으로 이동한다.

 <img width="1624" alt="스크린샷 2022-03-17 오후 9 56 59" src="https://user-images.githubusercontent.com/76269316/158813196-98875d71-5ad9-4fd9-a5ce-9ad30f634f32.png">


Selenium에서도 요소를 찾는 함수를 지원한다. <br>
함수가 업데이트 돼서 아래와 같이 작성할 것을 권장한다. 자세한 것은 [여기](https://goodthings4me.tistory.com/567)를 참조 <br>

- find_element는 조건에 맞는 요소 하나를 반환 <br>
- find_elements는 조건을 만족하는 모든 요소를 iterable 형태로 반환


```python
# 위에서 드라이버를 종료시켜서 다시 로드해줬다.
driver = webdriver.Chrome('chromedriver', options=chrome_options)  # 웹 드라이버 로드
url = 'https://www.google.com/'
driver.get(url)
```


```python
search_box = driver.find_element(By.CLASS_NAME, 'gLFyf')
```

- By.CLASS_NAME
- By.ID
- By.NAME
- By.LINK_TEXT
- By.PARTIAL_LINK_TEXT
- By.TAG_NAME
- By.CSS_SELECTOR
- By.XPATH

```
<html>
 <body>
  <p>Are you sure you want to do this?</p>
  <a href="continue.html">Continue</a>
  <a href="cancel.html">Cancel</a>
  <p class="content">Site content goes here.</p>
</body>
<html>
```

By.LINK_TEXT는 \<a> tag의 링크를 대상으로 찾는다. <br>
By.PARTIAL_LINK_TEXT는 요소의 링크가 전달한 링크를 일부분 포함하면 해당 요소가 선택된다.

```
continue_link = driver.find_element(By.LINK_TEXT, 'Continue')
continue_link = driver.find_element(By.PARTIAL_LINK_TEXT, 
'Conti')
content = driver.find_element(By.CSS_SELECTOR, 'p.content')
```

By.XPATH는 매우 강력한 찾기 기능을 제공한다. <br>
웹 페이지 상에서 해당 요소의 절대 경로 (혹은 상대 경로)를 갖고 요소를 찾을 수 있다. <br><br>
**원하는 요소에서 Copy Xpath만 하는 방식으로도 찾을 수 있다.** <br>

<img width="604" alt="스크린샷 2022-03-17 오후 11 59 27" src="https://user-images.githubusercontent.com/76269316/158831953-d7f3296a-e4ec-4446-b54d-a0799f8ddf9b.png">

아래 코드는 구글의 검색창을 XPATH 복사를 통해 선택한 코드이다.


```python
search_box = driver.find_element(By.XPATH, '/html/body/div[1]/div[3]/form/div[1]/div[1]/div[1]/div/div[2]/input')
```

XPATH 작성법은 [링크](https://greeksharifa.github.io/references/2020/10/30/python-selenium-usage/) 참조 <br>

![스크린샷 2022-03-18 오전 12 02 11](https://user-images.githubusercontent.com/76269316/158832291-7982f1f0-f3a2-4d2c-a330-edc48d6dcd84.png)


### 5.Text Input

구글 검색 창을 선택한 상태에서 send_keys(*value) 함수를 통해 키보드 입력을 할 수 있다. <br>


```python
search_box = driver.find_element(By.XPATH, '/html/body/div[1]/div[3]/form/div[1]/div[1]/div[1]/div/div[2]/input')
```


```python
search_box.send_keys('seominseok4834.github.io')
```

send_keys()는 인자값으로 문자열을 받는다. enter 같은 특수 키 입력도 (RETURN = '\ue006')과 같이 문자열로 처리할 수도 있지만 다음과 같이 입력할 수 있다. <br>
경우에 따라 다르지만 enter 키의 경우 Keys.ENTER 또는 Keys.RETURN으로 입력할 수 있다.


```python
from selenium.webdriver.common.keys import Keys

search_box.send_keys(Keys.RETURN)
```

아래는 입력할 수 있는 Keys의 목록이다.

```
class Keys(object):
    """
    Set of special keys codes.
    """

    NULL = '\ue000'
    CANCEL = '\ue001'  # ^break
    HELP = '\ue002'
    BACKSPACE = '\ue003'
    BACK_SPACE = BACKSPACE
    TAB = '\ue004'
    CLEAR = '\ue005'
    RETURN = '\ue006'
    ENTER = '\ue007'
    SHIFT = '\ue008'
    LEFT_SHIFT = SHIFT
    CONTROL = '\ue009'
    LEFT_CONTROL = CONTROL
    ALT = '\ue00a'
    LEFT_ALT = ALT
    PAUSE = '\ue00b'
    ESCAPE = '\ue00c'
    SPACE = '\ue00d'
    PAGE_UP = '\ue00e'
    PAGE_DOWN = '\ue00f'
    END = '\ue010'
    HOME = '\ue011'
    LEFT = '\ue012'
    ARROW_LEFT = LEFT
    UP = '\ue013'
    ARROW_UP = UP
    RIGHT = '\ue014'
    ARROW_RIGHT = RIGHT
    DOWN = '\ue015'
    ARROW_DOWN = DOWN
    INSERT = '\ue016'
    DELETE = '\ue017'
    SEMICOLON = '\ue018'
    EQUALS = '\ue019'

    NUMPAD0 = '\ue01a'  # number pad keys
    NUMPAD1 = '\ue01b'
    NUMPAD2 = '\ue01c'
    NUMPAD3 = '\ue01d'
    NUMPAD4 = '\ue01e'
    NUMPAD5 = '\ue01f'
    NUMPAD6 = '\ue020'
    NUMPAD7 = '\ue021'
    NUMPAD8 = '\ue022'
    NUMPAD9 = '\ue023'
    MULTIPLY = '\ue024'
    ADD = '\ue025'
    SEPARATOR = '\ue026'
    SUBTRACT = '\ue027'
    DECIMAL = '\ue028'
    DIVIDE = '\ue029'

    F1 = '\ue031'  # function  keys
    F2 = '\ue032'
    F3 = '\ue033'
    F4 = '\ue034'
    F5 = '\ue035'
    F6 = '\ue036'
    F7 = '\ue037'
    F8 = '\ue038'
    F9 = '\ue039'
    F10 = '\ue03a'
    F11 = '\ue03b'
    F12 = '\ue03c'

    META = '\ue03d'
    COMMAND = '\ue03d'
```

### 6.Text Clear

입력한 텍스트를 지우는 방법은 Keys.BACKSPACE 또는 Keys.BACK_SPACE를 사용하면 된다. <br>
만약 전체를 지우고 싶다면 선택한 요소에서 clear() 함수를 호출하면 된다.


```python
search_box.clear()
```

### 7.File Upload
파일을 받는 input을 선택한 뒤, send_keys(file_path)를 호출하면 된다.


```python
upload = driver.find_element_by_tag(input)
upload.send_keys(file_path)
```

### 8.Interaction

##### Click

find_element 함수로 요소를 선택한 다음 click() 함수를 호출하면 해당 요소가 클릭된다.


```python
# 위에서 엔터키를 입력해 검색 결과 페이지로 넘어가 버려서 다시 검색 페이지를 다시 로드해줬다.
url = 'https://www.google.com/'
driver.get(url)
```


```python
# 마찬가지로 다시 search_box를 찾아 내 블로그 주소를 입력해줬다.
search_box = driver.find_element(By.XPATH, '/html/body/div[1]/div[3]/form/div[1]/div[1]/div[1]/div/div[2]/input')
search_box.send_keys('seominseok4834.github.io')

search_box.send_keys(Keys.RETURN)
```

위 코드를 실행하면 다음과 같은 페이지에 있을 것이다.

<img width="1624" alt="스크린샷 2022-03-18 오전 10 11 00" src="https://user-images.githubusercontent.com/76269316/158918530-cefcabab-3314-4003-b7b8-49d9c70d9886.png">

여기서 <img width="615" alt="스크린샷 2022-03-18 오전 10 11 56" src="https://user-images.githubusercontent.com/76269316/158918623-3974bc24-dd4f-4655-ad95-af54f12639d7.png">
이 부분을 클릭할 것이다. <br>

command + option + i를 눌러 개발자 모드로 들어간 다음 왼쪽 위의 <img width="33" alt="스크린샷 2022-03-17 오후 9 45 43" src="https://user-images.githubusercontent.com/76269316/158811223-e18be2fb-9c16-4a5a-8eb3-a11ade995716.png">
 버튼을 누르고 웹 페이지의 요소를 클릭하면 해당 코드 부분으로 이동한다.

 ![스크린샷 2022-03-18 오전 10 13 39](https://user-images.githubusercontent.com/76269316/158918800-9678813c-8d65-4945-a8e6-c0dd6b24404f.png)

그런 다음 복사 -> XPath 복사를 클릭해 복사한다. <br>

복사한 뒤 find_element 함수로 해당 요소를 찾아 click() 함수를 호출해 클릭한다.


```python
blog = driver.find_element(By.XPATH, '//*[@id="rso"]/div[1]/div/div[1]/div/a/h3')
blog.click()
```

위 코드를 실행하면 아래처럼 내 블로그에 방문하게 된다.

<img width="1624" alt="스크린샷 2022-03-18 오전 10 17 41" src="https://user-images.githubusercontent.com/76269316/158919083-ee8ec231-436c-498c-8abe-a6c5885bc524.png">


##### Drag and Drop

어떤 동작을 수행하기 위해서는 ActionChains를 사용하면 된다. <br>
source 요소에서 target 요소로 Drag & Drop을 수행하는 코드는 다음과 같다.


```python
from selenium.webdriver import ActionChains

action_chains = ActionChains(driver)
action_chains.drag_and_drop(source, target).perform()
```

##### Window / Frame 이동

최신 웹 페이지에서는 반응형으로 구현하는 경우가 많아 프레임을 잘 사용하지 않지만, 예전에 만들어진 사이트의 경우 frame을 사용한 사이트들이 종종 있다. <br>
이렇게 프레임 안에 들어있는 요소는 find_element 함수를 통해서는 찾을 수 없고, 해당 프레임으로 이동해야 한다.

```
driver.switch_to_frame("frameName")
driver.switch_to_window("windowName")

# frame 내 subframe으로도 접근이 가능하다. 점(.)을 쓰자.
driver.switch_to_frame("frameName.0.child")
```

프레임 밖으로 나가려면 아래 코드를 사용하면 기본 프레임으로 돌아간다.

```
driver.switch_to_default_content()
```

윈도우 이름을 알고 싶다면 다음과 같은 코드에서 target에 해당하는 windowName을 사용하면 된다.

```
<a href="somewhere.html" target="windowName">Click here to open a new window</a>
```

또한 웹 드라이버는 윈도우 리스트에 접근할 수 있으므로 다음과 같이 모든 윈도우를 순회하는 것도 가능하다.

```
for handle in driver.window_handles:
    driver.switch_to_window(handle)
```

##### Alert

브라우저를 사용하다보면 아래와 같이 확인, 취소 같은 경고창이 뜰 때가 있는데, 윈도우나 프레임 뿐만 아니라 경고창으로 이동할 수도 있다.

<img width="1624" alt="스크린샷 2022-03-18 오전 10 40 18" src="https://user-images.githubusercontent.com/76269316/158921159-1bfefe47-d43b-4447-bf9a-68e57e768dcb.png">



```python
alert = driver.switch_to.alert
```

아래 코드를 통해 경고창에서 수락/거절을 누르거나, 경고창의 내용을 출력, 혹은 경고창에 특정 키 입력을 할 수 있다.


```python
from selenium.webdriver.common.alert import Alert

Alert(driver).accept()  # 수락
Alert(driver).dismiss()  # 거절

print(Alert(driver).text)  # 경고창 내용 출력
Alert(driver).send_keys(keysToSend=Keys.ESCAPE)  # 경고창에 키 입력
```

##### JavaScript 코드 실행
driver.execute_script() 함수를 통해 자바 스크립트 코드를 실행할 수 있다.
아래는 Name이 search_box인 요소 값을 query 값으로 변경하는 코드이다.

```
driver.execute_script("document.getElementsByName('id')[0].value=\'"+query+"\'")
```

##### Browser
브라우저 창 다루기

**뒤로가기, 앞으로 가기**


```python
driver.forward()
driver.back()
```

**아래로 내려가기** <br><br>
아래 코드를 실행하면 현재 로드된 웹페이지의 맨 밑으로 내려간다.


```python
driver.execute_script('window.scrollTo(0, document.body.scrollHeight);')
```

**무한 스크롤에서 아래로 내려가기** <br><br>
왓챠피디아 리뷰 페이지는 무한 스크롤이라고 부르는 방식이라 스크롤을 내릴 때마다 새로운 리뷰들이 로드된다. <br>
무한 스크롤의 경우 위 코드를 실행해 현재까지 로드된 맨 아래로 이동한 뒤, 새로운 요소들이 로드되면 다시 맨 아래로 로드한다. <br>
맨 아래로 이동하면서 height 값을 저장한 뒤, 더 이상 height 값이 변하지 않을 때 즉, 스크롤이 끝났을 때 종료한다.


```python
url = 'https://pedia.watcha.com/ko-KR/contents/mOVP23Z/comments'
driver.get(url)

scroll_pane_height = driver.execute_script('return document.documentElement.scrollHeight')

while True:
    driver.execute_script('window.scrollTo(0, document.documentElement.scrollHeight)')
    time.sleep(1)
    new_scroll_pane_height = driver.execute_script('return document.documentElement.scrollHeight')
    print(scroll_pane_height, new_scroll_pane_height)

    if scroll_pane_height == new_scroll_pane_height:
        break

    scroll_pane_height = new_scroll_pane_height
```

    872 981
    981 1847
    1847 2528
    2528 3233
    3233 4274
    4274 5171
    5171 6020
    6020 6020


**브라우저 최소화/최대화**



```python
driver.minimize_window()
driver.maximize_window()
```

**스크린샷 저장**


```python
driver.save_screenshot('screenshot.png')
```




    True



### 9.ActionChains

마우스, 키보드 입력 등 연속 동작 실행


```python
from selenium.webdriver import ActionChains

menu = driver.find_element(By.CSS_SELECTOR, '.nav')
hidden_submenu = driver.find_element(By.CSS_SELECTOR, '.nav #submenu1')

ActionChains(driver).move_to_element(menu).click(hidden_submenu).perform()
```

```
# 위 한 줄은 아래와 같은 동작을 수행한다.
actions = ActionChains(driver)
actions.move_to_element(menu)
actions.click(hidden_submenu)
actions.perform()
```

마우스 클릭, Drag & Drop, 키보드 입력 등을 연속적으로 수행할 수 있다.
- on_element 인자를 받는 함수는 인자가 주어지지 않을 경우 현재 마우스 위치를 기준으로 한다.
- element 인자를 받는 함수는 해당 인자가 주어지지 않으면 현재 선택돼 있는 요소를 기준으로 한다.
- key_down, key_up 함수는 ctrl 등의 키를 누를 때 사용한다.

```
# Ctrl + C
ActionChains(driver).key_down(Keys.CONTROL).send_keys('c').key_up(Keys.CONTROL).perform()
```

<img width="1087" alt="스크린샷 2022-03-18 오전 11 05 40" src="https://user-images.githubusercontent.com/76269316/158923623-41b0c156-3628-4be3-8994-b6b00a6b214f.png">

