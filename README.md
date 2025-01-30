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