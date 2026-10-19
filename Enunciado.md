# Prueba técnica · Diseñar una plataforma de datos de TPV

## Contexto

Vamos a construir una plataforma de analítica para grupos de restauración con varios locales.

La plataforma se conectará a los sistemas que cada grupo ya usa, guardará sus datos en un modelo común y calculará KPIs diarios por local: venta, ticket medio, venta por producto… La dirección del grupo los consultará en cuadros de mando.

Empezamos por las ventas, que vienen del TPV. Fichajes, reservas y otros sistemas llegarán después, pero no forman parte de esta prueba.

## El encargo

Diseña la plataforma para el primer cliente, que usa un TPV llamado **Comandero**. Tiene que estar hecha de forma que **mañana se puedan conectar otros TPV sin rehacerla**.

La web de los cuadros de mando queda fuera. Céntrate en cómo llegan los datos, cómo se guardan y cómo se calculan los KPIs.

Lo que sabemos de Comandero:

- Tiene una API REST paginada que permite filtrar los tickets por fecha de modificación. No tiene webhooks.
- Se autentica por una api key que el cliente nos facilita.
- Admite 60 peticiones por minuto por cuenta. El cliente tiene **40 locales en una sola cuenta**.
- Algunos locales pueden llegar a generar miles de tickets al día
- Un ticket se puede modificar hasta 7 días después de emitirse.
- Las horas vienen en hora local, sin zona horaria.
- El cliente quiere **dos años de histórico** al darse de alta.

Lo que pide negocio:

> «Quiero poder ver la siguiente información en el cuadro de mandos: el total vendido, el número de tickets, el ticket medio y el desglose de ventas por turno. A las 7:00 tiene que estar disponible la información del día anterior. Si un dato en el pasado cambia, el KPI se debe recalcular automáticamente»

## Qué haremos

1. **Lectura.** Lees este documento y tomas las notas que quieras.
2. **Preguntas.** Preguntas a Producto y a Técnico lo que necesites para diseñar. Lo que no preguntes, lo resuelves con supuestos.
3. **Diseño de la solucón.** Plantea el modelo de datos, las piezas de software que necesitamos y, sin entrar en mucho detalle, la definición de cada una de ellas. Plantea alternativas cuando tenga sentido, valora las ventajas/inconvenientes y toma decisiones en base a ello.
4. **Plan de implementación.** Desglosas el trabajo en tareas.
6. **Situaciones nuevas.** Te plantearemos un par de cambios sobre tu propuesta.
7. **Tus preguntas.**

## Herramientas

Tendrás dos espacios compartidos:

- **Una pizarra** para dibujar lo que quieras.
- **Un documento** con cuatro apartados vacíos: *Supuestos*, *Preguntas abiertas*, *Decisiones* y *Tareas*.

Úsalos como te resulte más útil.
