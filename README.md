# FRANKIE

**F**orward-kinematics **R**obot **A**rm **N**avigation **K**it for **I**nteractive **E**ducation

Simulador del algoritmo de **Denavit-Hartenberg** para la enseñanza de la cinemática
directa de robots manipuladores. Se ejecuta íntegramente en el navegador, sin
instalación, sin licencias y sin servicios externos.

<h1>[Abrir el simulador](https://cloudshadowforce.github.io/frankie/)</h1>

<!--<p align="center">
  <a href="https://cloudshadowforce.github.io/frankie/">
    <img src="assets/abrir-simulador.svg" alt="Abrir el simulador" width="260">
  </a>
</p>

<p align="center">
  <a href="https://cloudshadowforce.github.io/frankie/"><b>https://cloudshadowforce.github.io/frankie/</b></a><br>
  <sub>Se ejecuta en el navegador. Sin instalación, sin registro y sin coste.</sub>
</p>-->

---

## Qué hace

Carga una tabla de parámetros D-H, construye el robot en tres dimensiones y muestra en
tiempo real la posición y la orientación del extremo conforme se mueven las
articulaciones.

- Seis modelos precargados: ABB IRB 4600, KUKA LBR iiwa, Schunk LWA 4P y tres
  configuraciones conceptuales con pares prismáticos
- Tres vías de carga de la tabla: modelo predefinido, escritura directa o importación de
  un fichero de texto
- Validación sintáctica que **identifica la fila errónea** en lugar de fallar en silencio
- Lectura simultánea de posición y orientación, con conmutación entre radianes y grados
- Copia del resultado al portapapeles
- Sistemas de referencia de la base y del extremo, estela de la trayectoria y resaltado de
  la articulación que se manipula
- Control táctil multipunto, diseño adaptable a móvil y tableta, temas claro y oscuro

## Formato de la tabla D-H

Una fila por articulación, cinco columnas separadas por espacios, comas o puntos y coma:

```
a   alpha(°)   d   theta(°)   tipo
```

donde `tipo` vale **1** para articulación de rotación y **2** para prismática.

Ejemplo, ABB IRB 4600:

```
0.175 -90 0.495 0 1
1.095 0 0 -90 1
0.175 -90 0 0 1
0 90 1.2305 0 1
0 90 0 180 1
0 0 0.085 0 1
```

En la carpeta [`modelos/`](modelos/) están los seis modelos como ficheros de texto, listos
para importar.

> **Nota sobre los desfases articulares.** En el IRB 4600, las articulaciones 2 y 5
> incorporan desfases de −90° y +180°. En la columna θ hay que escribir `q + desfase`, no
> `q` directamente.

## Uso sin conexión

Descarga `index.html` y `three.min.js` en la misma carpeta y abre el primero con
cualquier navegador. No necesita servidor.

## Convención empleada

Convención de Denavit-Hartenberg estándar. La matriz de cada eslabón se compone como
`Rot(z,θ) · Trasl(z,d) · Trasl(x,a) · Rot(x,α)`, y la orientación del extremo se expresa en
**ángulos de Euler XYZ**.

## Verificación

El núcleo de cálculo se ha contrastado con la resolución manual mediante matrices de
transformación homogénea y con el modelo docente previo, sobre cuatro configuraciones del
ABB IRB 4600, con coincidencia en las cuatro cifras decimales mostradas.

## Origen

Desarrollado como Trabajo Fin de Máster del Máster Interuniversitario en Representación y
Diseño en Ingeniería y Arquitectura de la **Universidad de Almería**.

Toma como antecedente el simulador **RobotFKS** de la asignatura Diseño de Robótica
Industrial, escrito en VPython sobre GlowScript.

## Licencia

[MIT](LICENSE) — Copyright © 2026 Elena Garrido Sánchez.

Incluye una copia de [Three.js](https://threejs.org) r128, también bajo licencia MIT.
Ver [NOTICE.md](NOTICE.md).

## Cómo citar

Ver [`CITATION.cff`](CITATION.cff), o usar el botón *Cite this repository* de GitHub.
