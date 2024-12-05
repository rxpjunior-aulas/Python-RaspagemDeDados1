'''
https://www.youtube.com/watch?v=Csmo_ksiY0I
https://www.crummy.com/software/BeautifulSoup/bs4/doc.ptbr/#atributos
https://www.homehost.com.br/blog/tutoriais/tags-html/

RASPAGEM DE DADOS DE SITE DE NOTÍCIAS USANDO BEAUTIFULSOUP4

'''
#Importações necessárias
import requests
from bs4 import BeautifulSoup

#Define de que página a que página do site os dados serão raspados   
paginaInicial = 1
paginaFinal = 3

#Termos que se deseja pesquisar nas noticias
termosDeInteresse =["policia", "militar", "golpe"]

#A lista qre receberá as notícias já filtradas   
listaDeNoticias =[]

#Loop que percorrerá as páginas do site   
while True:
     url = "https://xxxxxxxx.com.br/ultimas/page/"+str(paginaInicial)
     pagina = requests.get(url)
     soup = BeautifulSoup(pagina.text, "html.parser") #A página coletada em texto através do requests é convertida para html
     todosItens = soup.find_all("h2", class_="post-title") #As tags de interesse com as noticias - Usar o Inspecionar do navegador
     if paginaInicial > paginaFinal or "Pagina não encontrada" in soup.title.string: #Itera entre as páginas até o fim um dos termos
        break
     paginaInicial = paginaInicial + 1
     
     #Loop que irá filtrar as noticias a procura dos termos de interesse
     for item in todosItens:
        noticia = {} #Um dicionário com cada notícia
        noticia["titulo"] = item.text
        noticia["link"] = item.a['href']
        aux = noticia["titulo"] 
        for termo in termosDeInteresse:
            if termo.lower() in str(noticia["titulo"]).lower():
                listaDeNoticias.append(noticia)
                break

#Imprime as noticias filtradas
print(len(listaDeNoticias))
for noticia in listaDeNoticias:
   for titulo, link in noticia.items():
       print(f"{titulo} {link}")
