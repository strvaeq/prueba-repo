# Puntos a mejorar y completar — Robotek

## Prioridad 1: necesarios antes de presentar

1. **Identidad y autoría.** Completar integrantes, roles, institución, evento y fecha en README. Explicar qué proviene del coach y qué desarrolló el equipo.
2. **Versión realmente instalada.** Comparar el commit del Pi con c5de794342b5da46725ba9a6994fb73bbebd0ff0. Incorporar cambios locales y conservar parámetros efectivos del lanzamiento. La fuente del coach describe el carro, pero falta comprobar qué revisión está instalada hoy.
3. **Esquema actual.** Dibujar batería, reguladores, Pi, RRC Lite, motor con encoder, servo y sensores, con conectores, pines y tensiones. Sustituir descripciones antiguas de L298N/TB6612 en el material de entrega.
4. **CAD y montaje.** Añadir diseños fabricables editables, exportaciones y montaje. Las mallas de simulación incluidas no demuestran que se pueda fabricar el vehículo.
5. **Fotografías y videos.** Añadir equipo, seis vistas actuales y videos de ambos retos. Al menos 30 segundos de autonomía por video según el PDF. Indicar versión y resultado del aparcamiento.
6. **Pruebas reales.** Registrar intentos, incluidos fallos, con batería, campo, sentido, commit y perfil. Los resultados heredados siguen siendo del experimento original; no se presentan como una validación nueva.
7. **Calendario.** Confirmar fecha y etapa del evento para revisar plazos de commits y entrega. Conservar historial auténtico; el ZIP no incluye ni fabrica historial.

## Prioridad 2: evidencias para los niveles altos de la rúbrica

| Criterio (6 puntos) | Mejora concreta | Evidencia esperada |
|---|---|---|
| Movilidad | Justificar materiales, dirección y transmisión; explicar velocidad/torque y alternativas | CAD, medidas, relación de engranajes, giro y frenado comparados |
| Alimentación y sensores | Cuantificar consumo, picos y autonomía; justificar ubicación y calibración | Presupuesto energético, esquemas, registros de calibración y fallos |
| Software y obstáculos | Explicar algoritmos, estados, excepciones y ajustes | Diagrama fiel al código, archivos enlazados y métricas por escenario |
| Integración y decisiones | Mostrar por qué cada cambio fue elegido y sus efectos en otros subsistemas | Problema → alternativas → ensayo → resultado → limitación |
| Reproducibilidad | Reconstruir y ejecutar desde instrucciones limpias | BOM, CAD, cableado, instalación verificada, versiones y pruebas |

## Prioridad 3: puntos técnicos que merecen comprobación

- El perfil de aparcamiento de ronda contiene dimensiones del lote, maniobras parciales y pulsos finales. Ensayar ambos sentidos, distintas posiciones y batería. No documentarlo únicamente como un planificador A* general.
- Medir la relación entre órdenes al motor y velocidad real; no asumir que las unidades de la placa equivalen directamente a vueltas del eje. Registrar la transmisión actual.
- Verificar la asimetría de dirección y los límites efectivos. El centro y la curva del servo son calibraciones específicas.
- Probar el fallback de sentido del Open cuando la cámara no decide; registrar si LiDAR corrige la decisión antes de la primera esquina.
- Verificar parada, sensores atrasados y pérdida de datos. No cambiar watchdogs o límites únicamente para ocultar fallos.
- Comprobar que la cámara, LiDAR e IMU tienen la orientación que supone robot.yaml.
- Añadir un diagrama de estados extraído de la estrategia efectivamente lanzada; no mezclar los estados del curso con Open v5.

## Qué ya se hizo

Se incorporó el código completo del coach conservando licencias y avisos; se redactó README en inglés, guía de instalación, mapa de archivos, ficha de configuración y documentos por criterio. Se prepararon CSV para materiales, calibración, consumo, decisiones y ensayos. Se corrigió .gitignore para permitir estrategias propias. No se modificó el código de conducción ni se ejecutó el robot.

## Cómo abrir y subir

1. Descomprimir Robotek-WRO2026-preparado.zip y abrir README.md en VS Code o cualquier lector Markdown.
2. Leer docs/current-vehicle.md, docs/strategy-map.md y este archivo.
3. Completar los puntos de prioridad 1 y marcar explícitamente cualquier limitación pendiente.
4. Para un repositorio GitHub que ya existe, clonarlo y copiar dentro el contenido de esta carpeta; revisar los cambios antes de hacer commit y push. No copiar una carpeta contenedora adicional ni usar force push.
5. Para uno completamente vacío, se puede inicializar Git en esta carpeta, crear un commit y conectarlo al remoto. Ese commit es nuevo, no acredita desarrollo anterior.

La documentación heredada incluye español y referencias de aprendizaje. Para la entrega internacional, revisar y traducir el material que forme parte de la documentación evaluada, manteniendo avisos legales originales. El mínimo de caracteres está cubierto; las evidencias pendientes todavía impiden considerar terminada la entrega.
