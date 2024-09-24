# Creando nuestra primera prueba

En esa sección la idea es poder crear nuestra primera prueba basica, debugear y ejecutar.

Para comenzar con el taller, partiremos desde el proyecto que encontramos en la carpeta [proyecto_base] (agregar_link) y es importante tener instalado y configurado el entorno con los pre-requisitos.

## ¿Que va a tener nuestra prueba?

Lo basico para poder ejecutar:

* Testplan
* Threadgroup
* Controller (no es necesario pero ayuda)
* Request

## Comencemos

Lo primero que vamos a hacer es importar la librería del JMeterDSL 

```
import static us.abstracta.jmeter.javadsl.JmeterDsl.*;
```

### -------

Luego vamos a agregar el Test plan, para esto escribimos testPlan(); dentro de nuestro constructor. Debería quedar de la siguiente manera:

```
  @Test
  public void PrimerTest() throws IOException {
    testPlan();
  }
```

### -------

Dentro del testPlan vamos a agregarle un threadgroup pero antes, prestar atención que cuando comienzas a escribir threadgroup la IDE ya nos da suguerencias e información referentes a las diferentes configuraciones que se le puede settear a este.

A efectos de esta demo usaremos el metodo definido de la siguiente manera: 

```
threadGroup(threads, iterations, children)
```

### -------

Como children podemos especificar de entre muchos elementos, los cuales se muestran a traves de la IDE a modo de documentación de estos. Nosotros buscaremos y seleccionaremos un httpsampler(url) con thread = 1 y iterations = 1. Quedando de la siguiente manera:

```
threadGroup(1, 1, httpsampler(url))
```

Y con esto tendriamos nuestro primera prueba, pero aún no le especificamos que hacer con ese testPlan.

### Debuguear

Si estas acostumbrado a usar JMeter por GUI existe un metodo muy útil para poder ver la misma prueba que estamos escribiendo mediante la GUI de JMeter. Dicho metodo es "showInGui()" agregandolo de esta manera:

```
testPlan(...).showInGui();
```


Otra forma de debugear es agregandole como hijo en el threadgroup el elemento "resultsTreeVisualizer()" de la siguiente manera:

```
@Test
  public void PrimerTest() throws IOException {
    testPlan(threadGroup(1, 1,
        httpSampler("https://myservice") ),
        resultsTreeVisualizer()
    );
  }
```

Esto nos va a permitir ver los pedidos y sus respuestas para comprobar que la automatización se comporta como queremos.

### -----

Hasta aquí tenemos nuestro script, pero ... ¿como lo ejecutamos?. Para esto tenemos el metodo run() que al igual que showInGui() es un metodo del testPlan, por lo que si configuramos nuestra prueba de la siguiente manera:

```
@Test
public void PrimerTest() throws IOException {
  testPlan(threadGroup(1, 1,
      httpSampler("https://myservice") ),
      resultsTreeVisualizer()
  ).run();
}
```

y luego ejecutando desde la terminal el comando "mvn clean test", nuestra prueba va a comenzar junto con la aparición de una GUI mostrando información de los pedidos y sus respectivas respuestas.

### -----

Con esto podemos decir que pudimos ejecutar nuestra primero prueba usando JMeterDSL exitosamente.