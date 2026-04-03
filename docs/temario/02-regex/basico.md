# Regex básico

## ¿Por qué?

Corpus lingüísticos digitales vienen sucios. Formatos inconsistentes, códigos extraños, metadatos mezclados con contenido. Limpieza manual es imposible en corpus de más de 1000 elementos.

## ¿Qué?

<div align=center>

|Regex = Expresión regular = Lenguaje de patrones|
|-|
Búsqueda de patrones en lugar de palabras exactas.

</div>

## ¿Para qué?

| Caso de uso | Regex |
|-------------|-------|
| Extraer fechas dd/mm/aaaa | `\d{2}/\d{2}/\d{4}` |
| Limpiar menciones de redes sociales | `@[\w]+` |
| Encontrar verbos en gerundio | `\w+(ando\|iendo)` |
| Extraer números de teléfono | `\d{3}-\d{3}-\d{4}` |
| Normalizar formatos (fechas) | Buscar `(\d{2})/(\d{2})/(\d{4})` → Reemplazar `$3-$2-$1` |

## ¿Cómo?

**Herramienta:** [regexr.com](https://regexr.com/)

Texto de trabajo

```
Ibuprofeno Fernández compró Ibuprofeno en la farmacia.
ibuprofeno genérico, IBUPROFENO 600, Ibupr0feno (marca pirata).
El médico recetó ibuprofeno; la farmacéutica dio Ibuprofeno.
Paracetamol 500mg   -   lote 2024/03/12
Aspirina  325mg - lote 2023/11/05
omeprazol   20mg   -  lote  2024/01/30
Contacto: ifernandez@farmacia.es  |  tel: 612 345 678
Cita: 12/03/2024 a las 09:30h, revisión: 05/11/2023
dr.García prescribió  3  unidades;   dra.López  prescribió 1
El el paciente debe tomar la la dosis indicada cada cada día.
```