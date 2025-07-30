print("-=-=-=-=-=-=-=-=-=-= BANCO BENÍCIO =-=-=-=-=-=-=-=-=-=-")
# Criação das variáveis necessárias
menu = """
[d] Depositar
[s] Sacar
[e] Extrato
[nc] Nova Conta
[lc] Lista de Contas
[nu] Novo Usuário
[q] Sair
=> """
saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3
contas = []
usuarios = {}

while True:
    # Faz com que o menu apareça
    opcao = input(menu)
    # Faz com que a pessoa possa digitar a letra maiúscula a com espaços  
    opcao = opcao.lower().strip()


    def depositar(valor):
        global saldo, extrato

        # Caso a pessoa digite um valor inválido a mensegem abaixo será exibida
        if valor <= 0:
            print("\n[ERRO] Por favor, digite um valor a partir de R$1.00.")

        else:
            saldo = saldo + valor
            #Faz com que todo valor gigitado entre no extrato
            extrato += f"Depósito: R${valor:.2f}\n"
            print("\nDepósito realizado com suscesso!")

    def sacar(*, valor):
        global saldo, extrato, LIMITE_SAQUES

         # Delimita a quantidade de saques 
        if LIMITE_SAQUES <= 0:
            print("\n[ERRO] Limite de saques atingido.")

        else:
            # Delimita o valor do saque
            if valor > 500:
                print("\n[ERRO] Por favor digite um valor até R$500.00")

            # Faz com que só possa ser sacado o que se tem no saldo
            elif valor > saldo:
                print("\n[ERRO] SALDO INSUFICIENTE.")    
            
            else:
                saldo = saldo - valor
                # Faz com que seja adcionado ao extrato  
                extrato += f"Saque: R${valor:.2f}\n"
                # Faz a contagem da quantidade de saques
                LIMITE_SAQUES = LIMITE_SAQUES - 1
                print("\nSaque realizado com suscesso!")

    def mostrar_extrato():
        # Caso não haja nada no extrato a mensagem abaixo será exibida
        if extrato == "":
            print("\nNão foram realizadas movimentações\n")

        else:
            print(f"\n{extrato}" )
            print(f"Saldo: R${saldo:.2f}")

    def encontrar_usuario(cpf):
        return usuarios.get(cpf)

    def criar_conta(cpf):
        usuario = encontrar_usuario(cpf)
        if not usuario:
            print("\n[ERRO] Usuário não encontrado.")
            return
        
        numero_conta = len(contas) + 1
        conta = {
            "agencia": "0001",
            "numero_conta": numero_conta,
            "usuario": usuario
        }
        contas.append(conta)
        print(f"\nConta criada com sucesso! Agência: 0001 | Conta: {numero_conta}")
    
    def criar_usuario(nome, data_nasc, cpf, ende ):
        if cpf in usuarios:
            print("[ERRO] CPF já cadastrado.")
        else:
            usuarios[cpf] = {
                'nome': nome,
                'nata_nasc': data_nasc,
                'endereco': ende
            }
            print("\nConta criada com seucesso!")

    def lista_contas():
        
        if not contas:
            print("\n[ERRO] Nenhuma conta foi criada ainda.\n")
            return

        for conta in contas:
            agencia = conta["agencia"]
            numero = conta["numero_conta"]
            usuario = conta["usuario"]
            
            print(f"\nAgência: {agencia}")
            print(f"Número da Conta: {numero}")
            print(f"Titular: {usuario['nome']}\n")


    # Configuração de depósito
    if opcao == "d":
        print("\n---------- ÁREA DE DEPÓSITO ----------\n")
        depositar(float(input("Qual o valor que será depositado?\nR$")))
        print("\n--------------------------------------\n")

    # Configuração de saque
    elif opcao == "s":
        print("\n---------- ÁREA DE SAQUES ----------\n")
        sacar(valor = float(input("Qual o valor a ser sacado?\nR$")))
        print("\n-------------------------------------\n")

    # Configuração do extrato
    elif opcao == "e":
        print("\n============== EXTRATO ==============")
        mostrar_extrato()
        print("\n=====================================\n")

    # Configuração de novas contas
    elif opcao == "nc":
        print("\n------------ NOVA CONTA -------------\n")
        criar_conta(cpf=input("Digite o seu CPF: ").strip())
        print("\n-------------------------------------\n")
 
    # Configuração da lista de contas
    elif opcao == "lc":
        print("\n-------- CONTAS CADASTRADAS --------\n")
        lista_contas()
        print("\n------------------------------------\n")
 
    # Configuração de novos usuários
    elif opcao == "nu":
        print("\n----------- NOVO USUÁRIO -----------\n")
        criar_usuario(input("Digite seu nome: ").strip(), input("Digite sua data de nascimento: ").strip(), input("Digite seu CPF: ").strip(), input("Digite seu endereço: ").strip())
        print("\n------------------------------------\n")

    # Configuração do encerramento
    elif opcao == "q":
        break

    # Configuração de um digito errado
    else:
        print("[ERRO] Opreração inválida, por favor selecione a operação desejada novamente.")

# No final da operação o texto abaixo será exibido
print("""----------------------------------------------------
             Obrigado pela preferência! 
                     Até logo!
----------------------------------------------------""")
