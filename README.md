# Parcial Magneto

## Introduccion
Magneto quiere reclutar la mayor cantidad de mutantes para poder luchar contra los X-Mens.

Te ha contratado a ti para que desarrolles un proyecto que detecte si un humano es mutante basándose en su secuencia de ADN.

Para eso te ha pedido crear un programa con un método o función con la siguiente firma:

**isMutant(String[] dna)**

## Funcionamiento

Se recibirá como parámetro un array de Strings que representan cada fila de una tabla de (6x6) con la secuencia del ADN. Las letras de los Strings solo pueden ser: (A,T,C,G), las cuales representa cada base nitrogenada del ADN.

Se sabrá si un humano es mutante, si se encuentra **MAS DE UNA SECUENCIA** de cuatro letras iguales, de forma oblicua, horizontal o vertical.

Las filas de la matriz a verificar se ingresan por teclado.

Ejemplo de input: '**ATCGTA**' (esto equivale a una fila de la matriz)

Una vez cargada correctamente la misma, se aplica una función que verifica si hay presencia en la matriz de mutantes o no y se devuelve el resultado al usuario en base a eso.

## Ejecución

El proyecto ha sido deployado a Render y puede ser accedido mediante el siguiente link:

https://parcial-magneto.onrender.com

### Endpoints

- **POST** /mutant - Recibe un JSON con la matriz de ADN a verificar. Ejemplo:

```json
{
    "dna": [
        "ATGCGA",
        "CAGTGC",
        "TTATGT",
        "AGAAGG",
        "CCCCTA",
        "TCACTG"
    ]
}
```
- **GET** /stats - Devuelve un JSON con la cantidad de mutantes y humanos verificados. Ejemplo:

```json
{
    "count_mutant_dna": 40,
    "count_human_dna": 100,
    "ratio": 0.4
}
```

## Ejemplos de ADN

Ejemplo de matriz **MUTANTE**:

```json
{
    "dna": [
      "ATGCGA",
      "CAGTGC",
      "TTATGT",
      "AGAAAG",
      "CCCCTA",
      "TCACTG"
    ]
}
```

Ejemplo de matriz **NO MUTANTE**:

```json
{
    "dna": [
      "ATGGTG",
      "GTCTTA",
      "AATTGG",
      "ACTAGT",
      "GGATTC", 
      "AGGCAA"
    ]
}

```

## Pruebas Unitarias

Se incluyen casos de pruebas contemplando todos los patrones posibles (en filas, columnas y diagonales).
# Instrucciones para Ejecutar el Programa/API

## Nivel 2: API REST para Detección de Mutantes

1. **Crear la API REST**:
   - La API está diseñada para detectar si un humano es mutante mediante una secuencia de ADN.

2. **Hostear la API**:
   - La API se encuentra hospedada en Render, un servicio de cloud computing gratuito.

3. **Endpoint del Servicio**:
   - El servicio para verificar si un humano es mutante se puede acceder en el siguiente endpoint:
     ```
     POST /mutant/
     ```

4. **Formato de la Solicitud**:
   - La solicitud debe enviarse en formato JSON con el siguiente formato:
     ```json
     {
       "dna": ["ATGCGA", "CAGTGC", "TTATGT", "AGAAGG", "CCCCTA", "TCACTG"]
     }
     ```

5. **Respuestas**:
   - Si el ADN es de un mutante, se devuelve un código HTTP **200 OK**.
   - Si el ADN pertenece a un humano, se devuelve un código HTTP **403 Forbidden**.

---

## Nivel 3: Integración de Base de Datos y Estadísticas

1. **Integración de H2**:
   - Se ha anexado una base de datos H2 para almacenar los ADN verificados.
   - Solo se permite un registro por ADN.

2. **Endpoint de Estadísticas**:
   - Un servicio adicional para exponer estadísticas de verificaciones de ADN:
     ```
     GET /stats
     ```

3. **Formato de Respuesta de Estadísticas**:
   - La respuesta devuelve un JSON con el siguiente formato:
     ```json
     {
       "count_mutant_dna": 40,
       "count_human_dna": 100,
       "ratio": 0.4
     }
     ```

4. **Requisitos de Escalabilidad**:
   - La API está diseñada para manejar fluctuaciones agresivas de tráfico, con un rango estimado de entre 100 y 1 millón de peticiones por segundo.

5. **Pruebas Automáticas**:
   - Se deben implementar pruebas automáticas con una cobertura de código superior al **80%**.

---

## Resultados de Pruebas

- **Resultados de JMeter**:
  - (Agregar aquí los resultados obtenidos de las pruebas de carga con JMeter)

- **Resultados de JaCoCo**:
  - (Agregar aquí los resultados de las pruebas automáticas y la cobertura de código con JaCoCo)

