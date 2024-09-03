# Reto 11: Matrices
### Steffy Geraldine Fernández González
## 1.Desarrolle un programa que permita realizar la suma/resta de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.
```python
def sumar_matrices(A,B):
  n = len(A) #filas de las matrices (ambas deben ser iguales)
  m = len(A[0]) #columnas de las matrices 
  C = [] #resultado de la suma
  for i in range(n):#se itera sobre las filas de A y B
    fila = [] #construcción de filas de C
    for j in range(m): #se itera sobre las columnas de A y B
      fila.append(A[i][j]+B[i][j]) #sumar los elementos correspondientes de A y B
    C.append(fila)
  return(C)

def restar_matrices(A,B):
  n = len(A) #filas de las matrices
  m = len(A[0]) #columnas de las matrices
  D = [] #resultado de la resta
  for i in range(n): #se itera sobre las filas
    fila = [] #construcción de filas de c
    for j in range(m): #se itera sobre las columnas
      fila.append(A[i][j]-B[i][j]) #restar los elementos correspondientes de A y B
    D.append(fila)
  return(D)

if __name__ == "__main__":

  filas_A = int(input("Digite el número de filas para la primera matriz ")) #valores ingresados por el usuario
  filas_B = int(input("Digite el número de filas para la segunda matriz "))
  columnas_A = int(input("Digite el número de columnas para la primera matriz "))
  columnas_B = int(input("Digite el número de columnas para la segunda matriz "))
  A =  [] #matrices donde se guardarán lo ingresado
  B = []

  if filas_A == filas_B and columnas_A == columnas_B: #condición para que se pueda hacer la suma y resta entre las dos matrices
    print("Matriz A")
    for i in range(filas_A):
      fila = []
      for j in range(columnas_A):
        fila.append(int(input("Ingrese un elemento para la matriz ")))
      A.append(fila) #cada fila se almacena como una lista dentro de la lista A (matriz)
    print("Matriz B")
    for i in range(filas_B):
      fila = []
      for j in range(columnas_B):
        fila.append(int(input("Ingrese el elemento para la segunda matriz ")))
      B.append(fila) #cada fila se almacena como una lista dentro de la lista B (matriz)
    suma = sumar_matrices(A,B) #llamar a las funciones
    resta = restar_matrices(A,B)
    print("La suma de las matrices es " +str(suma))
    print("La resta de las matrices es " +str(resta))
  else:
    print("Verificar el tamaño de las matrices, deben ser del mismo tamaño para su ejecución")
```
## 2.Desarrolle un programa que permita realizar el producto de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.
```python
def multiplicar_matrices(A,B):
  n = len(A) #filas
  m = len(A[0]) #columnas de A (número de filas de B)
  l = len(B[0]) #columnas de B
  C = [] #matriz resultante del producto

  for i in range(n): #iterar en las filas de A
    fila_c = [] #filas para C
    for j in range(l): #iterar en las columnas de B
      s = 0 #se inicia la suma para el elemento para cada elemento en C
      for k in range(m): #se itera sobre el elemento i de A y sobre la columna j de B
        s += A[i][k]*B[k][j] #multiplicar el elemento en la fila i y columna k dentro de A con el elemento en la fila k y columna j de B, a la vez que se acumulan los valores
      fila_c.append(s) #agregar el resultado a las filas de C
    C.append(fila_c) #agregar las filas de C al arreglo C
  return(C)

if __name__ == "__main__":

  filas_A = int(input("Digite el número de filas para la primera matriz ")) #valores ingresados por el usuario
  filas_B = int(input("Digite el número de filas para la segunda matriz "))
  columnas_A = int(input("Digite el número de columnas para la primera matriz "))
  columnas_B = int(input("Digite el número de columnas para la segunda matriz "))
  A =  [] #matrices donde se guardarán lo ingresado
  B = []
  
  if columnas_A == filas_B: #condición para que se pueda hacer el producto entre las dos matrices
    print("Matriz A")
    for i in range(filas_A):
      fila = []
      for j in range(columnas_A):
        fila.append(int(input("Ingrese un elemento para la matriz ")))
      A.append(fila) #cada fila se almacena como una lista dentro de la lista A (matriz)
    print("Matriz B")
    for i in range(filas_B):
      fila = []
      for j in range(columnas_B):
        fila.append(int(input("Ingrese el elemento para la segunda matriz ")))
      B.append(fila) #cada fila se almacena como una lista dentro de la lista B (matriz)
    multiplicacion = multiplicar_matrices(A,B) #llamar a la función
    print("La multiplicación de las matrices es " +str(multiplicacion))
  else:
    print("Verificar el tamaño de las matrices ")
```
## 3.Desarrolle un programa que permita obtener la matriz transpuesta de una matriz ingresada. El programa debe validar las condiciones necesarias para ejecutar la operación.

