# teste
teste
import requests
from bs4 import BeautifulSoup

# URL da página
url = "https://books.toscrape.com/"

# Fazendo a requisição para acessar a página
pagina = requests.get(url)
pagina.raise_for_status()  # Lança erro se a requisição falhar

# Parseando o HTML da página
dados_pg = BeautifulSoup(pagina.text, "html.parser")

# Encontrando todos os títulos dos livros
livros = dados_pg.find_all("h3")

# Exibindo os títulos
for livro in livros:
    titulo = livro.find("a")["title"]
    print(titulo)
