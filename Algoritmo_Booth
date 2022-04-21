# Funcion para multiplicar dos numeros binarios con el algoritmo de Booth
def MultiplicacionBinario():

    def Complemento2(n):
        #Invertimos los unos y los ceros (Complemento a1):
        for i in range(len(n)):
            if n[i]==0:
                n[i]=1
            elif n[i]==1:
                n[i]=0

        #Sumamos uno a la derecha (Complemento a2): 
        for i in range(7,-1,-1):                                              #Recorre la lista de derecha a izquierda, empieza en el indice 7, va hasta el indice 0 y decrementa en 1
            if n[i]==0:
                n[i]=1
                break
            elif n[i]==1:
                n[i]=0


    n1=(input("Ingrese el primer numero binario: "))                          #Pide el primer numero
    n2=(input("Ingrese el segundo numero binario: "))                         #Pide el segundo numero

    if n1 == "0" or n2 == "0":
        print("El resultado es 0")

    nl1=list(n1)                                                              #Convierte el numero a una lista
    nl2=list(n2)                                                              #Convierte el numero a una lista
    n1=[int(x) for x in nl1]                                                  #Convierte la lista a una lista int
    n2=[int(x) for x in nl2]                                                  #Convierte la lista a una lista int


    #Para evitar recibir numeros en otras bases
    for i in n1:
        if i != 0 and i != 1:
            print("El numero ingresado no es binario")
            break
    for i in n2:
        if i != 0 and i != 1:
            print("El numero ingresado no es binario")
            break

    #Aumenta los ceros de los numeros para que tengan 8 bits
    while len(n1)!=8:                                                         
        n1.insert(0,0)
    while len(n2)!=8:                                          
        n2.insert(0,0)
    

    Cn1=[0,0,0,0,0,0,0,0]                                                     #Declara la lista para el complemento de n1
    for i in range(8):
        Cn1[i]=n1[i]                                                          #Copia los valores de n1 a la lista Cn1    
    
    Complemento2(Cn1)                                                         #Llama a la funcion Complemento2 para el complemento de n1

    #Declara la matriz de multiplicacion
    matriz=[[0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0,0, 0],                            #A
            [0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0,0, 0],                            #S
            [0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0,0, 0]]                            #P

    for i in range(8):
        matriz[0][i]=n1[i]                                                    #Copia los valores de n1 a la primer fila de la matriz
    for i in range(8):
        matriz[1][i]=Cn1[i]                                                   #Copia los valores de Cn1 a la segunda fila de la matriz
    for i in range(8,16):
        matriz[2][i]=n2[i-8]                                                  #Copia los valores de n2 a la tercera fila de la matriz


    #Empieza el algoritmo 
    for j in range(8):

        if(matriz[2][15] == 0 and matriz[2][16] == 1): # P = P + A

            #Suma de P y A:
            for i in range(16,-1,-1):
                matriz[2][i] = matriz[2][i] + matriz[0][i]                    # Suma los valores de la fila P con la fila A
             
                # Como la suma puede llegar a ser mayor a 1, se hacen dos restricciones para remplazar 2 por 1,0 y 3 por 1,1:
                if matriz[2][i] == 2:
                    matriz[2][i] = 0
                    if i != 0:
                        matriz[2][i-1] = matriz[2][i-1] + 1

                if matriz[2][i] == 3:
                    matriz[2][i] = 1
                    if i != 0:
                        matriz[2][i-1] = matriz[2][i-1] + 1
            

            #Rotación a la derecha de P:
            for i in range(16,-1,-1):
                if i != 0:                                                    # Mueve los valores de la fila P a la derecha, cada posicion copia el valor de su posición a la izquierda
                    matriz[2][i] = matriz[2][i-1]                             # Excepto el bit más a la izquierda
            



        elif(matriz[2][15] == 1 and matriz[2][16] == 0): # P = P + S
            #Suma de P y S:
            for i in range(16,-1,-1):
                matriz[2][i] = matriz[2][i] + matriz[1][i]                    # Suma los valores de la fila P con la fila S
             
                # Como la suma puede llegar a ser mayor a 1, se hacen dos restricciones para remplazar 2 por 1,0 y 3 por 1,1:
                if matriz[2][i] == 2:
                    matriz[2][i] = 0
                    if i != 0:
                        matriz[2][i-1] = matriz[2][i-1] + 1

                if matriz[2][i] == 3:
                    matriz[2][i] = 1
                    if i != 0:
                        matriz[2][i-1] = matriz[2][i-1] + 1
            

            #Rotación a la derecha de P:
            for i in range(16,-1,-1):
                if i != 0:                                                    # Mueve los valores de la fila P a la derecha, cada posicion copia el valor de su posición a la izquierda
                    matriz[2][i] = matriz[2][i-1]                             # Excepto el bit más a la izquierda



        else: # Cuando es 0,0 y 1,1
            #Rotación a la derecha de P:
            for i in range(16,-1,-1):
                if i != 0:                                                    # Mueve los valores de la fila P a la derecha, cada posicion copia el valor de su posición a la izquierda
                    matriz[2][i] = matriz[2][i-1]                             # Excepto el bit más a la izquierda

    #Después de hacer todas las sumas y las rotaciones en la fila P, se hace una última rotación a la derecha de P:
    for i in range(16,-1,-1):
        if i != 0:                                                            # Mueve los valores de la fila P a la derecha, cada posicion copia el valor de su posición a la izquierda
            matriz[2][i] = matriz[2][i-1]                                     # Excepto el bit más a la izquierda

    #Se imprime el resultado final:
    print("El resultado es:")
    for i in range(9,17):
        print(matriz[2][i], end="")
    print('\n ------------------------------------ \n')
    

