adicionar um arquivo 


def menu(pergunta,min,max):
  x=int(input(pergunta))
  while ((x<min) or (x>max)):
    x=int(input(pergunta))
  return x

def criar(nomeArquivo):
  try:
    a=open(nomeArquivo,'wt+')
    a.close()
  except:
    print('Erro na criação do arquivo')
  else:
    print('Arquivo {} foi criado com sucesso\n'.format(nomeArquivo))

def exi(nomeArquivo):
  try:
    a=open(nomeArquivo,'rt')
    a.close()
  except FileNotFoundError:
    return False
  else:
    return True

def listarArquivo(nomeArquivo):
  try:
    a=open(nomeArquivo,'rt')
  except:
    print('Erro ao ler o arquivo!')
  else:
    print(a.read())
  finally:
    a.close()

def cadastrarJogo(nomeArquivo, nomeJogo,nomeVideoGame):
  try:
    a=open(nomeArquivo,'at')
  except:
    print('Erro ao abrir o arquivo!')
  else:
    a.write('{};{}\n'.format(nomeJogo,nomeVideogame))
  finally:
    a.close()

#Programa principal
arquivo = 'games.txt'
if exi(arquivo):
  print('Arquivo localizado no computador!')
else:
  print('Arquivo inexistente!')
  criar(arquivo)

while True:
  print('Menu')
  print('1-Cadastrar novo item:')
  print('2-Listar cadastros:')
  print('3- Sair...')

  op=menu('Escolha a opção desejada:', 1 , 3)
  if op == 1:
    print('Opção para cadastrar novo item selecionado...\n')
    nomeJogo=input('Nome do jogo:')
    nomeVideogame=input('Nome do Videogame:')
    cadastrarJogo(arquivo,nomeJogo,nomeVideogame)

  elif op == 2:
    print('Opção de listar selecionada...\n')
    listarArquivo(arquivo)
  elif op == 3:
    print('Saindo! Encerrando programa...')
    break