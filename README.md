# Descripción del proyecto 

Has recibido una tarea analítica de una tienda en línea internacional. Tus predecesores no consiguieron completarla: lanzaron una prueba A/B y luego abandonaron (para iniciar una granja de sandías en Brasil). Solo dejaron las especificaciones técnicas y los resultados de las pruebas.

# Descripción Técnica

- Nombre de la prueba: `recommender_system_test`
- Grupos: А (control), B (nuevo embudo de pago)
- Launch date: 2020-12-07
- Fecha en la que dejaron de aceptar nuevos usuarios: 2020-12-21
- Fecha de finalización: 2021-01-01
- Audiencia: 15% de los nuevos usuarios de la región de la UE
- Propósito de la prueba: probar cambios relacionados con la introducción de un sistema de recomendaciones mejorado
- Resultado esperado: dentro de los 14 días posteriores a la inscripción, los usuarios mostrarán una mejor conversión en vistas de la página del producto (el evento `product_page`), instancias de agregar artículos al carrito de compras (`product_card`) y compras (`purchase`). En cada etapa del embudo `product_page → product_card → purchase`, habrá al menos un 10% de aumento.
- Número previsto de participantes de la prueba: 6000

**Descarga los datos de la prueba, comprueba si se ha realizado correctamente y analiza los resultados.**

**Describe tus conclusiones con respecto a la etapa EDA y los resultados de la prueba A/B**

# Descripción de los Datos

Se te proporcionaron los siguentes datasets:

- `ab_project_marketing_events_us.csv`: El calendario de eventos de marketing para 2020
- `final_ab_new_users_upd_us.csv`: Todos los usuarios que se registraron en la tienda en línea desde el 7 hasta el 21 de diciembre de 2020
- `final_ab_events_upd_us.csv`: Todos los eventos de los nuevos usuarios en el período comprendido entre el 7 de diciembre de 2020 y el 1 de enero de 2021
- `final_ab_participants_upd_us.csv`: Tabla con los datos de los participantes de la prueba.

Estructura `ab_project_marketing_events_us.csv`:

- `name`: El nombre del evento de marketing
- `regions`: Regiones donde se llevará a cabo la campaña publicitaria
- `start_dt`: Fecha de inicio de la campaña
- `finish_dt`: Fecha de finalización de la campaña

Estructura `final_ab_new_users_upd_us.csv`:

- `user_id`: ID del usuario
- `first_date`: Fecha de inscripción
- `region`: Región donde se llevo cabo la campaña
- `device`: Dispositivo utilizado para la inscripción

Estructura `final_ab_events_upd_us.csv`:

- `user_id`: ID del usuario
- `event_dt`: Fecha y hora del evento
- `event_name`: Nombre del tipo de evento
- `details`: Datos adicionales sobre el evento (por ejemplo, el pedido total en USD para los eventos `purchase`)

Estructura `final_ab_participants_upd_us.csv`:

- `user_id`: ID del usuario
- `ab_test`: Nombre de la prueba
- `group`: El grupo de prueba al que pertenecía el usuario

## 🛠 Skills

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)

![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)

![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)

![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

![SciPy](https://img.shields.io/badge/SciPy-%230C55A5.svg?style=for-the-badge&logo=scipy&logoColor=%white)

## Lessons Learned

Aprendi a realizar pruebas estadisticas para A/B test. Analisis exploratorio de datos para diferentes datos agrupados y funnels para etapas de marketing de negocios.

# Conclusiones

- Durante el EDA se pudo validar que no habia filas completamente duplicadas, sin embargo, se encontraron valores ausentes pero estos no indicaban un problema para el analisis del dataset ya que los valores ausentes eran normales para la columna especifica. Se pudo notar que los registros del A/B test tienen un lapso de tiempo de menos de 1 mes de duracion. 

- Se encontraron 3675 usuarios unicos en el A/B test, teniendo en cuenta las descripciones tecnicas se pudo notar que es un numero demasiado bajo ya por lo menos deberiamos tener un numero previsto de participantes de 6000.

- Los resultados del A/B test indican que los usuarios no siguen una ruta de eventos establecida para el embudo propuesto en la descripcion tecnica de la prueba, al parecer, la prueba no se realizo correctamente o existes errores en los datos de lectura del tiempo exacto en que los usuarios realizaron los distintos eventos en el embudo.

- Los usuarios unicos por grupo no estan distribuidos de forma equitativa por lo que el numero de eventos por usuario difiere entre los distintos eventos.

- El Z-test nos indica que las proporciones de la conversion de los usuarios no son diferentes para todas las etapas por lo tanto la conversion mejora pero no para todos los eventos que es lo que en realidad busca el test validar, por lo tanto, se pudo notar que el test no mejoro la conversion para todas las etapas del embudo de eventos.
