# Billetera Digital – Caso 2 (Angular)

Billetera digital simple hecha con Angular y Bootstrap. Usa exactamente dos componentes propios:

- **`BilleteraComponent` (padre):** es dueño del estado (saldo inicial S/ 250.00 e historial vacío). Muestra el saldo con interpolación, el historial con `@for` y el mensaje "Aún no hay movimientos" con `@if`.
- **`NuevoMovimientoComponent` (hijo):** formulario de tipo (Recarga/Gasto) y monto. Recibe el saldo con `input()` y notifica al padre un movimiento válido con `output()`. Muestra el error con `@if` y deshabilita el botón con `[disabled]` cuando el formulario es inválido.

`App` (generado por Angular) solo es el contenedor. Los datos viven en memoria: no hay backend, servicios, enrutamiento ni formularios reactivos.

## Versiones usadas

- Node.js 20.19 o superior (o 22)
- Angular 22.2 / Angular CLI 22.2
- Bootstrap 5.3.3 (cargado por CDN en `src/index.html`, requiere internet)

## Cómo ejecutarlo

```bash
git clone https://github.com/stanizone/SolucionesWeb_T1_Caso2.git
cd SolucionesWeb_T1_Caso2
npm install
npm start
```

Abre http://localhost:4200 en el navegador. (`npm start` equivale a `ng serve`.)

## Pruebas automáticas

```bash
npm test
```

## Pruebas funcionales (manuales)

| # | Acción | Resultado esperado |
|---|--------|--------------------|
| 1 | Abrir la aplicación | Saldo S/ 250.00; historial vacío |
| 2 | Registrar recarga de S/ 100.00 | Saldo S/ 350.00; recarga en el historial |
| 3 | Registrar gasto de S/ 50.00 | Saldo S/ 300.00; el gasto aparece antes que la recarga |
| 4 | Intentar gasto de S/ 400.00 | Error "Saldo insuficiente", botón deshabilitado; saldo sigue en S/ 300.00 |
| 5 | Ingresar cero, negativo o monto vacío | Se rechaza; no cambia el saldo ni el historial |

## Estructura

```
src/app/
├── app.ts / app.html                    # contenedor
├── billetera.component.ts / .html       # padre: estado e historial
├── nuevo-movimiento.component.ts / .html # hijo: formulario y validación
└── movimiento.model.ts                  # tipos TypeScript
```
