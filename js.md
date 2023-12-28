# Diccionario de JavaScript

## parseInt  

 El parseInt devuelve todo lo encontrado hasta que encuentra el primer elemento no int.  

## String.repeat(ammount)

Dada una String str, con str.repeat(ammount) se repetirá ammount veces esa cadena.

## Encadenamiento opcional : "?."

Utilizando ?. en, x ejemplo, adventurer.dog?.name realiza el mismo trabajo que usar el . para acceder a un elemento. La diferenca es que con ?. , si dog no existiera , en vez de dar error como daría con . , al usar ?. devolvería undefined.

## Opciones de event

### Dado un form, con datos x

Si queremos recuperar su valor con js, se puede hacer de la siguiente manera:

```js
const handleClik = (event) => {
    event.preventDevault()
    const fields = new window.FormData(event.target) //aquí se recupera el form
    const query = fields.get('query') //y aquí el elemento con el nombre query 
    //( el input debe ser del estilo <input name='query'/>)
    /*podrías sacar cualquier elemento que 
    quieras del form. Si tienes x ejemplo, 3 inputs, 
    uno con name='query', otro con name='surname' y otro name='pit', 
    podrías recuperar todos de la siguiente manera:
    */
   const { query,surname,pit} = Object.fromEntries(new window.FormData(event.target))
}
```
