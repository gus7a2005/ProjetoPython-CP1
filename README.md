# <h1 align="center">Fantasy Game Fórmula E</h1>
A aplicação feita foi desenvolvida através do Python, atrelando estruturas poderosas envolvendo listas, dicionários e funções, além de cálculos matemáticos. Para garantir maior imersão, o usuário é possibilitado a simular corridas e compreender os resultados através de gráficos e mensuração da velocidade total. A aplicação é uma extensão do site desenvolvido através do React.

[Link do Repositório da Aplicação Python](https://github.com/gus7a2005/ProjetoPython-CP1)

[Link do Repositório da Aplicação Web](https://github.com/jota0802/ProjetoFrontEnd-CP1)

[Link do Vídeo explicativo](https://www.youtube.com/watch?v=SjJNHGwZoJ0)

-----------

## Índice 

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Estruturas e Funções Utilizadas](#estruturas-e-funções-utilizadas)
- [Estrutura de Código](#estrutura-de-código)
- [Desenvolvedores](#desenvolvedores)

## Visão Geral
A aplicação concede ao usuário maior proximidade e conexão com a equipe da Fórmula E, usufruindo das simulações para compreender de forma mais abrangente os pilotos que disputam a modalidade, a influência que os climas possuem nas pistas que alocam todo o espetáculo, ainda acumulando pontos para resgatar premiações, envolvendo desde descontos na loja oficial, até um dia acompanhando a corrida presencialmente totalmente de graça. O projeto visa atrair um maior público para essa nova modalidade, que vem crescendo exponencialmente ano após ano.

## Funcionalidades
- **Visualização imersiva dos resultados simulados** - através dos gráficos gerados pela biblioteca Matplotlib.
- **Resultados mostrados de forma específica em cada volta** - através do uso de um dicionário para armazenar essas médias.
- **Ajuste de velocidade feito em tempo real** - por meio de um ajuste através da condição climática na pista, e o uso do random.
- **Conversão de pontuação adquirida** - por meio do desempenho das corridas, e a escolha do usuário em um piloto para vencer.

## Estruturas e Funções Utilizadas
- **Listas**
- **Dicionários**
- **For**
- **Def**
- **Min**
- **If e Else**

## Estrutura de Código
import random
import pandas as pd
import matplotlib.pyplot as plt


# Definição das equipes e pilotos
equipes = {
    "LUCAS DI GRASSI": "ABT CUPRA FORMULA E TEAM",
    "ROBIN FRIJNS": "ENVISION RACING",
    "DAN TICKTUM": "ERT FORMULA E TEAM"
}

pilotos = list(equipes.keys())  # Lista com os nomes dos pilotos

#energia e pontos
energia = 10
pontos = 0


#lista para armazenar velocidades dos pilotos
velo_Lucas = []
velo_Robin = []
velo_Dan = []

# Definindo voltas e condições de corrida
num_voltas = 10  # Número de voltas da corrida
condicoes_climaticas = ["Ensolarado", "Chuvoso", "Nublado", "Nevando"]
condicao_atual = random.choice(condicoes_climaticas)  # Escolhe uma condição climática aleatória dentro da lista
tamanho_circuito = 3  # Tamanho do circuito em km

# Função para simular a velocidade de cada piloto em cada volta
def simular_volta(piloto, velocidades_pilotos):
    # Calcula a distância percorrida em segundos
    distancia_percorrida = ((tamanho_circuito / velocidades_pilotos[piloto]) * 3600)
    return distancia_percorrida  # Retorna o tempo formatado

# Iniciando a simulação
print('BEM-VINDO AO NOSSO FANTASY GAME!!!!!')
print("Durante a corrida de hoje o clima está:", condicao_atual)

# Determina os favorecidos e desfavorecidos com base na condição climática
if condicao_atual == "Ensolarado":
    favorecido = desfavorecido = None
    print("O clima não desfavorece nenhuma equipe!")
    print("\nPontuação de vitória:")
    print("Todos os pilotos: 3 pontos")
elif condicao_atual == "Chuvoso":
    favorecido = "DAN TICKTUM"
    desfavorecido = "LUCAS DI GRASSI"
    print("O clima desfavoreceu a equipe: ABT CUPRA FORMULA E TEAM")
    print("O clima favoreceu a equipe: ERT FORMULA E TEAM")
    print("\nPontuação de vitória:")
    print("LUCAS DI GRASSI (ABT CUPRA FORMULA E TEAM): 6 pontos")
    print("ROBIN FRIJNS (ENVISION RACING): 3 pontos")
    print("DAN TICKTUM (ERT FORMULA E TEAM): 2 pontos")
elif condicao_atual == "Nublado":
    favorecido = "LUCAS DI GRASSI"
    desfavorecido = "ROBIN FRIJNS"
    print("O clima desfavoreceu a equipe: ENVISION RACING")
    print("O clima favoreceu a equipe: ABT CUPRA FORMULA E TEAM")
    print("\nPontuação de vitória:")
    print("LUCAS DI GRASSI (ABT CUPRA FORMULA E TEAM): 2 pontos")
    print("ROBIN FRIJNS (ENVISION RACING): 6 pontos")
    print("DAN TICKTUM (ERT FORMULA E TEAM): 3 pontos")
else:
    favorecido = "ROBIN FRIJNS"
    desfavorecido = "DAN TICKTUM"
    print("O clima desfavoreceu a equipe: ERT FORMULA E TEAM")
    print("O clima favoreceu a equipe: ENVISION RACING")
    print("Pontuação de vitória:")
    print("LUCAS DI GRASSI (ABT CUPRA FORMULA E TEAM): 3 pontos")
    print("ROBIN FRIJNS (ENVISION RACING): 2 pontos")
    print("DAN TICKTUM (ERT FORMULA E TEAM): 6 pontos")

# Exibe os pilotos disponíveis para aposta e suas equipes
print("\nPilotos disponíveis para aposta:")
for piloto, equipe in equipes.items():
    print(f"{piloto} - {equipe}")

#Exibe a energia disponivel e seus pontos
print(f'\nEnergia disponível: {energia}')
print(f'pontos: {pontos}')
print('////////////////////////////////////////////////////////////////////////////////')
# Solicita ao jogador que faça sua aposta
piloto_apostado = input("Em qual piloto você deseja apostar?: ").upper()
energia_apostada = 0

# Dicionário para armazenar o tempo total de cada piloto
tempos_pilotos = {piloto: 0 for piloto in pilotos}

#Determinando o número da corrida
energia = 10

def energia_disponivel(energia, energia_inicial):
  energia = energia_inicial
  return energia

def verifica_energia(energia, energia_gasta):
  if energia_gasta > energia:
    print(f"Você não tem energia suficiente para gastar, seu saldo: {energia}")
    return False
  else:
    energia -= energia_gasta
    print(f"Energia gasta: {energia_gasta}")
    print(f"Energia restante: {energia}")
    return True








# Simulação das voltas da corrida
for volta in range(1, num_voltas + 1):  # O for garante que o range está dentro do número de voltas estipulado
    # Define as velocidades dos pilotos com base na condição climática
    if condicao_atual == "Ensolarado":
        velocidades_pilotos = {
            "LUCAS DI GRASSI": random.randint(150, 322),  # O comando "random.randint" escolhe um valor aleatório entre 150 e 322
            "ROBIN FRIJNS": random.randint(150, 322),
            "DAN TICKTUM": random.randint(150, 322)
        }
    elif condicao_atual == "Chuvoso":
        velocidades_pilotos = {
            "LUCAS DI GRASSI": random.randint(110, 300),
            "ROBIN FRIJNS": random.randint(150, 315),
            "DAN TICKTUM": random.randint(190, 322)
        }
    elif condicao_atual == "Nublado":
        velocidades_pilotos = {
            "LUCAS DI GRASSI": random.randint(175, 322),
            "ROBIN FRIJNS": random.randint(135, 310),
            "DAN TICKTUM": random.randint(150, 315)
        }
    elif condicao_atual == "Nevando":
        velocidades_pilotos = {
            "LUCAS DI GRASSI": random.randint(150, 315),
            "ROBIN FRIJNS": random.randint(190, 322),
            "DAN TICKTUM": random.randint(135, 310)
        }

    print(f"Volta {volta}/{num_voltas}")

    # Calcula o tempo de cada piloto para a volta atual
    for piloto in pilotos:
        tempo_volta = simular_volta(piloto, velocidades_pilotos)
        tempos_pilotos[piloto] += tempo_volta  # Acumula o tempo de cada volta no total de cada piloto

        #Chance de um fast-charging
        chance_fast_charging = random.randint(1,10)
        if chance_fast_charging == 15:
            print(f'//O piloto {piloto} teve que realizar um fast-charging que durou 30 segundos!//')
            tempo_volta += 30
        chance_attack_mode = random.randint(1,10)
        if chance_attack_mode == 10:
            print(f'//O piloto {piloto} ativou o modo ataque e ganhou um boost de velocidade!//')
            tempo_volta -= 15
        #Aumenta a chance de um boost de velocidade para o desfavorecido
        elif piloto == desfavorecido:
            chance_attack_mode = random.randint(1,8)
            if chance_attack_mode == 8:
                print(f'//O piloto {piloto} ativou o modo ataque e ganhou um boost de velocidade!//')
                tempo_volta -= 15

        print(f"{piloto} completou a volta em {tempo_volta:.2f} segundos, velocidade do piloto: {velocidades_pilotos[piloto]} km/h")
        if piloto == 'LUCAS DI GRASSI':
            velo_Lucas.append(velocidades_pilotos[piloto])
        elif piloto == 'ROBIN FRIJNS':
            velo_Robin.append(velocidades_pilotos[piloto])
        else:
            velo_Dan.append(velocidades_pilotos[piloto])
    print("-----------------------------------------------------------")

# Calcula a média de tempo de cada piloto
medias_pilotos = {piloto: tempos_pilotos[piloto] / num_voltas for piloto in pilotos}

# Determina o vencedor com a menor média de tempo
vencedor = min(medias_pilotos, key=medias_pilotos.get)
print("\nRESULTADO FINAL:")
for piloto, media_tempo in medias_pilotos.items():
    print(f"{piloto} teve uma média de {media_tempo:.2f} segundos por volta.")

print(f"\nO vencedor é {vencedor} com a menor média de tempo por volta!")

# Determina o multiplicador com base na condição do clima
if vencedor == piloto_apostado == favorecido:
    # Piloto favorecido ganha e você apostou nele
    multiplicador = 1.2
    energia_apostada -= 2
    energia -= 2
    pontos += 3

elif vencedor == piloto_apostado == desfavorecido:
    # Piloto desfavorecido ganha e você apostou nele
    multiplicador = 2.0
    energia_apostada -= 1
    energia -= 1
    pontos += 6

elif vencedor == piloto_apostado:
    # Piloto nem favorecido nem desfavorecido ganha e você apostou nele
    multiplicador = 1.5
    energia_apostada -= 1
    energia -= 1
    pontos += 2

elif piloto_apostado == favorecido and piloto_apostado != vencedor:
    # Piloto favorecido perde e você apostou nele
    energia_apostada -= 2
    energia -= 2
    pontos += 1

elif piloto_apostado == desfavorecido and piloto_apostado != vencedor:
    # Piloto desfavorecido perde e você apostou nele
    energia_apostada -= 1
    energia -= 1
    pontos += 1

else:
    # Piloto nem favorecido nem desfavorecido perde
    energia_apostada -= 1
    energia -= 1
    pontos += 1

# Calcula o prêmio do jogador
if piloto_apostado == vencedor:
    premio = energia_apostada * multiplicador
    print(f"Parabéns! Você apostou no vencedor {vencedor}!")
    print(f"Seus prêmios são: + {pontos} pontos!")
    print(f'Pontuação atual: {pontos}')
    print(f'Energia gasta: {energia_apostada}')
    print(f'Energia restante: {energia}')
else:
    print(f"Você apostou em {piloto_apostado}, mas o vencedor foi {vencedor}.")
    print("Você ganhou apenas 1 ponto!")
    print(f'Pontuação atual: {pontos}')






    print(f'Energia gasta: {energia_apostada}')
    print(f'Energia restante: {energia}')

lista_premios = [(50, " 10% de desconto em produtos da loja oficial"),
                 (60, "acesso ao conteúdo exclusivo dos bastidores"),
                 (75, "15% de desconto em produtos da loja oficial"),
                 (85, "evento online exclusivo com os pilotos da Fórmula E"),
                 (105, "brinde à sua escolha na loja oficial + 20% de desconto"),
                 (140, "acesso VIP virtual ao paddock durante uma corrida da Fórmula E"),
                 (150, "assinatura anual gratuita ao nosso serviço de streaming para acompanhar as corridas"),
                 (250, "viagem com tudo pago para acompanhar a próxima corrida de Fórmula E")]

print("Com base no seu desempenho, aqui está a tabela de premiação disponibilizada pela equipe da Formula E!")

df_premios = pd.DataFrame(lista_premios, columns=["Pontuação", "Descrição"]).value_counts()
print(df_premios)




df = pd.DataFrame({
    'Lucas': velo_Lucas,
    'Robin': velo_Robin,
    'Dan': velo_Dan
})

# Criando subplots
fig, axs = plt.subplots(3, 1, figsize=(10, 15))

# Gráfico de Lucas
axs[0].plot(df['Lucas'], marker='o', label='Lucas')
axs[0].set_title('Velocidade de Lucas')
axs[0].set_xlabel('Voltas')
axs[0].set_ylabel('Velocidade')
axs[0].grid()

for i in range(len(df)):
    axs[0].text(i, df['Lucas'][i], df['Lucas'][i], ha='center', va='bottom')

# Gráfico de Robin
axs[1].plot(df['Robin'], marker='o', label='Robin', color='orange')
axs[1].set_title('Velocidade de Robin')
axs[1].set_xlabel('Voltas')
axs[1].set_ylabel('Velocidade')
axs[1].grid()
for i in range(len(df)):
    axs[1].text(i, df['Robin'][i], df['Robin'][i], ha='center', va='bottom')

# Gráfico de Dan
axs[2].plot(df['Dan'], marker='o', label='Dan', color='green')
axs[2].set_title('Velocidade de Dan')
axs[2].set_xlabel('Voltas')
axs[2].set_ylabel('Velocidade')
axs[2].grid()
for i in range(len(df)):
    axs[2].text(i, df['Dan'][i], df['Dan'][i], ha='center', va='bottom')

# Ajustando layout
plt.tight_layout()
plt.show()
# tem menu de contexto

# <h1 align="center">Desenvolvedores</h1>

-------

| Dev | Avatar | RM |
| ------------- | ------ | ----- |
| ![](https://img.shields.io/badge/DEV-João-47797a?style=for-the-badge&logo=github) | <a href="https://github.com/jota0802"><img src="https://avatars.githubusercontent.com/u/161319025?v=4" height="50" style="border-radius:30px;"></a> | RM556790 |
| ![](https://img.shields.io/badge/DEV-Yuri-70b2b4?style=for-the-badge&logo=github) | <a href="https://github.com/yurisilpess"><img src="https://avatars.githubusercontent.com/u/99032447?v=4" height="50" style="border-radius:30px;"></a> | RM557475 |
| ![](https://img.shields.io/badge/DEV-Igor-7ca787?style=for-the-badge&logo=github) | <a href="https://github.com/igor-soos"><img src="https://avatars.githubusercontent.com/u/164360059?v=4" height="50" style="border-radius:30px;"></a> | RM556010 |
| ![](https://img.shields.io/badge/DEV-Pietro-537064?style=for-the-badge&logo=github) | <a href="https://github.com/Pic0777"><img src="https://avatars.githubusercontent.com/u/162361580?v=4" height="50" style="border-radius:30px;"></a> | RM557283 |
| ![](https://img.shields.io/badge/DEV-Gustavo-516b58?style=for-the-badge&logo=github) | <a href="https://github.com/gus7a2005"><img src="https://avatars.githubusercontent.com/u/161319479?v=4" height="50" style="border-radius:30px;"></a> | RM556289 |
