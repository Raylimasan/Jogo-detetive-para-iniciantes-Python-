# Jogo-detetive-para-iniciantes-Python-
O objetivo do jogo é achar quem foi o comilão que comeu escondido.

import random

#OBS.: Primeiro crie uma lista .txt com nomes de pessoas.
#Começo de jogo (conhecendo o detetive)
def começar():
    print('###############################################')
    print('               ##DETETIVE##          ')
    print('###############################################')
    nome_do_jogador = input("Informe seu nome detetive:")
    print(f'Olá {nome_do_jogador}, que bom que você chegou para descobrir quem comeu os doces da geladeira'
          f' vamos inicia a investigação!')

#Abertura e leitura do arquivo

    arquivo = open("suspeitos.txt", "r")
    palavras = []

    for linha in arquivo:
        linha = linha.strip()
        palavras.append(linha)

    arquivo.close()

#Sorteio do nome da lista .txt
    numero = random.randrange(0, len(palavras))
    palavrasecreta = palavras[numero].upper()

    letrasacertadas = ["_" for letra in palavrasecreta]

#Inicio do jogo, começando a investigação
    enforcou = False
    acertou = False
    erros = 0

    while (not enforcou and not acertou):

        chute = input("Qual letra?")
        chute = chute.strip().upper()

        print("Investigando ...")

#Se o chute esta na palavra secreta(comilão)
        if (chute in palavrasecreta):
            index = 0
            for letra in palavrasecreta:
                if (chute == letra):
                    letrasacertadas[index] = letra
                    print(f'Parabéns detetive {nome_do_jogador}, '
                          f'estamos no caminho certo a letra {chute} é uma pista!')
                index += 1
#Se não estiver na palavra secreta você perde uma chance, você(detetive) tem 6 chances para acerta

        else:
            erros += 1
            print(f'Não desanime detetive {nome_do_jogador}, você esta quase descobrindo!')
        enforcou = erros == 6
        acertou = "_" not in letrasacertadas
        print(letrasacertadas)
        if erros == 6 or acertou:
            print(f'Infelismente o comilão não deixou rastros detetive {nome_do_jogador},  '
              f'na proxima a gente pega ele.')
            para_ou_continua = int(input("Digite (1) se deseja jogar novamente,(2)se quiser encerrar: "))

            if para_ou_continua == 1:
                começar()
            if para_ou_continua == 2:
                print(f'Obrigado por jogar, espero te ver novamente em breve {nome_do_jogador}!')
                break
            if else:
                print('Opção Inválida, vamos iniciar outra investigação para você!')
                começar()




if (__name__ == '__main__'):
    começar()

#Obs.: Tenho pouco mais de uma mês, aceito sugestões de melhorias e dicas nos comentários.
