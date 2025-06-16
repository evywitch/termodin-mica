# termodin-mica
trabalho do curso técnico de uma calculadora termodinâmica em python
termodinamica.py
import math

print("=== SISTEMA DE FÍSICA - 2º BIMESTRE ===")
print("Escolha o tema: ")
print("1. 1ª Lei da Termodinâmica")
print("2. Ciclos Termoniâmicos")
print("3. Calores Espécíficos dos Gases Perfeitos")
print("4. Máquinas Térmicas e 2ª Lei da Termodinâmica")
print("5. Ciclo de Carnot")
print("6. Refrigeradores")
print("7. Ondas")
print("0. Sair")

while True:
    tema = input("\nDigite o número do tema: ")
    if tema == "0":
        print("Encerrando o programa...")
        break
    elif tema== "1":
        print("\n=== 1ª LEI DA TERMODINÂMICA ===")
        print("ΔU = Q - W")
        print("1. Calcule variação de energia interna")
        print("2. Calcular calor trocado")
        print("3. Calcular trabalho realizado")

        opcao = input("Escolha o cálculo: ")
        
        if opcao=="1":
            Q = float(input("Calor trocado (J): "))
            W = float(input("Trabalho realizado (J): "))
            delta_U = Q - W
            print(f"\nVariação de energia interna(ΔU) = {delta_U} J")
            if delta_U > 0:
                print("A energia interna do sistema aumentou.")
            elif delta_U < 0:
                print("A energia interna do sistema diminuiu.")
            else:
                print("A energia interna do sistema permaneceu constante.")

        elif opcao == "2":
            delta_U = float(input("Variação de energia (J): "))
            W = float(input("Trabalho realizado (J) "))
            Q = delta_U + W 
            print(f"\nCalor trocado (Q) = {Q} J")
            if Q > 0:
                print("O sistema absorveu calor.")
            elif Q < 0:
                print("O sistema liberou calor.")
        
        elif opcao == 3:
            Q = float(input("Calor trocado (J): "))
            delta_U = float(input("Variação de energia interna (J): "))
            W = Q - delta_U
            print(f"\nTrabalho realizado (W) = {W} J")
            if W > 0:
                print("O sistema realizou trabalho sobre o ambiente.")
            elif W < 0:
                print("O ambiente realizou trabalho sobre o sistema.")
    if tema == "2":
        print("\n=== CICLOS TERMODINÂMICOS ===")
        print("1. Trabalho no ciclo (Área do ciclo)")
        print("2. Rendimento do ciclo")

        opcao = input("Escolha o cálculo: ")

        if opcao == "1":
            print("\nDigite os valores do ciclo no diagrama P x V")
            P_max = float(input("Pressão máxima (Pa): "))
            P_min = float(input("Pressão mínima (Pa): "))
            V_max = float(input("Volume máximo (m³): "))
            V_min = float(input("Volume mínimo (m³): "))
            W = (P_max - P_min) * (V_max - V_min)
            print(f"\nTrabalho no ciclo = {W} J")
    elif opcao == "2":
        Q_abs = float(input("Calor absorvido (J): "))
        Q_libera = float(input("Calor  liberado (J): "))
        rendimento = (Q_abs - Q_libera) / Q_abs
        print(f"\nRendimento do ciclo = {rendimento:.2%}")
    
    elif tema == "3":
        print("\n=== CALORES ESPECÍFICOS DOS GAZES PERFEITOS===")
        print("1. Calor específicos a volume constante (Cv)")
        print("2. Calor específico a pressão contante (Cp)")
        print("3. Relação entre cp e Cv (γ = Cp/Cv)")

        opcao = input("Escolha o cálculo: ")
        R = 8.314

        if opcao == "1":
            graus_liberdade = int(input("Graus de liberdade do gás (1-3): "))
            Cv = ((graus_liberdade / 2) + 1) * R
            print(f"\nCv = {Cv} J/(mol·K)")

        elif opcao == "2":
            graus_liberdade = int(input("Graus de liberdade do gás (1-3): "))
            Cp = ((graus_liberdade / 2) + 1) * R
            print(f"\nCp = {Cp} J/(mol·K)")

        elif opcao == "3":
            graus_liberdade = int(input("Graus de liberdade do gás(1-3): "))
            gamma = ((graus_liberdade / 2)+ 1) / (graus_liberdade / 2)
            print(f"\nγ  = Cp/Cv = {gamma: .4f}")

    elif tema =="4":
        print("\n=== MÁQUINAS TÉRMICAS E 2ª LEI ===")
        print("1. Rendimento da máquina térmica")
        print("2. Calor rejeitado para a fonte fria")

        opcao = input("Escolha o cálculo: ")

        if opcao == "1":
            Q_quente = float(input("Calor absorvido da fonte quente (J): "))
            Q_frio = float(input("Calor rejeitado para fonte fria (J): "))
            rendimento = (Q_quente - Q_frio)/ Q_quente
            print(f"\nRendimento = {rendimento:.2%}")

        elif opcao == "2":
            Q_quente = float(input("Calor absorvido da fonte quente (J): "))
            rendimento = float(input("Rendimento da máquina (decimal): "))
            Q_frio = Q_quente * (1 - rendimento)
            print(f"\nCalor rejeitado = {Q_frio} J")

    elif tema == "5":
                print("\n=== CICLO DE CARNOT ===")
                t_quente=float(input("Temperatura da fonte fria (K): "))
                T_frio=float(input("Temperatura de fonte fria (K): "))
                rendimento= 1 - (T_frio/t_quente)
                print(f"\nRendimento de carnot = {rendimento:.2%}")

    elif tema == "6":
                print("\n=== REFRIGERADORES ===")
                print("1. Coeficiente de desempenho (COP)")
                print("2. calor removido da fonte fria")

                opcao= input("escolha o cálculo")

                if opcao =="1":
                    T_frio = float(input("Temperatura da fonte fria (K): "))
                    t_quente = float(input("Temperatura da fonte quente (K): "))
                    COP = T_frio / (t_quente - T_frio)
                    print(f"\nCOP = {COP:.2f}")

                elif opcao == "2":
                    W = float(input("Trabalho realizado (J): "))
                    COP = float(input("Coeficiente de desempenho (COP): "))
                    Q_frio = COP * W
                    print(f"\nCalor removido = {Q_frio} J")

    elif tema == "7":
        print("\n=== ONDAS ===")
        print("1. Equação fundamental da ondulatória")
        print("2. Energia transportada por uma onda")

        opcao=input("Escolha o cálculo")

        if opcao =="1":
            print("\nEquação: v = λ.f")
            print("1. Calcular velocidade da propagação")
            print("2. Calcular comprimento de onda")
            print("Calcular frequência")

            sub_opcao=input("Escolha: ")

            if sub_opcao =="1":
                lambd = float(input("Comprimento de onda (m)"))
                f = float(input("Frequência (Hz): "))
                v= lambd * f
                print(f"\nVelocidade de progação = {v} m/s")

            elif sub_opcao =="2":
                v = float(input("Velocidade de progação (m/s): "))
                f = float(input("frequência (Hz): "))
                lambd= v/ f
                print(f"\nComprimento de onda = {lambd} m")

            elif sub_opcao == "3":
                v = float (input("Velocidade de propagação (m/s): "))
                lambd= float(input("Comprimento de onda (m): "))
                f = v / lambd
                print(f"\nFrequência = {f} Hz")

        elif opcao == "2":
            A = float(input("Amplitude da onda (m): "))
            f = float(input("Frequência (Hz): "))
            rho = float(input("Densidade linear (kg/m): "))
            v = float(input("Velocidade de propagação (m/s): "))
            E = 2 * math.pi**2 * rho * v * f**2 * A**2
            print(f"\nEnergia transportada = {E} J/m")

        else:
            print("opção inválida! Digite um número de 0 a 7.")