# Funcion para dividir dos numeros binarios con el algoritmo de Booth
def DivisionBinario(): #Para dividir numeros positivos de 4 bits
    n1=(input("Ingrese el dividendo en binario: "))                             #Pide el primer numero
    n2=(input("Ingrese el divisor en binario: "))                           #Pide el segundo numero

    if n1 == n2:
        print("El resultado es: 1")
    if n1 == "0" or n2 == "0":
        print("No se puede dividir por 0")

    nl1=list(n1)                                                              #Convierte el numero a una lista
    nl2=list(n2)                                                              #Convierte el numero a una lista
    n1=[int(x) for x in nl1]                                                  #Convierte la lista a una lista int
    n2=[int(x) for x in nl2]                                                  #Convierte la lista a una lista int

    #Para evitar recibir numeros en otras bases
    for i in n1:
        if i != 0 and i != 1:
            print("El numero ingresado no es binario")
            break
    for i in n2:
        if i != 0 and i != 1:
            print("El numero ingresado no es binario")
            break

    #Aumenta los ceros de los numeros para que tengan 4 bits
    while len(n1)!=4:                                                         
        n1.insert(0,0)
    while len(n2)!=4:                                          
        n2.insert(0,0)

    A = [0,0,0,0]                                                             #Acumulador
    
    matriz=[[0,0,0,0,0,0,0,0],                                                #A y Q Respectivamente (Acumulador y dividendo)
            [0,0,0,0,0,0,0,0]]                                                #M (Divisor)
    
    #Se llenan las matrices con los numeros ingresados y el acumulador
    for i in range(4):
        matriz[0][i] = A[i]
        matriz[1][i] = n2[i]
    for i in range (4,8):
        matriz[0][i] = n1[i-4]
    
    #Empieza el algoritmo (4 veces para 4 bits)
    for j in range(4):
        #Desplazar a la izquierda el acumulador y el dividendo
        for i in range(8):
            if i != 7:                                                        #Todas las posiciones de la lista, menos la ultima, toman el valor de la posicion siguiente,
                matriz[0][i] = matriz[0][i+1]                                 #Haciendo que se desplacen a la izquierda

        #El siguiente paso es restar A - M y guardar este resultado en A
        for i in range(7,-1,-1):
            matriz[0][i] = matriz[0][i] - matriz[1][i]                        #Esto se hace exactamente igual que la suma pero con el signo de resta XD
            if matriz[0][i] == -1:                                            #Igual que en la suma, los resultados pueden dar diferente de 1 y 0,
                matriz[0][i] = 1                                              #por lo que se corrige esto con condiciones remplazando -1 por 0 y -2 por 1
                if i != 0:
                    matriz[0][i-1] = matriz[0][i-1] - 1
            if matriz[0][i] == -2:
                matriz[0][i] = 0
                if i != 0:
                    matriz[0][i-1] = matriz[0][i-1] - 1

        #El siguiente paso es revisar si A es menor que 0 o no, debido a que cuando el resultado es negativo ested a en complemento a2, seria muy complicado para el programa 
        #saber si es negativo o no (habría que hacer una funcion que pase de a2 a decimal) por ende la forma más facil es:
        # Revisar quien es mayor entre A y M para saber si el resultado de A es menor a 0
        A=matriz[0][0:4]
        M=matriz[1][0:4]
        if A>=M:                                                            #Si A es mayor o igual a M, entonces el resultado es positivo:
            matriz[0][7] = 0                                                #el bit mas a la derecha de Q es 0
            #A = A + M                                                      y se suma A + M a A 
            for i in range(7,-1,-1):
                matriz[0][i] = matriz[0][i] + matriz[1][i]
                if matriz[0][i] == 2:
                    matriz[0][i] = 0
                    if i != 0:
                        matriz[0][i-1] = matriz[0][i-1] + 1
                if matriz[0][i] == 3:
                    matriz[0][i] = 1
                    if i != 0:
                        matriz[0][i-1] = matriz[0][i-1] + 1
        else:                                                               #Si A es menor a M, entonces el resultado es negativo:
            matriz[0][7] = 1                                                #el bit mas a la derecha de Q es 1
    #Repitiendo este proceso 4 veces (o las veces que lacantidad de bits requiera) se llega al resultado final
    #Donde Q es el cociente y A es el residuo
        
    #Se imprime el resultado final:
    print("El resultado es:")
    print("Cociente: ", matriz[0][4:8] , "Residuo:" , matriz[0][0:4])
    print('\n ------------------------------------ \n')
        
    
        



# Menú principal
print("1. Multiplicar dos números binarios con el algoritmo de Booth")
print("2. Dividir dos números binarios con el algoritmo de Booth")
print("3. Salir")


opcion = int(input("\n Ingrese una opción: "))
while opcion != 3:
    if opcion == 1:
        MultiplicacionBinario()
    elif opcion == 2:
        DivisionBinario()
    else:
        print("Opción inválida")
    opcion = int(input("\n Ingrese una opción: "))
