# 📊 Proyecto de Análisis de Ventas - Power BI

## 🎯 Descripción del Proyecto

Este proyecto de Power BI está diseñado para analizar datos de ventas y proporcionar insights clave sobre el rendimiento de productos, tendencias temporales y métricas comerciales importantes.

## 🏗️ Arquitectura del Modelo de Datos

### Modelo Estrella (Star Schema)

```
📊 TABLA DE HECHOS
├── Fac_datos (Tabla principal de hechos)
│   ├── Cantidades
│   ├── Dim_ventas.Valor
│   └── Relaciones con dimensiones

🏷️ TABLAS DE DIMENSIONES
├── Dim_productos
│   ├── Id_productos
│   └── Producto
├── Dim_cantidades
│   ├── Fecha
│   ├── Grupo
│   └── Producto
├── Dim_ventas
│   ├── Fecha
│   ├── Centro
│   ├── Producto
│   └── Valor
├── Dim_grupos
│   ├── Grupo
│   └── Id_grupo
├── Dim_precio
│   ├── Fecha
│   ├── Grupo
│   ├── Producto
│   └── Valor
└── calendario
    ├── Date
    ├── Año
    ├── Mes
    └── Jerarquía de fechas
```

## 📈 Medidas DAX Principales

### 🏆 Productos Más y Menos Vendidos

```dax
Producto Mas Vendido 2023 = 
CALCULATE(
    MAXX(
        TOPN(1, VALUES(Dim_productos[Producto]), SUM(Fac_datos[Cantidades]), DESC),
        Dim_productos[Producto]
    ),
    YEAR(calendario[Date]) = 2023
)

Producto Menos Vendido 2023 = 
CALCULATE(
    MAXX(
        TOPN(1, VALUES(Dim_productos[Producto]), SUM(Fac_datos[Cantidades]), ASC),
        Dim_productos[Producto]
    ),
    YEAR(calendario[Date]) = 2023
)
```

### 📊 Totales por Período

```dax
Total Ventas 2023-2024 = 
CALCULATE(
    SUM(Fac_datos[Cantidades]),
    YEAR(calendario[Date]) IN {2023, 2024}
)
```

## 🚀 Funcionalidades Implementadas

### ✅ Análisis de Productos
- Identificación del producto más vendido por año
- Identificación del producto menos vendido por año
- Cantidad total vendida por producto
- Análisis de valor monetario por producto

### ✅ Análisis Temporal
- Comparativa entre años (2023-2024)
- Tendencias mensuales y trimestrales
- Análisis de estacionalidad

### ✅ Métricas de Negocio
- Total de ventas por período
- Valor monetario de las transacciones
- Análisis por grupos de productos

## 📋 Requisitos del Sistema

- **Power BI Desktop**: Versión 2.0 o superior
- **Memoria RAM**: Mínimo 4GB recomendado
- **Espacio en disco**: 500MB para archivos del proyecto
- **Sistema Operativo**: Windows 10/11

## 🔧 Instalación y Configuración

### 1. Clonar o Descargar el Proyecto
```bash
git clone [URL_DEL_REPOSITORIO]
cd powerbi-analisis-ventas
```

### 2. Abrir en Power BI Desktop
1. Abrir Power BI Desktop
2. Seleccionar "Abrir archivo"
3. Navegar hasta el archivo `.pbix` del proyecto
4. Actualizar conexiones de datos si es necesario

### 3. Configuración de Fuentes de Datos
- Verificar las conexiones a las fuentes de datos
- Actualizar credenciales si es necesario
- Configurar la actualización automática

## 📊 Estructura de Archivos

```
📁 powerbi-analisis-ventas/
├── 📄 README.md
├── 📄 LICENSE
├── 📁 datos/
│   ├── ventas_2023.csv
│   ├── ventas_2024.csv
│   └── productos.csv
├── 📁 pbix/
│   └── analisis_ventas.pbix
├── 📁 documentacion/
│   ├── manual_usuario.pdf
│   └── diccionario_datos.md
└── 📁 scripts/
    └── medidas_dax.txt
```

## 🎨 Dashboards Incluidos

### 📈 Dashboard Principal
- Resumen ejecutivo de ventas
- KPIs principales
- Gráficos de tendencias

### 🏆 Dashboard de Productos
- Ranking de productos más vendidos
- Análisis de productos menos vendidos
- Comparativas por categoría

### 📅 Dashboard Temporal
- Análisis de ventas por mes/trimestre/año
- Comparativas período a período
- Tendencias estacionales

## 🔄 Actualización de Datos

### Actualización Manual
1. Clic en "Actualizar" en Power BI Desktop
2. Verificar que todos los datos se carguen correctamente

### Actualización Programada (Power BI Service)
- Configurar gateway de datos si es necesario
- Establecer horarios de actualización
- Configurar notificaciones de errores

## 🛠️ Mantenimiento

### Optimización del Modelo
- Revisar relaciones entre tablas
- Optimizar medidas DAX complejas
- Eliminar columnas y tablas no utilizadas

### Mejores Prácticas Implementadas
- Nomenclatura consistente de tablas y medidas
- Documentación de medidas DAX
- Uso de formato condicional en visuales
- Implementación de tooltips informativos

## 🤝 Contribución

### Cómo Contribuir
1. Fork del proyecto
2. Crear una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit de cambios (`git commit -am 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Crear Pull Request

### Estándares de Código
- Usar nomenclatura clara para medidas DAX
- Documentar medidas complejas
- Seguir convenciones de modelado Power BI
- Probar todas las funcionalidades antes del commit

## 📝 Changelog

### v1.0.0 (2024-09-06)
- ✅ Implementación inicial del modelo de datos
- ✅ Creación de medidas básicas de análisis
- ✅ Dashboard principal de ventas
- ✅ Análisis de productos más/menos vendidos

### v1.1.0 (En desarrollo)
- 🔄 Mejoras en performance del modelo
- 🔄 Nuevas visualizaciones interactivas
- 🔄 Integración con fuentes de datos adicionales

## 📞 Soporte

Para soporte técnico o consultas sobre el proyecto:

- **Email**: [tu-email@ejemplo.com]
- **Issues**: Usar el sistema de issues de GitHub
- **Documentación**: Revisar la carpeta `/documentacion/`

## 📚 Recursos Adicionales

- [Documentación oficial de Power BI](https://docs.microsoft.com/power-bi/)
- [DAX Guide](https://dax.guide/)
- [Power BI Community](https://community.powerbi.com/)
- [Star Schema The Complete Reference](https://www.kimballgroup.com/)

## 🏷️ Tags

`#PowerBI` `#BusinessIntelligence` `#DataAnalytics` `#DAX` `#DataVisualization` `#Sales` `#KPI`

---

**Desarrollado con ❤️ usando Power BI**