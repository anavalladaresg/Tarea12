# Ejercicio 12 - Tarea BBDD

👤 **Autor:** Ana Valladares González

---

Primero, debemos crear una nueva base de datos para almacenar los datos con los que trabajaremos. Seleccionaremos la opción de instalar los datos de demo para que se cree una base de datos con datos de ejemplo.

## 1️⃣ Apartado 1

Aunque no es recomendable, en ocasiones puede ser necesario crear tablas ajenas a Odoo dentro de su base de datos (integración con sistemas externos, almacenamiento de históricos, datos temporales, etc.). Utilizando PgAdmin u otro método adecuado, elabora y ejecuta una sentencia que cree una tabla llamada `EmpresasFCT` con los siguientes campos:

- `idEmpresa`: autonumérico. Este campo será la clave primaria.
- `nombre`: texto con tamaño máximo de 40 caracteres.
- `quiereAlumnos`: booleano.
- `numAlumnos`: número entero.
- `fechaContacto`: tipo fecha.

```sql
CREATE TABLE IF NOT EXISTS public."EmpresasFCT"
(
    "idEmpresa" integer NOT NULL DEFAULT nextval('"EmpresasFCT_idEmpresa_seq"'::regclass),
    nombre character varying(40) COLLATE pg_catalog."default" NOT NULL,
    "quiereAlumnos" boolean NOT NULL,
    "numAlumnos" integer,
    "fechaContacto" date NOT NULL,
    CONSTRAINT "EmpresasFCT_pkey" PRIMARY KEY ("idEmpresa")
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public."EmpresasFCT"
    OWNER to odoo;
```

![Creación tabla](img/1.png)

## 2️⃣ Apartado 2

Inserta 5 registros inventados en la tabla mediante una sentencia SQL.

```sql
INSERT INTO public."EmpresasFCT" ("nombre", "quiereAlumnos", "numAlumnos", "fechaContacto")
VALUES ('Empresa 1', true, 5, '2025-01-30'),
       ('Empresa 2', false, 0, '2025-01-29'),
       ('Empresa 3', true, 3, '2025-01-28'),
       ('Empresa 4', false, 0, '2025-01-27'),
       ('Empresa 5', true, 2, '2025-01-26');
```

<p align="center">
  <img src="img/2.png" alt="Inserción registros" width="49%" />
  <img src="img/3.png" alt="Registros insertados" width="49%" />
</p>