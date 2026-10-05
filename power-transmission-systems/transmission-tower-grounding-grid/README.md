# Transmission Tower Grounding Grid Design

Análisis de alta frecuencia del desempeño de un tramo de línea de subtransmisión de
33 kV frente a descargas atmosféricas, y diseño de un sistema de puesta a tierra
orientado a evitar el *backflashover* (BFO) en la estructura A173 (tipo "Tormenta
R1"), modelando también las estructuras adyacentes A172 y A174.

## Metodología

- **ATPDraw**: modelo electromagnético en el dominio del tiempo del nodo de estudio
  y los apoyos adyacentes (A170 a A176), con la función de onda de corriente del
  rayo (Heidler), el criterio Volt-Time para el comportamiento no lineal del
  aislamiento, y las impedancias de impulso de las estructuras.
- **IEEE Flash 2.04**: evaluación estadística de la tasa anual de salidas de línea
  por apantallamiento y por backflashover.
- **SMath Studio**: memorias de cálculo de los parámetros de línea y del sistema de
  puesta a tierra.

## Resultado

Se evaluaron contrapesos horizontales de 40 m, 30 m, 20 m y 10 m. Un contrapeso de
10 m resultó insuficiente (se presenta BFO); 20 m fue la longitud mínima que evita
el backflashover. La configuración final —dos contrapesos horizontales de 20 m más
un electrodo vertical de 2,4 m— da una resistencia equivalente a pie de torre de
11,6454 Ω, y la evaluación estadística confirmó que el backflashover es el mecanismo
de falla predominante en el nodo estudiado (el apantallamiento tiene un desempeño
satisfactorio).

## Contenido

- `Diseño_de_una_malla_de_alta_frecuencia_para_torres_de_transmisión_G4.pdf` —
  informe final (46 páginas): marco teórico, metodología, modelado en ATPDraw,
  diseño del sistema de puesta a tierra, evaluación con IEEE Flash y conclusiones.
- `latex-source/` — fuente en LaTeX del informe (`Analisis_BFO.tex`,
  `references.bib`, carpeta `Figs/` con las figuras).
- `Memoria de Cálculo SMath G4.pdf` / `.sm` — memoria de cálculo (SMath Studio).
- `IEEE Flash - G4.xlsm` — hoja de cálculo de la evaluación estadística (IEEE Flash).
- `Simulacion_malla_atp_G4.acp` — modelo de simulación en ATPDraw.

> Nota: se excluyeron los archivos de compilación auxiliares de LaTeX
> (`.aux`, `.log`, `.out`, `.toc`, `.synctex.gz`, `.blg`, `.bbl`) y el `.zip` con el
> mismo código fuente, por ser redundantes con `latex-source/` y el PDF.

## Software

**ATPDraw**, **IEEE Flash 2.04** y **SMath Studio**.
