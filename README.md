# Semáforos

## funcionamiento.py

Ejemplo sencillo de cómo funciona un semáforo.

## impresoras.py

Vamos a simular que tenemos una serie de `Computadoras` que necesitan imprimir cosas en `Impresoras`. Dentro de la red podemos tener cualquier número de impresoras y computadoras; aunque obviamente en este ejemplo habrá más computadoras que impresoras.

A la implementación que ya está hecha, agregarle semáforos para que las computadoras se queden esperando si no hay impresoras disponibles. Como está ahora, arroja un error al intentar sacar un elemento cuando la lista está vacía. 


## comensales.py

En esta otra simulación tenemos `Comensales`, un `Cocinero` y una determinada cantidad de platos disponibles.

Si un comensal quiere comer y no hay más platos, debería:
1. despertar al `Cocinero` para que los reponga;
1. esperar a que este termine;
1. comer.

Agregar la sincronización necesaria para que el programa dado funcione así. No importa el orden en que comen los comensales, sí importa que no coman cuando no hay más platos. Una vez sincronizado probar de agregar más comensales, debería funcionar igual.

La salida debería verse más o menos así:

```
19:22:57.349 [Comensal 0] - ¡Qué rico! Quedan 2 platos
19:22:57.349 [Comensal 1] - ¡Qué rico! Quedan 1 platos
19:22:57.350 [Comensal 2] - ¡Qué rico! Quedan 0 platos
19:22:57.350 [Cocinero] - Reponiendo los platos...
19:22:57.350 [Comensal 4] - ¡Qué rico! Quedan 2 platos
19:22:57.350 [Comensal 3] - ¡Qué rico! Quedan 1 platos
```
### Comentario

No se puede asegurar que el thread que llamó al cocinero y se queda esperando, sea el primero en recibir un plato cuando el cocinero termina de cocinar. Esto es algo inherente a la concurrencia. Se puede leer de [acá](https://docs.python.org/3.8/library/threading.html#semaphore-objects) del `acquire()`.

## Variantes de comensales.py

Ahora podés probar algunas variantes. Por ejemplo

* Que haya más de un cocinero, compiten por quién cocina primero y solamente uno puede cocinar.
* Que haya más de un cocinero, y pueden cocinar dos a la vez.
* Que el cocinero *agregue* platos antes de que se terminen. (Ahora nunca se va a dar el caso de que un comensal tenga que esperar al cocinero porque no hay más platos).
* La cantidad de comensales que pueden pedir platos al mismo tiempo son 2.
