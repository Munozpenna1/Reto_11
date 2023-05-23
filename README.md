# Reto_11
# 1. Desarrolle un programa que permita realizar la suma/resta de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.



```
def validar_matrices(matriz1, matriz2):
    # Verificar si las matrices tienen la misma dimensión
    if len(matriz1) != len(matriz2) or len(matriz1[0]) != len(matriz2[0]):
        return False
    else:
        return True

def operar_matrices(matriz1, matriz2, operacion):
    if validar_matrices(matriz1, matriz2):
        filas = len(matriz1)
        columnas = len(matriz1[0])
        resultado = []
        for i in range(filas):
            fila = []
            for j in range(columnas):
                if operacion == "suma":
                    elemento = matriz1[i][j] + matriz2[i][j]
                elif operacion == "resta":
                    elemento = matriz1[i][j] - matriz2[i][j]
                fila.append(elemento)
            resultado.append(fila)
        return resultado
    else:
        return "Las matrices no tienen la misma dimensión. No se puede realizar la operación."

# Solicitar al usuario la cantidad de filas y columnas
filas = int(input("Ingrese el número de filas: "))
columnas = int(input("Ingrese el número de columnas: "))

print("Ingrese los valores de la primera matriz:")
matriz1 = []
for i in range(filas):
    fila = []
    for j in range(columnas):
        valor = float(input("Ingrese el valor para la posición [{}, {}]: ".format(i, j)))
        fila.append(valor)
    matriz1.append(fila)

print("Ingrese los valores de la segunda matriz:")
matriz2 = []
for i in range(filas):
    fila = []
    for j in range(columnas):
        valor = float(input("Ingrese el valor para la posición [{}, {}]: ".format(i, j)))
        fila.append(valor)
    matriz2.append(fila)

print("Operaciones disponibles: suma, resta")
operacion = input("Ingrese la operación que desea realizar: ")

resultado = operar_matrices(matriz1, matriz2, operacion)

if isinstance(resultado, str):
    print(resultado)
else:
    print("El resultado de la {} de matrices es:".format(operacion))
    for fila in resultado:
        print(fila)
```

# 2. Desarrolle un programa que permita realizar el producto de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.



```
def validar_matrices(matriz1, matriz2):
    # Verificar si el número de columnas de la matriz1 coincide con el número de filas de la matriz2
    if len(matriz1[0]) != len(matriz2):
        return False
    else:
        return True

def crear_matriz(filas, columnas):
    # Función para crear una matriz
    matriz = []
    for i in range(filas):
        print("Ingrese los valores de la fila", i)
        fila = []
        for j in range(columnas):
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz

def producto_matrices(matriz1, matriz2):
    # Realiza el producto de dos matrices
    filas_A = len(matriz1)
    columnas_A = len(matriz1[0])
    filas_B = len(matriz2)
    columnas_B = len(matriz2[0])

    # Verificar si las matrices cumplen las condiciones necesarias para el producto
    if columnas_A != filas_B:
        print("No se puede realizar el producto de matrices. Verifique las dimensiones.")
        return None

    # Inicializar matriz de producto con ceros
    matriz_producto = []
    for i in range(filas_A):
        fila = [0] * columnas_B
        matriz_producto.append(fila)

    # Realizar el cálculo del producto de matrices
    for i in range(filas_A):
        for j in range(columnas_B):
            for k in range(columnas_A):
                matriz_producto[i][j] += matriz1[i][k] * matriz2[k][j]

    return matriz_producto


if __name__ == "__main__":
    print("PRODUCTO DE MATRICES")
    print("El número de columnas de la primera matriz debe ser igual al número de filas de la segunda matriz.")

    # Crear matriz A
    print("MATRIZ A")
    filas_A = int(input("Especifique el número de filas de la primera matriz: "))
    columnas_A = int(input("Especifique el número de columnas de la primera matriz: "))
    matrizA = crear_matriz(filas_A, columnas_A)
    for i in range(filas_A):
        print(matrizA[i])

    # Crear matriz B
    print("MATRIZ B")
    filas_B = int(input("Especifique el número de filas de la segunda matriz: "))
    columnas_B = int(input("Especifique el número de columnas de la segunda matriz: "))
    matrizB = crear_matriz(filas_B, columnas_B)
    for i in range(filas_B):
        print(matrizB[i])

    # Realizar el producto de matrices
    matriz_producto = producto_matrices(matrizA, matrizB)
    if matriz_producto:
        print("El producto de matrices es:")
        for i in range(filas_A):
            print(matriz_producto[i])
```
# 3. Desarrolle un programa que permita obtener la matriz transpuesta de una matriz ingresada. El programa debe validar las condiciones necesarias para ejecutar la operación.



