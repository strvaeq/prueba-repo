# Mejoras realizadas y evidencia pendiente

## Lo que cambia respecto de la entrega anterior

- Presentación con identidad Renkay/Sami recuperada de su propio README, portada y diagramas originales.
- Capítulos redactados sobre el carro y el código real: ya no son listas que dicen «escribe esto».
- Mecánica con ecuaciones, límites, diferencias de geometría, transmisión y calibración asimétrica.
- Electrónica con roles de sensores, calibraciones por cámara, presupuesto por potencia y comportamiento de fallos.
- Open v5 explicado con sus estados reales, su control y sus condiciones de giro/finalización.
- Obstacle explicado desde percepción hasta aparcamiento, distinguiendo el perfil con pulsos del planificador geométrico.
- Guía de reconstrucción, protocolos de pruebas, mapa de rúbrica y créditos por componente.
- Traducción del texto chino de los controladores conservados y reducción del material ajeno al proyecto.

## Qué se tomó de los ejemplos

| Equipo | Práctica aplicada |
|---|---|
| Double X | Arquitectura y razonamiento energético por rieles; algoritmos vinculados a archivos |
| KMIDS | Organización del CAD, exportaciones y montaje reproducible |
| STORMS | Protocolos de desviación, giro, frenado y relación entre velocidad y observación |
| JEEP | Registro de versiones y adaptación documentada al campo |
| VizDrive | Evolución del auto, fallos y consecuencias de cada cambio |
| Fire On All Cylinders | Ruta clara desde presentación hasta detalle técnico |
| ANTi | Documentación especializada y calibración de visión |
| Flawil | Interacción entre subsistemas y procedimiento de ensamblaje |

No se atribuyen causas a sus descuentos de puntos: harían falta comentarios de jueces. No se copiaron sus resultados ni se presentaron sus fotos como propias.

## Lo que falta del mundo físico

1. Confirmar nombres y roles de esta temporada; Renkay y Sami provienen del README anterior.
2. Identificar el commit instalado en el Pi y cualquier cambio local respecto del coach.
3. Entregar fotos actuales de equipo y seis vistas del auto, más detalles de motor, engranajes y conexiones.
4. Trazar el cableado actual: batería, reguladores, conexiones de la placa, motor y sensores. El diagrama incluido explica funciones; no inventa pines.
5. Adjuntar CAD editable de fabricación, materiales, tornillos y ensamblaje actual.
6. Medir dimensiones, masa, giro, frenado, velocidad, consumo y autonomía; registrar condiciones.
7. Grabar rondas de Open y Obstacle. En Obstacle indicar salida, tres vueltas y aparcamiento, con el perfil exacto.
8. Completar los ensayos de ambos sentidos y distintas disposiciones incluyendo fallos.
9. Confirmar evento y fecha; revisar aclaraciones aplicables y plazos reales de GitHub.

## Comprobaciones técnicas prioritarias

El perfil de ronda de aparcamiento tiene pulsos dependientes del montaje y del campo. Debe ensayarse con distintas condiciones y en ambos sentidos. La conversión de motor, mínimo de rps y transmisión influyen en la velocidad real de esos pulsos. Los dos modelos de distancia entre ejes requieren validar coherencia con su tabla de esquinas; no se corrigieron números sin pruebas. Las protecciones desactivadas se describen como desactivadas, y la alerta de batería se diferencia de una parada automática.

El mínimo de caracteres del README está cubierto con explicación técnica, pero la cantidad de texto no sustituye evidencias. El archivo docs/10-evidence-register.md permite completar lo pendiente sin volver a escribir la documentación.
