# README - SMACSS

**Proyecto:** Tarjeta de perfil  
**Metodología:** SMACSS (Scalable and Modular Architecture for CSS)

## Qué es SMACSS

SMACSS es una forma de organizar los estilos CSS en grupos según su función.  
No cambia tanto los nombres de las clases, sino dónde guardo cada tipo de estilo.

## Grupos que usé

### 1. Base

Estilos generales de la página: reset, tipografía, imágenes.

```scss
// base/_base.scss
* { 
  box-sizing: border-box; 
  margin: 0; 
  padding: 0; 
}

body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f9;
}
```

### 2. Layout

Estructura principal de la página (contenedores y zonas).  
Se usa prefijo `.l-` para identificarlos.

```scss
// layout/_layout.scss
.l-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.l-page-title {
  margin-bottom: 30px;
  text-align: center;
}
```

### 3. Modules (módulos)

Componentes reutilizables, como la tarjeta de perfil.

```scss
// modules/_profile-card.scss
.profile-card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.profile-card-image {
  width: 100%;
  height: 280px;
  object-fit: cover;
}

.profile-card-name {
  font-size: 28px;
}
```

### 4. State (estado)

Estados especiales de los módulos.  
Se usa prefijo `.is-` para identificarlos.

```scss
// state/_state.scss
.is-disabled {
  opacity: 0.6;
  pointer-events: none;
}

.profile-card:hover {
  transform: translateY(-5px);
}
```

### 5. Theme (tema) *(opcional)*

Colores y valores que se pueden reutilizar.

```scss
// theme/_theme.scss
$color-primary: #4F46E5;
$color-bg: #f4f4f9;
```

## Estructura del proyecto

```
scss/
  main.scss
  base/_base.scss
  layout/_layout.scss
  modules/_profile-card.scss
  state/_state.scss
  theme/_theme.scss
```

## Archivo main.scss

Se importa todo en este orden:

```scss
@use 'base/base';
@use 'layout/layout';
@use 'modules/profile-card';
@use 'state/state';
@use 'theme/theme';
```

## Compilación

```bash
sass scss/main.scss styles.css
```

## Por qué me sirvió

- Me ayuda a saber rápido en qué archivo tengo que tocar algo.
- El proyecto se mantiene ordenado cuando agrego más componentes.
- Puedo combinar SMACSS con BEM: uso SMACSS para la organización de carpetas y BEM para los nombres de las clases dentro de cada módulo.

## Prefijos que usa SMACSS

| Prefijo | Uso | Ejemplo |
|---------|-----|---------|
| `.l-` | Layout (estructuras) | `.l-container`, `.l-header` |
| `.is-` | State (estados) | `.is-active`, `.is-disabled` |
| ninguno | Modules (componentes) | `.profile-card`, `.button` |
