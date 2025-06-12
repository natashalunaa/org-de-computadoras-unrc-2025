# org-de-computadoras-unrc-2025

Integrantes del grupo: 
- Luna Farias, Natasha. 46226882
- Quiroga, Maira. 44372426
  
Archivos: "P1Guia5" es la máquina, "sumaRPila" es el programa con la subrutina recursiva y "subrutinas3" es el programa con los 3 niveles anidados de subrutinas.

-sumaRPila: programa que toma un número como parámetro y simula la suma gaussiana, es decir por ejemplo ingresamos el 5 y la subrutina va a hacer 5 + 4 + 3 + 2 + 1 = 15, 15 será el resultado que veremos por consola. Debido a la memoria de 256 con la que trabajamos, el número máximo posible para ingresar es el 35.

-subrutinas3: programa que toma 3 números como parámetros y los suma, veremos dos resultados por consola, el de la suma entre el primer y segundo parámetro y el de sumar ese valor con el tercer parámetro. 

-subrutinaSwap: programa que toma 2 números como parámetros y los intercambia, de manera que obtenemos como resultado ambos números en consola tal cual los ingresamos y luego los tenemos en sentido inverso. Por ejemplo si ingreso 13 y 28, como resultado el programa me imprime 13 28 28 13. Se realiza cambio de registros.

Máquina creada con CPUSim versión 4.0.11

Trabajamos con una arquitectura de 16bits, por ende el OPCODE (identificador de operación) será si o si de 4bits. Tenemos dos registros de propósitos generales, A y B, ambos de 16bits cada uno. Contamos con la interfaz de memoria: registro MAR de 10bits para trabajar con direcciones y registro MDR de 16bits para trabajar con datos. IR (resgistro de instrucción) de 16bits, PC (program counter) de 10bits que almacena la próxima instrucción a ejecutar, BP (base pointer) de 10 bits para poder tener una dirección de referencia para acceder a v.locales y a los parámetros, SP (stack pointer) de 10bits para apuntar al tope de la pila. FLAGS de 3 bits (CO = carryOut, HALT bandera del Stop y OF = overflow). 

Memoria RAM con 256 direcciones de 8 bits c/u.
Contamos con 16 instrucciones para trabajar. Tenemos que tener en cuanta en muchos casos con cuál registro trabajo, A = 0, B = 1.
- STOP: detiene la ejecución (prendo el bit de HALT)
- In: ingresar valores por teclado. Hago test para ver en cuál resgistro.
- Out: mostrar valores por pantalla. Hago test para ver en cuál registro. 
- Load: leer valores en la memoria.
- Save: guardar valores en la memoria.
- Add: operación aritmética de suma. Tomamos como operando un registro y una dirección de memoria. Además tenemos que aclarar si queremos realizar la instrucción de manera directa (accedo a la memoria) o inmediata (trabajo con el valor, no la dirección). 
- Sub: operación aritmética de resta. Funciona de manera similar a la suma, en este caso no tomamos en cuenta la diferenciación entre tipo inmediato y directo.
- Jump: "salta", recibe como operando la próxima dirección a ejecutar y modifica el PC con esa dirección. Salta si o si.
- JumpZ: "salta" de igual forma que el Jump, pero en este caso sucede si el registro A es igual a cero. 
- Move: toma dos registros, el primero se considera "destino" y el segundo "origen". Copio el registro de origen en el registro destino.
- Call: lo uso para llamar a una subrutina. Guarda en la pila cuál es la dirección a la que tengo que volver y pongo en el PC la dirección dónde se encuentra la subrutina, entonces cuando termine con la subrutina puedo volver a la dirección pusheada en la pila.
- Ret: me avisa que terminó la ejecución de la subrutina. Vuelvo estableciendo el PC en la dirección que indica el tope de la pila (SP) y la desapilo.
- Push: agrego un elemento a la pila.
- Pop: tomo/ elimino un elemento perteneciente a la pila. Recordando que trabaja de manera que el último en entrar es el primero en salir.
- LoadStack: toma un registro para guardar el valor leído desde la pila. Tenemos en cuanta un valor inmediato (positivo o negativo) para desplazarnos en la pila tomando como referencia el BP.
- SaveStack: toma un registro que tiene el valor a almacenar en la pila y un valor inmediato (positivo o negativo) que indica a qué posición de memoria acceder teniendo en cuenta el BP (guardo variables locales).
