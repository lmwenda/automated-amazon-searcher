import playsound
from gtts import gTTS
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
 
options = Options()

"""
options.add_argument('--headless')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')
"""

driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=options)
driver.get("https://www.amazon.co.uk/")
print(driver.title)
 
def speak(message):
    tts = gTTS(text=message, lang="en")
    filename = "voice.mp3"
    tts.save(filename)
    playsound.playsound(filename)

def get_product():
    product = input("Search for Product on Amazon: ")

    return str(product)

speak(str(driver.title))
product = get_product()


search_box = driver.find_element(by=By.ID, value="twotabsearchtextbox")

search_box.send_keys(product)
search_box.send_keys(Keys.RETURN)

products = driver.find_elements(by=By.CLASS_NAME, value="a-size-medium a-color-base a-text-normal")

for product in products:
    print(product.text)
