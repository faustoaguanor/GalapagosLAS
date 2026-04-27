# GalapagosLAS - Visualizador de Nubes de Puntos LAS

Un visualizador web interactivo de nubes de puntos LAS/LiDAR para las Islas Galápagos, desarrollado con tecnologías de visualización 3D y procesamiento de datos geoespaciales.

## Descripción

Este proyecto permite la visualización y exploración interactiva de nubes de puntos LiDAR (formato LAS) de las Islas Galápagos utilizando Potree, una biblioteca de visualización de nubes de puntos basada en WebGL. La aplicación incluye dos interfaces principales: un visualizador 3D completo y un mapa interactivo para selección de datos.

## Características principales

- **Visualización 3D de nubes de puntos**: Renderizado en tiempo real de millones de puntos LiDAR
- **Interfaz Potree completa**: Controles de navegación, medición y análisis de datos 3D
- **Sistema de coordenadas georreferenciadas**: Soporte para proyecciones cartográficas específicas
- **Mapa interactivo de selección**: Interfaz basada en OpenLayers para selección de tiles
- **Modos de visualización avanzados**: EDL (Eye Dome Lighting), coloración por RGB, elevación e intensidad
- **Herramientas de análisis**: Medición de distancias, perfiles, clipping y estadísticas
- **Gestión de grandes volúmenes de datos**: Optimización para datasets extensos mediante octrees
- **Interfaz multilingüe**: Soporte para internacionalización

## Tecnologías utilizadas

