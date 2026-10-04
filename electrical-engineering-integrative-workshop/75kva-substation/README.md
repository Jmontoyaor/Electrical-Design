# Sistema de 75 kVA

Estudio de flujo de cargas de una subestación de distribución radial (red externa →
PCC 11,4 kV → cable de MT → transformador TR1 de 75 kVA → alimentador de BT →
tablero general de distribución), modelada en **DIgSILENT PowerFactory** con
Newton-Raphson AC balanceado, e interpretada frente al marco normativo colombiano
(RETIE, NTC 2050, NTC 1340).

## Resultados del sistema modelado

Todas las barras quedan dentro de la banda ±5 %/−10 % de la NTC 1340 (PCC y MT en
1,00 p.u., BT en 0,98 p.u., tablero general en 0,95 p.u.). El transformador opera al
83,9 % de su capacidad y el alimentador de BT al 67,2 % (cargabilidad, no caída de
tensión). Dos criterios quedan **justo en el límite**: la caída en el alimentador de
BT (≈3 %) y la caída acumulada MT→tablero (≈5 %), ambos calculados con las
resistencias a 20 °C. El informe recomienda repetirlos a la temperatura real de
operación del conductor, donde dejarían de cumplirse.

## Ejemplo didáctico independiente

Además del sistema real, el informe resuelve un caso de 4 barras (13,2 kV/220 V,
75 kVA) en tres escenarios —20 °C, 75 °C, y 75 °C con el tap del transformador
elevado un 2,5 %— para ilustrar el método de Newton-Raphson paso a paso. Converge
con convergencia cuadrática en 3 iteraciones en los tres casos. Pasar de 20 °C a
75 °C hace que la caída del alimentador de BT pase de cumplir (2,67 %) a incumplir
(3,14 %) el criterio del 3 %, mostrando que la temperatura de cálculo cambia el
resultado de la verificación normativa. Todos los resultados de este ejemplo
(tensiones, flujos, pérdidas y verificación normativa) se recalcularon de forma
independiente con un programa propio de Newton-Raphson escrito en Python, y
coincidieron con los valores reportados.

## Coordinación de protecciones

El informe de coordinación verifica, con curvas tiempo-corriente a 6 kV, la
selectividad de la ruta de protección (fusibles 8K e intermedio, fusible 8T,
reconectador Noja y relé SPAJ 142C de respaldo) frente a una falla de ≈1,1 kA. Los
cuatro pares de dispositivos cumplen el margen de coordinación exigido, aunque el
par fusible intermedio → 8T queda cerca del límite (72 % frente al 75 % máximo
permitido).

## Contenido

- `Informe_Flujo_de_Cargas_Subestacion_75kVA.pdf` — informe principal: fundamentos
  del flujo de cargas, configuración del cálculo en PowerFactory, resultados del
  sistema modelado, verificación normativa, ejemplo didáctico de Newton-Raphson y su
  verificación independiente.
- `Flujo de carga.pdf` — diagrama unifilar exportado de PowerFactory con los
  resultados del flujo de cargas (Figura 1 del informe principal).
- `informe_coordinacion.pdf` — estudio de coordinación de protecciones (ruta 1) con
  las curvas tiempo-corriente de fusibles, reconectador y relé.
- `subestaciones 75 kva(1).pfd` — proyecto de DIgSILENT PowerFactory.

## Software

Análisis realizado en **DIgSILENT PowerFactory**, con verificación independiente en
Python (Newton-Raphson).