```
 def crear_matriz(filas, columnas):
    # Función para crear una matriz
    matriz = []
    for i in range(filas):
        print("Ingrese los valores de la fila", i)
        fila = []
        for j in range(columnas):
            valor = float(input())  # Solicita al usuario ingresar un valor y lo convierte a tipo float
            fila.append(valor)  # Agrega el valor a la fila
        matriz.append(fila)  # Agrega la fila a la matriz
    return matriz

def matriz_transpuesta(matriz):
    # Obtiene la matriz transpuesta de una matriz dada
    filas = len(matriz)  # Obtiene el número de filas de la matriz
    columnas = len(matriz[0])  # Obtiene el número de columnas de la matriz (asumiendo que todas las filas tienen la misma longitud)

    # Crear la matriz transpuesta
    transpuesta = []  # Inicializa una lista vacía para almacenar la matriz transpuesta
    for x in range(columnas):  # Itera sobre las columnas de la matriz original
        lista = []  # Inicializa una lista vacía para cada columna de la matriz transpuesta
        for m in range(filas):  # Itera sobre las filas de la matriz original
            lista.append(matriz[m][x])  # Agrega el elemento en la posición [m][x] a la lista de la columna transpuesta
        transpuesta.append(lista)  # Agrega la lista de la columna transpuesta a la matriz transpuesta

    return transpuesta

if __name__ == "__main__":
    print("OBTENER MATRIZ TRANSPUESTA")
    print("El número de columnas de la matriz transpuesta será igual al número de filas de la matriz original.")

    # Crear matriz
    print("MATRIZ ORIGINAL")
    filas = int(input("Especifique el número de filas de la matriz: "))  # Solicita al usuario ingresar el número de filas de la matriz
    columnas = int(input("Especifique el número de columnas de la matriz: "))  # Solicita al usuario ingresar el número de columnas de la matriz
    matriz = crear_matriz(filas, columnas)  # Crea la matriz llamando a la función crear_matriz y pasando los valores de filas y columnas
    for i in range(filas):
        print(matriz[i])  # Imprime cada fila de la matriz

    # Obtener la matriz transpuesta
    matriz_trans = matriz_transpuesta(matriz)  # Calcula la matriz transpuesta llamando a la función matriz_transpuesta y pasando la matriz original
    print("La matriz transpuesta es:")
    for i in range(columnas):
        print(matriz_trans[i])  # Imprime cada fila de la matriz transpuesta
```

# 4. Desarrollar un programa que sume los elementos de una columna dada de una matriz.



```
def crear_matriz(filas, columnas):
    # Función para crear una matriz
    matriz = []
    for i in range(filas):
        print("Ingrese los valores de la fila", i)
        fila = []
        for j in range(columnas):
            valor = float(input())  # Solicita al usuario ingresar un valor y lo convierte a tipo float
            fila.append(valor)  # Agrega el valor a la fila
        matriz.append(fila)  # Agrega la fila a la matriz
    return matriz

def sumar_columna(matriz, columna):
    # Suma los elementos de una columna dada de una matriz
    suma = 0
    for i in range(len(matriz)):
        suma += matriz[i][columna]  # Suma el elemento en la posición [i][columna] a la suma total
    return suma

if __name__ == "__main__":
    print("SUMA DE ELEMENTOS DE UNA COLUMNA")
    
    # Crear matriz
    print("MATRIZ")
    filas = int(input("Especifique el número de filas de la matriz: "))  # Solicita al usuario ingresar el número de filas de la matriz
    columnas = int(input("Especifique el número de columnas de la matriz: "))  # Solicita al usuario ingresar el número de columnas de la matriz
    matriz = crear_matriz(filas, columnas)  # Crea la matriz llamando a la función crear_matriz y pasando los valores de filas y columnas
    for i in range(filas):
        print(matriz[i])  # Imprime cada fila de la matriz

    # Seleccionar columna para sumar
    columna = int(input("Especifique el número de columna a sumar (0-indexed): "))  # Solicita al usuario ingresar el número de columna a sumar (0-indexed)

    # Validar que la columna exista en la matriz
    if columna >= 0 and columna < columnas:
        # Sumar los elementos de la columna seleccionada
        suma_columna = sumar_columna(matriz, columna)  # Calcula la suma llamando a la función sumar_columna y pasando la matriz y la columna seleccionada
        print("La suma de los elementos de la columna", columna, "es:", suma_columna)
    else:
        print("La columna seleccionada no es válida.")
```

# 5. Desarrollar un programa que sume los elementos de una fila dada de una matriz.



```
def crear_matriz(filas, columnas):
    # Función para crear una matriz
    matriz = []
    for i in range(filas):
        print("Ingrese los valores de la fila", i)
        fila = []
        for j in range(columnas):
            valor = float(input())  # Solicita al usuario ingresar un valor y lo convierte a tipo float
            fila.append(valor)  # Agrega el valor a la fila
        matriz.append(fila)  # Agrega la fila a la matriz
    return matriz

def sumar_fila(matriz, fila):
    # Suma los elementos de una fila dada de una matriz
    suma = sum(matriz[fila])  # Suma los elementos de la fila utilizando la función sum
    return suma

if __name__ == "__main__":
    print("SUMA DE ELEMENTOS DE UNA FILA")
    
    # Crear matriz
    print("MATRIZ")
    filas = int(input("Especifique el número de filas de la matriz: "))  # Solicita al usuario ingresar el número de filas de la matriz
    columnas = int(input("Especifique el número de columnas de la matriz: "))  # Solicita al usuario ingresar el número de columnas de la matriz
    matriz = crear_matriz(filas, columnas)  # Crea la matriz llamando a la función crear_matriz y pasando los valores de filas y columnas
    for i in range(filas):
        print(matriz[i])  # Imprime cada fila de la matriz

    # Seleccionar fila para sumar
    fila = int(input("Especifique el número de fila a sumar (0-indexed): "))  # Solicita al usuario ingresar el número de fila a sumar (0-indexed)

    # Validar que la fila exista en la matriz
    if fila >= 0 and fila < filas:
        # Sumar los elementos de la fila seleccionada
        suma_fila = sumar_fila(matriz, fila)  # Calcula la suma llamando a la función sumar_fila y pasando la matriz y la fila seleccionada
        print("La suma de los elementos de la fila", fila, "es:", suma_fila)
    else:
        print("La fila seleccionada no es válida.")
```

