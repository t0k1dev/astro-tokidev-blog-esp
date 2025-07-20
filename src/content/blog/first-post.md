---
title: 'Angular 17 | Componentes sin módulos'
description: 'Si bien la característica de Angular que conocemos como standalone components fué presentado el año 2023 como una parte del set de caracteristicas muy nuevas de angular 17.'
pubDate: 'Jul 19 2025'
heroImage: 'https://miro.medium.com/v2/resize:fit:720/format:webp/1*SepPK5_D3yAUvTtsj0HoDg.png'
categories: ['Angular']
authors: ['t0k1dev']
tags: ['Angular', 'Web', 'Development', 'Stand alone', 'components', 'Angular 17']
---


Si bien la característica de Angular que conocemos como standalone components fué presentado el año 2023 como una parte del set de caracteristicas muy nuevas de angular 17.

La verdad es que los standalone components están disponibles de manera estable desde la versión 15 y como dev preview desde la versión 14.

---

## ¿Por qué este artículo?

El 2023 dentro de un meetup de Angular Bolivia, antes de que sea anunciado Angular 17, tuve la oportunidad de hablar por primera vez de stand alone components y como venían a cambiar el juego de los programadores de Angular.

Este tema me llamo mucho la antención desde que lo escuche y justo por eso motivo inicié a prepar una charla sobre esto.

Este artículo, que lo tenía planado desde hace tiempo, es un pequeño resumen de este tema con el objetivo que le sirva y ayuda a cualquier programador que lo este leyendo.

---

## ¿Sigue siendo relevante Angular en 2025?

Angular siempre fue el framework empresarial por defecto para empresas y productos web grandes y de larga duración, por el motivo de la solides y consistencia en en su desarrollo además de tener una gran empresa por detrás que mantiene su desarrollo.

Después de varios años de no sentir mucho progreso entre versión tras versión, en base a muchos comentarios de desarrolladores y en especial tomando en cuenta state of JS, se notaba que muchos programadores que usaban Angular por primera vez sentían que tenia mucha complejidad agregada y una curva inicial de aprendizaje muy alta. Este motivo hacia de que la popularidad del framwork se reduzca a comparación de otras librerías y frameworks.

El 2023, Angular nos sorprendió con la versión 17 que traía un cambio total, entregando un framework mucho más moderno, más flexible y amigable, además de nueva web, nuevo logo y casi se siente incluso como una nueva Etapa de Angular en la web.

Esta nueva versión 17, si bien tiene muchas cosas que resaltar, la funcionalidad de standalone components fue prensentada como parte del nuevo set de cosas nuevas que traía Angular en esta su nueva presentación moderna, flexible y amigable.

---

## ¿Qué es un módulo en Angular?

Probablemente si estas leyendo esto ya eres un programado con experiencia en Angular, pero solo para dar la explicación completa.

En Angular, un módulo es un mecanismo fundamental para organizar la aplicación.Un módulo en Angular es una clase con el decorador `@NgModule` que agrupa componentes, directivas, pipes y otros servicios relacionados.

---

## ¿Qué es un componente standalone?

Los standalone components simplemente son components que no dependen necesariamente de ningún módulo.

Al no depender de ningún módulo: 

**Ventajas:**
- Más sencillos de implementar.  
- Mayor flexibilidad y capacidad de reutilización.  
- Declaración explícita de sus propias importaciones.

No es necesario de que si inicias a usar standalone components en tu proyecto todos los componentes tengan que ser de esta manarea. Los stand alone components son comatibles con otros componentes que tienen módulo lo cual te permite migrar tu aplicación poco a poco en el caso de que lo necesites o tener un proyecto híbrido en el cual tengas algunos componentes standalone y otros con módulos sin ningun problema.

---

## ¿Cómo declarar un componente standalone?

Para declarar un componente de manera standalone debes considerar de agregar la configuración `standalone: true` y además de agregar las importaciones necesarias que necesita el componente.

Aquí viene un ejemplo de un componente básico que es standalone y no necesita ser parte de ningún módulo para poder ser utilizado dentro de nuestra aplicación.

```ts
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'my-component',
  template: `
    <h1>Hello world</h1>
    <input type="text" [(ngModel)]="name" />
  `,
  standalone: true,
  imports: [
    FormsModule
  ]
})
export class StandAloneComponent {
  name: string = ""
}
```

---

## ¿Cómo generar un componete standalone?

en caso de que quieras crear el componente a mano y quieres aumentar la productividad lo que puedes hacer es usar el CLI de angular para generar tus componentes en modo standalone con el siguiente comando:

```bash
ng generate component componentName --flat --standalone` 
```

`ng generate component` simplemente es el comando de toda la vida que nos ayuda a crear componentes.

`--flat` es un flag que nos permite usar nuestro componente y que solo sea en un archivo con la extensión en `.ts` y no 3 en formanto `.html`, `.css` y `.ts` .

`--standalone` este es un flag que nos ayuda a crear los componentes en esta modalida y no necesite ser decalarado en ningún módulo y sea independient.

---

## ¿Cómo iniciar una aplicación de angular con componentes standalone?

En el caso de que quieras trabajar en la migración de los componentes de t aplicación para que todos sean standalone, puedes aprovechar los schematics. Si bien gran parte del proceso de esta migración es casi automática no es perfecta y hay varios pasos de que nos toca arreglar a mano.


```bash
ng generate @angular/core:standalone
```


Este comando nos brindará un prompt de la migración de paso por paso en los que se considerará:

1. Migración de todos los componentes, directivas y pipes a standalone.
2. Se emilinan todos los módulos innecesarios de la aplicación.
3. Se modifica el bootstrap de la aplicación para usar standalone APIs.

---

## ¿Cuales son las ventajas?

- Reducimos todo el boiler plate code de Angular que teniamos que hacer por la creación y definición de Módulos que nos ayuda mucho a que nuestra aplicación sea más simple.

- Reducimos el bundle de nuestra aplicación además de mejorar el performance de la misma.

## Tomar en cuenta

Si te llamo la atención esta nueva funcionalidad de Angular te animo explorarla y ver todas las ventajas que te puede brindar en tu proyecto acutal, y si estas iniciando un proyecto nuevo aún más te sugiero probarlo desde el inicio.

Es importante considerar de que si estamos quitando los módulos del juego, no perdemos la capacidad de hacer y utlizar lazy loading.

Tambié es importante considerar de que si estamos en un proyecto muy grande que use microfrontends es compatible con los standalone components.