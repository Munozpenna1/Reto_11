# Reto_11
# 1. lista de arreglos para que de un promedio

```
Lista_arreglo= [3.5, 6.7, 1.23, 2.34, 4.567, 34.5, 34.2, 3.98, 3.4] #Proponemos la lista con los numeros separados por una coma

suma = 0 #iniciamos la variable para poder sumar los valores de la lista

for digito in Lista_arreglo: # Utilizamos el ciclo for para que todos los numeros de la lista se sumen
    suma += digito #Inicializamos la variable promedio usando la formula que es la suma de todos lo variables dividida en la cantidad de variables

Promedio= suma / len(Lista_arreglo) # usamos la funcion len para que nos muestre la cantidad de valores que hay en la lista

print("Este es el arreglo:", Promedio) #imprimimos el promedio 
```

# 2. Desarrollar un algoritmo que calcule el producto punto de dos arreglos de números enteros (reales) de igual tamaño.

```def calcular_producto_punto(a, b): #declaramos las variables 
    producto_punto = 0 
    for i in range(len(a)): # usamos el for para que vaya pasando por todos los elementos de las listas y ponemos la lista a como referencia
        producto_punto += a[i] * b[i]
    return producto_punto
#Ponemos los valores de relacion
a = [1, 2, 3, 4, 5]
b = [2, 4, 6, 8, 10]
producto_punto = calcular_producto_punto(a, b) #utilizamos la definicion del calcular_producto_punto
print(producto_punto) #imprimimos el producto punto ()
```

# 3. Hacer un algoritmo que deje al final de un arreglo de números todos los ceros que aparezcan en dicho arreglo.

```def mover_los_numeros_0_al_final(arreglo): #definimos arreglo
    arreglo2 = [] #creamos la lista de arreglo2 para la actualizacion de datos al final
    contador_ceros = 0 #ponemos el contador en 0 
    for i in arreglo: #utilizamos for para recorrer el arreglo
        if i != 0: #verifica si es 0
            arreglo2.append(i)
        else:
            contador_ceros += 1 #Aumenta el valor de contador_ceros en uno para contar este cero.
    arreglo2.extend([0] * contador_ceros) #agrega los 0 al arreglo2
    return arreglo2 #permite volver a ver los 0 al final de arreglo2
arreglo = [1, 0, 2, 0, 3, 0, 4]
arreglo2 = mover_los_numeros_0_al_final(arreglo)
print(arreglo2) #imprime el arreglo 2
```
