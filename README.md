import pyautogui as py
import time 
import pandas as pd
py.PAUSE = 0.3

#Abrir o navegador 
py.press("win")
py.write("chrome")
py.press("enter")
time.sleep(3)

#Acessar o site 
site = "https://dlp.hashtagtreinamentos.com/python/intensivao/login"
py.write(site)
py.press("enter")
time.sleep(3)

#Digitar o login
py.click(x=815, y=529)
py.write("zabotte34@gmail.com")

#Aperta o Tab para digitar a senha
#py.press("tab")
py.click(x=810, y=664)
py.write("Senha123")


#Aperta o Tab para realizar o login
#py.press("tab")
py.click(x=961, y=749)
#py.press('enter')
time.sleep(3)

#Importar a base de dados


tabela = pd.read_csv('produtos.csv')


#Cadastrar um produto
for linha in tabela.index:
    #Cadastrar código
    py.click(x=996, y=401)
    codigo = tabela.loc[linha, 'codigo']
    py.write(codigo)

    #Cadastrar Marcar
    py.press('tab')
    marca = tabela.loc[linha, 'marca']
    py.write(marca)

    #Cadastrar Tipo do produto
    py.press('tab')
    tipo = tabela.loc[linha, 'tipo']
    py.write(tipo)

    #Cadastrar a Categoria
    py.press('tab')
    categoria = str(tabela.loc[linha,'categoria'])
    py.write(categoria)

    #Cadastrar o preço unico
    py.press('tab')
    preco_unico = str(tabela.loc[linha,'preco_unitario'])
    py.write(preco_unico)

    #Cadastar o Custo
    py.press('tab')
    custo = str(tabela.loc[linha,'custo'])
    py.write(custo)

    #Cadastrar Observação
    py.press('tab')
    obs = tabela.loc[linha, "obs"]
    if not pd.isna(obs):
        py.write(str(tabela.loc[linha, "obs"]))

    #Aperta Enviar
    py.press("tab")
    py.press("enter")

    #Volta para o Inicio da página
    py.scroll(10000) #-> Define roda o scroll do mause tanto pra baixo quanto para cima 
    #| Usando um valor muito alto eu posso subir até o topo da página

#nan -> valor vazio 