```python
def calcular_matriz_transpuesta(A):
  A_T = [] #se crea una lista vacía correspondiente a la transpuesta de la matriz
  n = len(A) #filas
  m = len(A[0]) #columnas
  for i in range(m): #para acceder a los correspondientes indices de las columnas de A
    A_T.append([]) # filas de la transpuesta
    for j in range(n): #para acceder a los correspondientes índices de las filas de A
      A_T[i].append(A[j][i]) #el elemento con posicion j,i en la matriz original, será puesto en la posición i,j dentro de la matriz transpuesta
  return A_T

if __name__ == "__main__":
  filas_A = int(input("Digite el número de filas para la matriz ")) #valores ingresados por el usuario
  columnas_A = int(input("Digite el número de columnas para la matriz "))
  A = [] #se crea el arreglo vacío que será la matriz
  for i in range(filas_A):
    fila = []
    for j in range(columnas_A):
      fila.append(int(input("Ingrese un elemento para la matriz "))) 
    A.append(fila) #cada fila se almacena como una lista dentro de la lista A (matriz)

  transpuesta = calcular_matriz_transpuesta(A) #llamar a la función
  print("La matriz ingresada fue: " +str(A))
  print("y su transpuesta es: " +str(transpuesta))
```
## 4.Desarrollar un programa que sume los elementos de una columna dada de una matriz.
```python
def sumar_elementos_columna(A,columna_indice):
  suma = 0 #se inicia la suma en 0 para ser iterada 
  for i in A: #se recorre cada fila i dentro de la matriz ingresada por el usuario
    suma += i[columna_indice] #se accede al elemento dentro de la columna indicada por el usuario y se itera
  return suma

if __name__ == "__main__":
  filas_A = int(input("Digite el número de filas para la matriz "))
  columnas_A = int(input("Digite el número de columnas para la matriz ")) #valores ingresados por el usuario
  A = [] #se crea el arreglo vacío que será la matriz
  for i in range(filas_A):
    fila = []
    for j in range(columnas_A):
      fila.append(int(input("Ingrese un elemento para la matriz "))) 
    A.append(fila) #cada fila se almacena como una lista dentro de la lista A (matriz)

  columna_indice = int(input("Ingrese el índice de la columna que desea que cuyos elementos sean sumados: ")) #se empieza desde 0 el índice
  suma_columna = sumar_elementos_columna(A,columna_indice) #llamar a la función
  print("La matriz ingresada fue " +str(A))
  print("y la suma de los elementos de la columna correspondiente es: " +str(suma_columna))
```
## 5.Desarrollar un programa que sume los elementos de una fila dada de una matriz.
```python
def sumar_elementos_fila(A,fila_indice):
  suma = 0 # se inicializa la variable suma en 0 para ser iterada
  for i in A[fila_indice]: #se especifica que la iteración sea en la posicion de la fila que el usuario quiere
    suma += i
  return suma

if __name__ == "__main__":
  filas_A = int(input("Digite el número de filas para la matriz "))
  columnas_A = int(input("Digite el número de columnas para la matriz ")) #valores ingresados por el usuario
  A = [] #se crea el arreglo vacío que será la matriz 
  for i in range(filas_A):
    fila = []
    for j in range(columnas_A):
      fila.append(int(input("Ingrese un elemento para la matriz ")))  #cada fila se almacena como una lista dentro de la lista A (matriz)
    A.append(fila)

  fila_indice = int(input("Ingrese el índice de la fila que desea que cuyos elementos sean sumados ")) #se empieza desde 0 el índice
  suma_fila = sumar_elementos_fila(A,fila_indice) #llamar a la función
  print("La matriz ingresada fue " +str(A))
  print("y la suma de los elementos de la fila correspondiente es: " +str(suma_fila))
```
