## Importar as bibliotecas primeiramente
from selenium import webdriver
import time
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.keys import Keys

## Navegar ate o whatsapp web

driver = webdriver.Chrome(ChromeDriverManager().install())
driver.get('https://web.whatsapp.com/')
time.sleep(15)

Definir contatos e grupos que serão enviados contatos devem ser escritos igual está salvo na sua agenda e separados por aspas simples e virgulas, exemplo abaixo
contatos = ['contato1', 'contato2', 'grupo1', 'Grupo 02']


### Criando a váriavel mensagem e incluindo a mensagem, abaixo exemplo

mensagem = 'Oi pessoal, desculpem mandar mensagem essa hora, estou testando automação, então quem está enviando é o robô que eu fiz rsrs (tô falando sério)'


### Buscar contatos / grupos

def buscar_contato(contato):
    campo_pesquisa = driver.find_element_by_xpath('//div[contains(@class,"copyable-text selectable-text")]')
    time.sleep(4)
    campo_pesquisa.click()
    campo_pesquisa.send_keys(contato)
    campo_pesquisa.send_keys(Keys.ENTER)



### Função de envio da mensagem

def enviar_mensagem(mensagem):
    campo_mensagem = driver.find_elements_by_xpath('//div[contains(@class,"copyable-text selectable-text")]')
    campo_mensagem[1].click()
    campo_mensagem[1].send_keys(mensagem)
    campo_mensagem[1].send_keys(Keys.ENTER)



### Laço de repetição para buscar os contatos

for contato in contatos:
    buscar_contato(contato)
    enviar_mensagem(mensagem)