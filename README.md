
Implementando una Lista
=====
---

## IMPORTANTE 
### Antes de comenzar

1. Cree un repositorio en GitHub a partir del template proporcionado e impórtelo a su cuenta de Replit.
   Si no recuerda el procedimiento, revise el [tutorial](https://chartreuse-goal-d5c.notion.site/Instrucciones-para-realizar-los-Labs-301d965dc59e8034b554e1e6a9772615?source=copy_link).

2. El laboratorio **debe desarrollarse íntegramente en su cuenta personal de Replit**, **con el autocompletado basado en IA desactivado**.

   Vea [**AQUI**](https://chartreuse-goal-d5c.notion.site/Como-desactivar-llenado-autom-tico-de-repl-it-31ad965dc59e80b7b05bd02ae7970fdb?source=copy_link) como desactivar el autocompletado.

3. Solo está permitido modificar los archivos `list.c` y `main.c` y no está permitido utilizar comandos Git.

4. **No está permitido copiar bloques de código de fuentes externas**.

5. Para ejecutar los tests, abra la terminal (Shell) en Replit y ejecute:

   ```bash
   bash test.sh
   ```
6. Debe ejecutar los tests **luego de terminar cada ejercicio**.

7. Al finalizar, adjunte en el aula virtual:

   * La URL de su repositorio GitHub (con los cambios actualizados).
   * El *join link* de su proyecto en Replit.
   * Si utilizó IA como herramienta de apoyo conceptual: enlace a la conversación completa **en un único chat**.

### 🤖 Sobre el uso de IA generativa

Se permite el uso de IA generativa únicamente como apoyo conceptual.

Está permitido:

* Solicitar explicaciones sobre conceptos del lenguaje C.
* Consultar el significado de errores o advertencias del compilador.
* Pedir orientación general **sin solicitar código**.

No está permitido:

* Pedir la solución completa o parcial de los ejercicios.
* Solicitar generación, corrección o reescritura del código del laboratorio.
* **Copiar o utilizar código generado por IA**.

Si utiliza herramientas de IA durante el laboratorio, debe:

* **Mantener la conversación completa en un único chat**.
* Adjuntar el enlace o la transcripción completa de dicha conversación junto con la entrega a través del aula virtual.

**Ejemplo de uso permitido (caso límite):**

Un estudiante puede compartir un fragmento de su propio código junto con el mensaje de error y preguntar:

> “Tengo este código y aparece un `segmentation fault`. ¿Qué causas comunes podrían producir este error? **No me des la solución ni el código corregido; solo explícame en palabras qué podría estar fallando.**”

---

# ACTIVIDAD

En este laboratorio implementaremos una **lista**. Para ello usaremos la siguiente estructura (lista enlazada doble):

````c
typedef struct Node Node;

struct Node {
    void * data; // Puntero al dato
    Node * next; // Puntero al siguiente nodo
    Node * prev; // Puntero al nodo previo
};

typedef struct {
    Node * head; // Puntero al primer elemento
    Node * tail; // Puntero al ultimo elemento
    Node * current; // Puntero para poder recorrer la lista
} List;
````

Si tiene dudas o no sabe como funciona una lista enlazada, puede ver [esta presentación](https://docs.google.com/presentation/d/1ywdRlclnyEt5j02rHXF1nC_3oF0RJcuz2U12qPuv5N4/edit), revisar [este libro](https://edutechlearners.com/download/Introduction_to_algorithms-3rd%20Edition.pdf), buscar en internet o preguntar.

Ejercicios
----

1. Programe la función `List* createList()`, la cual retorna el puntero del tipo de dato `List` con sus valores inicializados en NULL.
> Recuerda reservar memoria al puntero usando malloc o calloc.

2. Programe las funciones `void * firstList(List * list)` y `void * nextList(List * list)`. 
   * La primera retorna el dato del primer nodo de la lista (`head`) y actualiza el current para que apunte a ese nodo. 
   * La segunda función retorna el dato del nodo a continuación del current y actualiza el current para que apunte a ese nodo.

3. Programe las funciones `void * lastList(List * list)` y `void * prevList(List * list)`.
   * La primera retorna el dato del último elemento en la lista y actualiza el current al nodo correspondiente. 
   * La segunda función retorna el dato del nodo anterior a current y actualiza el current para que apunte a ese nodo.

4. Programe la función `void pushFront(List * list, void * data)`, la cual agrega un dato al comienzo de la lista. 
> Puede utilizar la función `Node* createNode(void * data)` la cual crea, incializa y retorna un nodo con el dato correspondiente. 

5. Programe la función `void pushCurrent(List * list, void* data)`, la cual agrega un dato a continuación del nodo apuntado por `list->current`.

6. Programe la función `void* popCurrent(List * list)`, la cual elimina el nodo que está en la posición del current de la lista enlazada, y además retorna el **dato** del nodo eliminado.
> **Nota**: El current debe quedar apuntando al nodo siguiente del eliminado.

Las funciones `pushBack`, `popFront` y `popBack` se pueden implementar usando `popCurrent` y `pushCurrent` (búsquelas en el código).

### Por lo tanto, ya tiene implementado su primer TDA!

----

### Pruebe su implementación

Revise el ejemplo en el archivo `main.c`.

Luego para compilar y ejecutar:

    gcc main.c list.c -o main
    ./main 


