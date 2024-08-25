
menu1 = str(input("""

Olá 
Seja bem vindo 
ao Banco do Brasil                  
Por favor, Digite seu nome:

"""))
    
menu = f"""
   
    
{menu1}, Selecione a opção desejada
[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair

"""




saldo = 0
numero_saque = 0
extrato = ""
limite = 500
LIMITE_SAQUE = 3

while True:
    opcao = input(menu)
    if opcao == "1":
        valor = float(input("Informe o valor que vai ser depositado: "))
        if valor > 0:
            saldo += valor
            extrato += f"Deposito: R$ {valor:.2f}\n"
    
    elif opcao == "2":
        valor = float(input("Informe o valor que vai ser sacado: "))
       
        excede_saldo = valor > saldo
       
        excedeu_limite = valor > limite
       
        excede_saque = numero_saque > LIMITE_SAQUE
        
        if excede_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite permitido.")

        elif excede_saque:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saque += 1
        
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "3":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "4":
        print("Agrdecemos sua presença, volte sempre!")
        break 
    


    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")





