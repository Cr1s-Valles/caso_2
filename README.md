# Segunda Vida — Caso 2

Aplicación local de apoyo a decisiones para el caso ficticio **“Segunda Vida y el pedido de mandos reacondicionados”**.

## Cómo ejecutar
1. Descarga o clona este repositorio.
2. Abre `index.html` directamente en un navegador moderno.
3. Modifica demanda, minutos netos, proporción de ruta M y rendimiento mínimo.
4. Selecciona una alternativa para destacarla. La tabla compara siempre Referencia, A y B.
5. Usa “Restablecer escenario base” para volver a 196 mandos buenos, 420 minutos, r=0,30 y mínimo=0,98.

No requiere servidor, instalación, API, claves, dependencias externas ni conexión a internet.

## Decisión que apoya
Permite comparar si la referencia y los rediseños obligatorios A y B pueden planificar la demanda de mandos buenos, respetando el rendimiento mínimo, el inventario de 300 entradas y el tiempo neto disponible. También muestra cargas por persona, capacidad, coste incremental y productividad del plan realizable.

## Datos y fórmulas
Todos los datos son sintéticos y proceden de la ficha del Caso 2 del cuaderno del proyecto.

Tiempos estándar manuales, con suplemento del 15 % sobre el tiempo normal:
- A = 34,50 s
- B = 96,60 s
- C = 131,10 s
- D = 34,50 s
- E = 46,00 s

Con proporción de ruta M (r), tasa de fallo inicial (f) y recuperación del segundo intento del 80 %:
- Cambios de módulo esperados por entrada = r + f.
- Buenos esperados por entrada = 1 − 0,2f.
- Pruebas esperadas por entrada = 1 + f.
- Ocupación del banco por entrada = (1 + f) × (D estándar + 60 s).
- Capacidad de entradas = piso(tiempo neto disponible en segundos / mayor carga por puesto).
- Entradas requeridas = techo(demanda de buenos / rendimiento esperado).

Cargas:
- Referencia y A: Persona 1 = A + B; Persona 2 = (r+f)C + (1−0,2f)E; Persona 3 = (1+f)(D+60).
- B: Persona 1 = B; Persona 2 = (r+f)C + (1−0,2f)E; Persona 3 = (1+f)(D+60); Persona 4 = A + (1−0,2f)E.

Costes incrementales:
- Referencia = 0 €/turno.
- A = 250 €/20 turnos.
- B = 200 €/20 turnos + 90 €/turno.

La extensión C no forma parte de la comparación obligatoria y no está incluida como opción seleccionable en esta versión.

## Muestreo y ergonomía
La app muestra las proporciones derivadas de 300 observaciones (210 primera pasada, 36 retrabajo, 39 espera, 15 traslado) y calcula el tamaño orientativo de muestra para estimar espera con p=0,13, z=1,96 y e=0,05. También presenta la comparación de alcances y ubicaciones de contenedores de la ficha, con una propuesta de reubicación. No atribuye ahorros de tiempo al cambio ergonómico.

## Límites
- Es un modelo de medias; no garantiza la entrega de cada turno ni pronostica colas o nivel de servicio.
- No sustituye los cálculos manuales ni la validación de la clase.
- La herramienta no diagnostica lesiones ni certifica cumplimiento normativo.
- No incluye cálculo biomecánico porque la ficha no proporciona todos los insumos necesarios.
- Las pruebas de aceptación incluidas deben conciliarse con resultados manuales independientes antes de entregar la versión académica.

## Pruebas pendientes de conciliación manual
La ficha solicita comprobar tres referencias: Referencia (196, 420 min, r=0,30, mínimo 0,98), A con los mismos parámetros y B (220, 420 min, r=0,30, mínimo 0,98). También se deben probar una frontera, una entrada inválida y un escenario no factible. La interfaz rechaza dominios inválidos y muestra factibilidad, pero el equipo debe registrar en su tabla el resultado manual, el obtenido, la diferencia, la tolerancia y la explicación.

## Uso de IA
Se utilizó IA como apoyo para estructurar la interfaz, implementar cálculos deterministas, explicar fórmulas y proponer pruebas. El equipo conserva la responsabilidad de revisar el código, resolver referencias manuales, conciliar resultados y documentar las sugerencias aceptadas, modificadas o descartadas. No se incorporan servicios externos ni claves API.
