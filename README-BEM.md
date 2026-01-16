# README - BEM

**Proyecto:** Tarjeta de perfil  
**Metodología:** BEM (Block Element Modifier)

## Qué es BEM

BEM es una forma de nombrar clases de CSS para que el código quede ordenado y fácil de entender.  
Divide el componente en:

- **Bloque:** el componente completo.
- **Elemento:** una parte interna del bloque.
- **Modificador:** una versión diferente del bloque o del elemento.

## Cómo lo usé en la tarjeta

HTML:

```html
<article class="profile-card">
  <img class="profile-card__image" src="avatar.jpg" alt="Avatar">
  <div class="profile-card__content">
    <h1 class="profile-card__name">John Doe</h1>
    <p class="profile-card__title">CEO & Founder</p>
    <button class="profile-card__button profile-card__button--primary">
      Contactar
    </button>
  </div>
</article>
```

Clases:

- **Bloque:** `profile-card`
- **Elementos:** `profile-card__image`, `profile-card__content`, `profile-card__name`, `profile-card__title`, `profile-card__button`
- **Modificador:** `profile-card__button--primary`

## Por qué me sirvió

- Los nombres de las clases dicen claramente a qué componente pertenecen.
- Evito usar clases genéricas como `.title` o `.button` que se pisan en proyectos grandes.
- Es más fácil mantener y cambiar estilos sin romper otras partes de la página.

## Estructura del proyecto

```
scss/
  main.scss
  abstracts/        // variables, mixins
  base/             // reset, estilos generales
  layout/           // contenedores
  components/       // profile-card con BEM
```

## Compilación

```bash
sass scss/main.scss styles.css
```

## Ejemplo de SCSS con BEM

```scss
.profile-card {
  background-color: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);

  &__image {
    width: 100%;
    height: 280px;
    object-fit: cover;
  }

  &__name {
    font-size: 28px;
    color: #000;
  }

  &__button {
    padding: 12px 24px;
    border: none;

    &--primary {
      background-color: #000;
      color: #fff;
    }
  }
}
```
