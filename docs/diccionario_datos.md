# Diccionario de datos

| Variable | Tipo | Uso en el proyecto | Observación |
|---|---|---|---|
| `ID` | Numérica | Eliminada | Identificador, no aporta generalización y puede afectar privacidad. |
| `NombreEmpleado` | Categórica/texto | Eliminada | Dato identificatorio; se excluye por privacidad. |
| `Departamento` | Categórica | Predictora | Área organizacional del empleado. |
| `Cargo` | Categórica | Predictora | Puesto o función laboral. |
| `SalarioBase` | Numérica | Predictora | Salario base mensual. |
| `HorasExtra` | Numérica | Predictora | Tiene valores faltantes; se imputa con mediana. |
| `OtrosPagos` | Numérica | Predictora | Pagos adicionales. |
| `Beneficios` | Numérica | Predictora | Tiene valores faltantes; se imputa con mediana. |
| `SalarioTotal` | Numérica | Predictora | Variable salarial agregada. |
| `SalarioTotalConBeneficios` | Numérica | Predictora | Variable dominante; se relaciona directamente con la etiqueta. |
| `Año` | Numérica | Predictora | Todos los registros corresponden a 2025. |
| `Notas` | Numérica/vacía | Eliminada | Columna completamente vacía. |
| `Oficina` | Categórica | Predictora | Ubicación o tipo de oficina. |
| `TipoContrato` | Categórica | Predictora | Tiene valores faltantes; se imputa con moda. |
| `Sexo` | Categórica | Variable sensible y predictora en el notebook | Se usa para auditoría de equidad; debe manejarse con cautela. |
| `IngresoAnual` | Numérica derivada | Eliminada del entrenamiento | Se usa para crear la etiqueta. |
| `GanaMas40K` | Binaria | Variable objetivo | 1 si supera USD 40.000 anuales; 0 si no. |