### Visualización 3D y Nubes de Puntos
- **[Potree](https://github.com/potree/potree)**: Biblioteca principal para visualización de nubes de puntos en WebGL
- **[Three.js](https://threejs.org/)**: Motor de gráficos 3D para renderizado WebGL
- **[plas.io](https://github.com/verma/plasio)**: Lector de archivos LAS/LAZ para navegadores web

### Mapeo y Proyecciones
- **[OpenLayers 3](https://openlayers.org/)**: Biblioteca de mapeo web para la interfaz de selección
- **[proj4js](http://proj4js.org/)**: Biblioteca de transformaciones de coordenadas
- **[OpenStreetMap](https://www.openstreetmap.org/)**: Capas base de mapas

### Interfaz de Usuario
- **[jQuery](https://jquery.com/)**: Manipulación DOM y eventos
- **[jQuery UI](https://jqueryui.com/)**: Componentes de interfaz de usuario
- **[Perfect Scrollbar](https://github.com/utatti/perfect-scrollbar)**: Scrollbars personalizados
- **[jstree](https://www.jstree.com/)**: Componente de árbol para navegación de datos
- **[Spectrum](https://bgrins.github.io/spectrum/)**: Selector de colores
- **[D3.js](https://d3js.org/)**: Visualizaciones de datos y gráficos

### Utilidades
- **[Tween.js](https://github.com/tweenjs/tween.js/)**: Animaciones suaves
- **[i18next](https://www.i18next.com/)**: Internacionalización
- **[BinaryHeap](https://github.com/adamhooper/js-binaryheap)**: Estructura de datos para algoritmos de optimización

## Estructura del proyecto

```
GalapagosLAS/
├── index.html                  # Visualizador 3D principal de Potree
├── lasmap_index.html           # Mapa interactivo para selección de tiles
├── libs/                       # Dependencias externas
│   ├── potree/                 # Biblioteca Potree
│   ├── three.js/               # Motor 3D Three.js
│   ├── jquery/                 # jQuery y jQuery UI
│   ├── openlayers3/            # OpenLayers 3
│   ├── proj4/                  # Transformaciones de coordenadas
│   ├── plasio/                 # Lector LAS/LAZ
│   └── [otras bibliotecas]
├── pointclouds/index/          # Datos de nubes de puntos
│   ├── cloud.js                # Archivo de configuración principal
│   ├── metadata.json           # Metadatos de la nube de puntos
│   ├── sources.json            # Información de fuentes de datos
│   └── hierarchy.bin/          # Estructura octree optimizada
└── [otros archivos de datos]
```

## Instalación y uso

### Requisitos previos
- Servidor web (Apache, Nginx, o servidor estático como `http-server` de Node.js)
- Navegador web moderno con soporte WebGL (Chrome 60+, Firefox 55+, Edge 79+)
- Acceso a datos LAS/LAZ convertidos al formato Potree

### Instalación local
1. Clona el repositorio:
   ```bash
   git clone https://github.com/faustoaguanor/GalapagosLAS.git
   cd GalapagosLAS
   ```

2. Inicia un servidor web local:
   ```bash
   # Con Python 3
   python -m http.server 8000
   
   # O con Node.js http-server
   npx http-server
   ```

3. Abre tu navegador:
   - **Visualizador 3D**: `http://localhost:8000/index.html`
   - **Mapa de selección**: `http://localhost:8000/lasmap_index.html`

### Conversión de datos LAS/LAZ
Para usar datos propios, necesitas convertirlos al formato Potree:
```bash
# Instalar PotreeConverter (requiere CMake y compilador C++)
git clone https://github.com/potree/PotreeConverter.git
cd PotreeConverter
mkdir build && cd build
cmake ..
make

# Convertir archivo LAS/LAZ
./PotreeConverter /ruta/a/tu/archivo.las -o /salida/directorio
```

## Funcionalidades principales

### Visualizador 3D (index.html)
- **Navegación 3D**: Orbit, pan, zoom con controles intuitivos
- **Modos de coloración**: RGB, elevación, intensidad, clasificación
- **Filtrado de puntos**: Por clasificación, elevación, intensidad
- **Herramientas de medición**: Distancias 3D, áreas, volúmenes
- **Cortes de sección**: Planos de corte en cualquier orientación
- **Estadísticas**: Análisis de densidad, distribución, valores extremos
- **Exportación**: Capturas de pantalla, datos de medición

### Mapa de selección (lasmap_index.html)
- **Visualización espacial**: Ubicación geográfica de tiles LAS
- **Selección interactiva**: Selección de tiles individuales o por área
- **Descarga de datos**: Generación de listas de archivos para descarga
- **Información de tiles**: Metadatos y estadísticas por tile
- **Coordenadas geográficas**: Visualización en múltiples sistemas de coordenadas

## Formatos de datos soportados

### Entrada
- **LAS 1.0-1.4**: Formato estándar de nubes de puntos LiDAR
- **LAZ**: Versión comprimida de LAS (LASzip)
- **ASCII**: Formatos de texto de puntos separados por comas

### Salida/Visualización
- **Potree formato octree**: Estructura jerárquica optimizada para web
- **Texturas de tiles**: Representación visual de densidad de puntos
- **Metadatos JSON**: Información estructural y estadística

## Licencia

Este proyecto está licenciado bajo la **Licencia MIT**.

```
MIT License

Copyright (c) 2025 faustoaguanor

Se concede permiso, de forma gratuita, a cualquier persona que obtenga una copia
de este software y los archivos de documentación asociados (el "Software"), para
utilizar el Software sin restricción, incluyendo sin limitación los derechos
de uso, copia, modificación, fusión, publicación, distribución, sublicencia y/o
venta de copias del Software, y para permitir a las personas a las que se les
proporcione el Software hacer lo mismo, sujeto a las siguientes condiciones:

El aviso de copyright anterior y este aviso de permiso se incluirán en todas
las copias o partes sustanciales del Software.

EL SOFTWARE SE PROPORCIONA "TAL CUAL", SIN GARANTÍA DE NINGÚN TIPO, EXPRESA O
IMPLÍCITA, INCLUYENDO PERO NO LIMITADO A GARANTÍAS DE COMERCIALIZACIÓN,
IDONEIDAD PARA UN PROPÓSITO PARTICULAR Y NO INFRACCIÓN. EN NINGÚN CASO LOS
AUTORES O TITULARES DEL COPYRIGHT SERÁN RESPONSABLES DE NINGUNA RECLAMACIÓN,
DAÑOS U OTRAS RESPONSABILIDADES, YA SEA EN UNA ACCIÓN DE CONTRATO, AGRAVIO O
CUALQUIER OTRO MOTIVO, QUE SURJA DE O EN CONEXIÓN CON EL SOFTWARE O EL USO U
OTRO TIPO DE ACCIONES EN EL SOFTWARE.
```

## Créditos

### Desarrollo y Mantenimiento
- **Desarrollador principal**: faustoaguanor

### Bibliotecas Principales
- **Potree**: Markus Schütz y colaboradores (TU Wien)
- **Three.js**: Mr.doob y colaboradores
- **OpenLayers**: Comunidad OpenLayers
- **plas.io**: Uday Verma y colaboradores

### Tecnologías de Soporte
- **Proj4js**: Mike Adair, Richard Marsden y colaboradores
- **jQuery**: jQuery Foundation
- **OpenStreetMap**: Comunidad OpenStreetMap

### Formatos y Estándares
- **Formato LAS**: ASPRS (American Society for Photogrammetry and Remote Sensing)
- **Compresión LAZ**: Martin Isenburg (rapidlasso)
- **WebGL**: Khronos Group

## Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Abre un issue para discutir cambios importantes antes de realizar un pull request
2. Sigue las convenciones de código existentes
3. Incluye tests relevantes para nuevas funcionalidades
4. Actualiza la documentación según sea necesario

## Soporte y Problemas

Para problemas técnicos o preguntas:
1. Revisa la [documentación de Potree](https://github.com/potree/potree/wiki)
2. Consulta los [issues del repositorio](https://github.com/faustoaguanor/GalapagosLAS/issues)
3. Para problemas con datos LAS/LAZ, consulta las especificaciones ASPRS

## Aplicaciones y Casos de Uso

Este proyecto está diseñado para:
- **Investigación científica**: Análisis de cambios topográficos en Galápagos
- **Conservación ambiental**: Monitoreo de ecosistemas y biodiversidad
- **Planificación urbana**: Desarrollo sostenible en áreas protegidas
- **Educación**: Visualización interactiva de datos LiDAR para enseñanza
- **Turismo virtual**: Experiencias inmersivas de paisajes naturales

---

*Proyecto desarrollado para la visualización y análisis de datos LiDAR de las Islas Galápagos, patrimonio natural de la humanidad.*