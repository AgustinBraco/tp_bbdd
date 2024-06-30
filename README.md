<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=e1bbbd&height=120&section=header"/>

# Base de datos
Este repositorio contiene la estructura y datos para la creación de una  base de datos para gestionar el alquiler de canchas deportivas.

## Tablas
1. Usuarios
   - `id_usuario`: Variable numérica. Almacena el identificador único del usuario.
   - `nombreUsuario`: Variable de texto. Almacena el nombre del usuario.
   - `apellidoUsuario`: Variables de texto. Almacena el apellido del usuario.
   - `dniUsuario`: Variable numérica. Almacena el DNI del usuario.
   - `mailUsuario`: Variable de texto. Almacena el correo electrónico del usuario.
   - `telefonoUsuario`: Variable numérica. Almacena el número de teléfono del usuario.

2. Tipo de suelo
   - `id_tiposuelo`: Variable numérica. Almacena el identificador único del tipo de suelo.
   - `tipodesuelo`: Variable de texto. Almacena el nombre del tipo de suelo de la cancha.

3. Canchas
   - `id_cancha`: Variable numérica. Almacena el identificador único de la cancha.
   - `capacidad`: Variable numérica. Almacena la capacidad máxima de la cancha.
   - `id_tiposuelo`: Variable numérica. Almacena el identificador único del tipo de suelo para ser referenciado.
   - `techo`: Variable booleana. Indica si la cancha tiene o no techo.
   - `precio`: Variable numérica. Almacena el precio de alquiler de la cancha.
   - `disponible`: Variable booleana. Indica si la cancha está o no disponible.

4. Administradores
   - `id_administrador`: Variable numérica. Almacena el identificador único del administrador.
   - `nombreAdmin`: Variable de texto. Almacena el nombre del administrador.
   - `apellidoAdmin`: Variables de texto. Almacena el apellido del administrador.
   - `dniAdmin`: Variable numérica. Almacena el DNI del administrador.
   - `mailAdmin`: Variable de texto. Almacena el correo electrónico del administrador.
   - `telefonoAdmin`: Variable numérica. Almacena el número de teléfono del administrador.

5. Metodo de pago
   - `id_metodoPago`: Variable numérica. Almacena el identificador único del método de pago.
   - `metodoPago`: Variable de texto. Almacena el nombre del método de pago.

6. Estado de la reserva
   - `id_estadoReserva`: Variable numérica. Almacena el identificador único del estado de la reserva.
   - `estadoReserva`: Variable de texto. Almacena el estado actual de la reserva.

7. Reservas
   - `id_reserva`: Variable numérica. Almacena el identificador único de la reserva.
   - `id_usuario`: Variable numérica. Almacena el identificador único del usuario para ser referenciado.
   - `id_cancha`: Variable numérica. Almacena el identificador único de la cancha para ser referenciado.
   - `id_administrador`: Variable numérica. Almacena el identificador único del administrador para ser referenciado.
   - `id_estadoReserva`: Variable numérica. Almacena el identificador único del estado de reserva para ser referenciado.
   - `id_metodoPago`: Variable numérica. Almacena el identificador único del método de reserva para ser referenciado.
   - `fechaInicio`: Variable de fecha y hora. Almacena el horario cuando empeza la reserva.
   - `fechaFin`: Variables de fecha y hora. Almacena el horario cuando finzaliza la reserva.
   - `monto`: Variable numérica. Almacena el monto total de la reserva.
   - `seña`: Variable numérica. Almacena el monto de la seña recibida para la reserva.

## Consultas de ejemplo
- Tablas completas:
```sql
SELECT * FROM usuarios;
SELECT * FROM tipoDeSuelo;
SELECT * FROM canchas;
SELECT * FROM administradores;
SELECT * FROM metododePago;
SELECT * FROM estadoReserva;
SELECT * FROM reservas;
```

- Total de canchas disponibles:
```sql
SELECT COUNT(*) AS 'Canchas disponibles'
FROM canchas
WHERE disponible = 1;
```

- Canchas disponibles según capacidad:
```sql
SELECT canchas.capacidad AS 'Capacidad',
tipoDeSuelo.tipodesuelo AS 'Suelo',
canchas.precio AS 'Precio'
FROM canchas
INNER JOIN tipoDeSuelo
ON canchas.id_tiposuelo = tipoDeSuelo.id_tiposuelo
WHERE disponible = 1 && capacidad = 14;
```

- Reservas abonadas ordenadas por fecha con administrador:
```sql
SELECT reservas.id_cancha AS 'Cancha', 
DATE(reservas.fechaInicio) AS 'Fecha', 
TIME(reservas.fechaInicio) AS 'Horario', 
CONCAT(administradores.nombreAdmin, ' ', administradores.apellidoAdmin) AS 'Reservado por'
FROM reservas
INNER JOIN administradores
ON reservas.id_administrador = administradores.id_administrador
INNER JOIN estadoReserva
ON reservas.id_estadoReserva = estadoReserva.id_estadoReserva
WHERE estadoReserva.estadoReserva = 'Abonada'
ORDER BY Fecha, Horario;
```

## Grupo: Fuentón de achuras
### Integrantes:
- Agustín Braco
- Ayelén Corrillo
- Claudio Rodríguez
- Daniel Drago
- Mercedes Marighetti
- Tobias Arraiza

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=e1bbbd&height=120&section=footer"/>