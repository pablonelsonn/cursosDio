# cursosDio

 menu = """
 
 [d] Depositar
 [s] Sacar
 [e] Extrato
 [q] Sair
 
   """

 saldo = 0
 limite = 500
 extrato = ''
 numero_saques = 0
 LIMITE_SAQUES = 3
 TAXA_SAQUE = 5

 while True:
    opcao = input(menu).lower()

    if opcao == 'd':
        valor = float(input("Informe o valor a depositar: "))
        saldo += valor
        extrato += f"Depósito: R${valor}\n"
        print(f'Depósito de R${valor} realizado com sucesso!')

    elif opcao == 's':
        if numero_saques < LIMITE_SAQUES:
            valor = float(input("Informe o valor a sacar: "))
            if valor <= (saldo + limite):
                saldo -= valor
                saldo -= TAXA_SAQUE  # Aplicar a taxa de saque
                numero_saques += 1
                extrato += f"Saque: R${valor}\n"
                print(f'Saque de R${valor} realizado com sucesso! Taxa de R${TAXA_SAQUE} aplicada.')
            else:
                print('Saldo insuficiente!')
        else:
            print('Limite de saques atingido!')

    elif opcao == 'e':
        print("Extrato:")
        print(extrato + f"Saldo: R${saldo}")

    elif opcao == 'q':
        print('Saindo do sistema...')
        break

    else:
        print('Opção inválida, por favor escolha novamente uma opção')
