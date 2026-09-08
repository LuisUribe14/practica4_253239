# practica4_253239

1. Si Express no mandara los rechazos automáticamente al middleware de errores, ¿qué tendría que agregar en cada ruta?

Tendria que envolver el codigo de cada ruta en un bloque try/catch yo mismo y dentro del catch llamar a next a mano para pasarle el error al middleware y pues sin eso si algo fallara dentro de una ruta el error se quedaria "perdido" y el usuario nunca recibiria una respuesta

2. ¿Por qué mi Service no lanza directamente un error 409 en vez de EjemplarPrestadoError?

Porque mi service no deberia saber nada de HTTP no sabe si algun dia se usa desde una API web, una app de escritorio, o un script de consola y pues lo unico que le importa es la regla de negocio: "no se puede prestar un ejemplar ya prestado". Por eso lanza ese error y es tarea del servidor traducir ese error a un código HTTP como 409

3. Si mañana agregara una app móvil que también consume esta API, ¿qué archivos tendría que tocar?

Ps nada la app movil hablaria directo con mi API igual que lo hace ahora cliente.ts desde el navegador asi que no tendria que tocar el Service, el Repository, ni siquiera servidor.ts  porque la API ya está expuesta
