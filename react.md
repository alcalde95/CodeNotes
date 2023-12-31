# Diccionario de React  

- [Diccionario de React](#diccionario-de-react)
  - [Components](#components)
  - [Tipos de fuentes](#tipos-de-fuentes)
  - [Props tips](#props-tips)
    - [Boolean Prop](#boolean-prop)
    - [**Qué son los children**?](#qué-son-los-children)
    - [Prop default value](#prop-default-value)
  - [Tips](#tips)
  - [Componente vs Elementos](#componente-vs-elementos)
  - [Malas prácticas](#malas-prácticas)
  - [Hooks](#hooks)
    - [useState()](#usestate)
    - [useEffect()](#useeffect)
  - [Imperativo vs Declarativo](#imperativo-vs-declarativo)
  - [Pasar de desarrollo a producción y hacer deploy](#pasar-de-desarrollo-a-producción-y-hacer-deploy)
  - [Modo producción](#modo-producción)
    - [Despliegue](#despliegue)

## Components

Los nombres de los componentes utilizan PascalCase

## Tipos de fuentes

- ### PascalCase

Se usan en los nombres de los componentes. Esto es debido a que es la única forma que tiene react de diferenciar entre etiquetas html y componentes.
Si se pone un nombre de un componente en minúscula, react no entenderá que es un componente y por lo tanto no lo renderizará correctamente,
los renderizará como elementos html.

- ### camelCase

- ### snake_case

- ### kebab-case

## Props tips

> [!IMPORTANT]
**LAS PROPS SON INMUTABLES**
>
Otro important
> [!IMPORTANT]
 **Si inicializas un valor de un componente utilizando un prop, si ese prop cambia, el valor del componente no se modificará debido a que el prop se usa para inicializarlo.**
>
### Boolean Prop

Si queiremos pasarle un boolean a un componente, por ejemplo :

```js
//el componente TwitterFollowCard recibe como parámetros username,isFollowing(boolean)

<TwitterFollowCard isFollowing userName = "Midudev" />;

```

Al paarle isFollowing, el componente lo recibirá como un true. En caso de que queramos  
que sea false se le pasaría como isFollowing = {false}

### **Qué son los children**?

Si tenemos la siguiente estructura:

```js

<div>
    <BodyComponent>
        Hola <-- Este hola sería el children de BodyCOmponent
    </BodyComponent>
</div>
```

Desde el componente, se recibiría como prop :  

```js
export function BodyComponent ({ children , (resto de elementos)}) {
    //
}
```

Este children que se pasa como props sería, en este caso, "hola". Se podría acceder a él mediante {children}, evaluando childre. En children se puede tener tanto un div como un component como otros elementos.  

### Prop default value

Si tenemos la siguiente estructura:

```js
export function BodyComponent ({ userName , age, isFollowing}) {
    //
}
```

Si queremos poner un valor por defecto a un prop, se puede realizar de la siguiente manera:

```js
export function BodyComponent ({ userName , age = 50, isFollowing}) {
    //
}
```

Con ```age = 50``` le indicamos que el valor predeterminado de age es 50 en caso de que age sea undefined

## Tips

- Para evauar un elemento, por ejemplo, un parámetro de una url, se puede hacer de dos formas:

```js
//utilozando una variable
const imageSrc = `https://unavatar.io/${username}`;
<img src = {imageSrc}/>

//o evaluando directamente en el src

<img src = {`https://unavatar.io/${username}`}/>;

```

- Comentarios dentro del return : { /\* comentaio \*/ }

## Componente vs Elementos

Un componente es una factoría de elementos. Un componente es una función que al ejecutarla
te devuelve un elemento.
Los elementos son los que renderiza react

## Malas prácticas

- **Modificar una prop**. Nunca modifiques una prop. So necesitas cambiar algo, crea una variable nueva. **Las props son inmutables**
-  

## Hooks

> [!IMPORTANT]
Los hooks no se pueden meter en if's, es decir, debes controlar tú dentro de estes lo que quieres que ocurra. No puedes hacer, por ejemplo:

```js
if(enable){
  useEffect(.....)
}
```

### useState()

- useState sólo se inicializa una vez, es decir, el siguiente código sólo se ejecuta una vez:
  
```js
const [isFollowing,setIsFollowing] = useState(false)
```

- Este código sólo se ejecuta una vez, incluso si se re-renderiza el componente  

### useEffect()

- Es un hook que nos permite ejecutar código arbitrario (arbitrario = el que tu indiques ) cuando el componente se monta en el DOM y cada vez que cambian las dependencias que nosotros le indicamos.Uso:

```js
useEffect(codeToExecute,listOfDependences)

useEffect(() => { 
  //como mínimo se ejeutará una vez
  console.log("código a ejecutar" )
}[])
//El segundo parámetro es opcional. Si no le pasas nada, se ejecutará el código cada vez que se renderice nuestro componente
//Si se le pasa un array vacío se ejecuta sólo una vez, cuando se renderiza por primera vez

```

- useEffect también te permite devolver una función. Esta función se ejecutará cada vez que alguna dependencia cambie o cuando se desmonta el componente.Ej:

```js
useEffect({

  //....

return () =>{
  window.removeEventListener('pointermove',handleMove)
}
},[enabled])
```

- En este código se puede ver que, partiendo del hecho qu

## Imperativo vs Declarativo

(ejemplo de comprar pan)

Imperativo: baja a la calle,vete al super, paga ,...

Declarativo: quiero pan.

## Pasar de desarrollo a producción y hacer deploy

## Modo producción

``npm run build`` Te genera un código, lo subes y listo

### Despliegue

Algunas aplicaciones pueden ser netlify drop
