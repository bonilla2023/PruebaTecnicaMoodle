# PruebaTecnicaMoodle
Prueba Tecnica para el proceso LIDER EXPERTO MOODLE

## Enunciado de la Prueba
RED DE HOSPITALES ACME

Se cuenta con una red de hospitales a nivel nacional, se requiere contar con un software que optimice el uso de historias clínicas de los pacientes.
Actualmente se lleva la información en archivos físicos. Cada paciente puede visitar cualquier hospital de la red o instituciones asociadas. 
Las instituciones asociadas y los mismos hospitales pueden hacer toma de exámenes médicos. Las instituciones asociadas pueden ser propias de la red.
Para cada institución se requiere conocer el nivel de ocupación de las habitaciones, salas, y médicos.
Como parte de la historia clínica se debe tener el historial de citas de cada paciente con el medico,
cual fue el diagnostico, que tratamientos se le han aplicado. En una cita medica puede que lo atienda mas de un medico. 
Una enfermedad puede ser atendida por mas de un medico en diferentes citas o en la misma cita. 
Para el proceso de solicitud de citas se debe llamar con antelación para asignar una cita.
En las historias clínicas se debe incluir si el paciente falleció.

## Análisis / Algoritmia
1. Que información necesitaría adicional para mejorar la atención de los pacientes.
2. Como realizaría la optimización / planeación de los espacios y médicos en los hospitales? Teniendo en cuenta que los espacios y los médicos son fijos?
3. Como calcularía la fecha mas próxima de la solicitud una cita?
4. Defina un algoritmo que implemente las optimizaciones antes mencionadas. (Diagrama de flujo)
5. Para asegurar interoperabilidad entre sistema se requiere exposición via API Rest para el control de historias clínicas entre entidades de la red hospitalaria.
6. Utilice el framework más reciente y soportado que considere


## Base de Datos 
7. En que motor de base de datos implementaría su modelo? Por que? Defina sus Criterios y opciones.
8. Defina un modelo de datos que cumpla con los requerimientos antes mencionados. Explique que forma normal usaría? 
9. Realice las siguientes consultas SQL, teniendo en cuenta el modelo previo.
            Realice un reporte que indique cuantos médicos laboran en cada hospital
            Dada una enfermedad y un año determine cuales son los nombres de los médicos especialistas y cuantos pacientes entendieron en el año.
            Determine el porcentaje de ocupación de cada sala por mes.
            Realice un reporte que indique cuales son las enfermedades mas presentadas por los pacientes.

Finalmente envíe y sustente la soluciones en un espacio Git con control de versiones y en un video corto de no mas de 5 min sustente el proyecto desarrollado

## Solucion Algoritmia 1 al 3

1. Para mejorar la atención de los pacientes
Se requiere información adicional como el historial de enfermedades de los pacientes, así como información sobre medicamentos y alergias.

2. Para la optimización de los espacios y médicos en los hospitales.
Se puede utilizar un enfoque basado en la demanda por hora del día, día de la semana, mes y temporada del año. De esta manera, se pueden prever las necesidades futuras y asignar los recursos de manera más eficiente.

3. Para calcular la fecha más próxima de la solicitud de una cita.
Se debe tener en cuenta la disponibilidad de los médicos, la prioridad del paciente y la gravedad de la situación.

5. Se selecciona el framework Django para la implementación del sistema.

6. Para la base de datos se utilizaría un motor de base de datos relacional como MySQL.
Se realiza esta elección por su capacidad de manejar grandes cantidades de datos y su flexibilidad de manejo de transacciones complejas.

## Solucion Base de Datos

7. Se implementaría un modelo de datos relacional utilizando tablas para cada una de las entidades involucradas para asegurar la integridad de los datos. Se usarían claves foráneas para relacionar las tablas.

8. El modelo de datos que cumple con los requerimientos incluiría las siguientes entidades: pacientes, médicos, hospitales, historias clínicas, citas, enfermedades. Se usaría la tercera forma normal para asegurar la integridad y reducción de redundancia de los datos.

9. CONSULTAS SQL

SELECT hospital, COUNT(medico) FROM medicos GROUP BY hospital;
SELECT medico,nombre, COUNT(DISTINCT paciente) FROM historias_clinicas JOIN citas ON citas.historia_id = historias_clinicas.id JOIN medicos ON medicos.id = citas.medico_id WHERE enfermedad = "xxxx" AND YEAR(fecha) = 2021 GROUP BY medico;
SELECT sala, YEAR(fecha), MONTH(fecha), COUNT(DISTINCT historia_id) AS ocupacion FROM citas GROUP BY sala, YEAR(fecha), MONTH(fecha);
SELECT enfermedad, COUNT(DISTINCT paciente_id) FROM historias_clinicas GROUP BY enfermedad;
