# Atividade-GitHub-Copilot-DIO_Atualizado
Atividade GitHub Copilot DIO

Passo 1: Planejamento e estrutura do projeto
Objetivo:
Criar um programa simples que, dado o número de um cartão, identifica se ele é Visa, MasterCard, Amex, etc.

Passo 2: Tecnologias e linguagem
Para um projeto simples e fácil de rodar, recomendo Python — é direto e ótimo para lógica de identificação.

Mas se preferir JavaScript (ex: para rodar no navegador ou Node.js), me avise!

Passo 3: Como identificar a bandeira do cartão?
Cada bandeira tem regras para o número do cartão, normalmente usando os primeiros dígitos (BIN/IIN) e o tamanho do número:

Visa: começa com 4, 13 ou 16 dígitos

MasterCard: começa com 51 a 55 ou 2221 a 2720, 16 dígitos

American Express (Amex): começa com 34 ou 37, 15 dígitos

Discover: começa com 6011, 622126–622925, 644–649, ou 65, 16 dígitos

cartao-bandeira/
│
├── main.py              # Código principal do programa
├── README.md            # Documentação do projeto
├── requirements.txt     # (Opcional, caso use libs)
└── images/              # (Opcional, para capturas de tela)


def identificar_bandeira(numero):
    numero = numero.replace(" ", "")  # remove espaços
    if not numero.isdigit():
        return "Número inválido"
    
    if (numero.startswith('4') and len(numero) in [13, 16]):
        return "Visa"
    elif (len(numero) == 16 and (51 <= int(numero[:2]) <= 55 or 2221 <= int(numero[:4]) <= 2720)):
        return "MasterCard"
    elif (len(numero) == 15 and (numero.startswith('34') or numero.startswith('37'))):
        return "American Express"
    elif (len(numero) == 16 and (
          numero.startswith('6011') or
          622126 <= int(numero[:6]) <= 622925 or
          644 <= int(numero[:3]) <= 649 or
          numero.startswith('65'))):
        return "Discover"
    else:
        return "Bandeira não identificada"

def main():
    numero = input("Digite o número do cartão de crédito: ")
    bandeira = identificar_bandeira(numero)
    print(f"Bandeira identificada: {bandeira}")

if __name__ == "__main__":
    main()
