# Autocarga de Composer - Guillermo Mas | 1GS131

Composer es un administrador de dependencias para PHP, que permite definir el uso de paquetes de código de terceros en un proyecto, facilitando su instalación y actualización.
El objetivo de este laboratorio es crear un proyecto básico que implemente la Carga Automática (Autoload) bajo el Estándar PSR-4 con Composer.

## Guía de Instalación

  - Paso 1: Al haber creado un proyecto junto con su estructura básica, ya es propicio activar las funciones de composer para crear los archivos de autocarga. **El primer paso** consiste en abrir la terminal y escribir el siguiente comando en la carpeta del proyecto:
```
composer install
```
  - Paso 2: El próximo paso consiste en llamar al composer para hacer las labores de autocarga de clases, para evitar hacer cantidades grandes de ```require``` e ```include```.
    Escribe el siguiente comando en la terminal:
```
composer dump-autoload
```
## Estructura de archivos
En este caso, se está haciendo un documento sencillo que tiene una clase User y una base de datos ProductModel, y que imprimen datos almacendos en cada objeto en un archivo index.php. A continuación se muestra todo lo que deben tener los archivos para seguir este ejemplo.

### Estructura del Proyecto
```
AUTOCARGAMAS/
├── App/
│   └── User.php
├── Database/
│   └── Models/
│       └── ProductModel.php
├── vendor/
│   ├── composer/
│   │   ├── autoload_classmap.php
│   │   ├── autoload_namespaces.php
│   │   ├── autoload_psr4.php
│   │   ├── autoload_real.php
│   │   ├── autoload_static.php
│   │   ├── ClassLoader.php
│   │   ├── installed.json
│   │   ├── installed.php
│   │   ├── InstalledVersions.php
│   │   └── LICENSE
│   └── autoload.php
├── .gitignore
├── composer.json
├── composer.lock
└── index.php
```
### App/User.php
```
<?php

namespace App;

class User {

    public function getName():string {
        return "Dave";
    }
}

?>
```
### Database/Models/ProductModel.php
```
<?php

namespace Database\Models;

class ProductModel {

    public function getId():int {
        return 123;
    }
}   

?>
```
### index.php

```
<?php

use App\User;
use Database\Models\ProductModel;

require 'vendor/autoload.php';

$user = new User;
echo $user->getName();
echo "\n";

$product = new ProductModel;
echo $product->getId();
echo "\n";

?>
```

### composer.json
```
{"autoload": {
    "psr-4": { 
        "App\\": "app/",
        "Database\\": "database/"
        }
    }
}
```

## Pruebas de ejecución

- Paso 1
<img width="781" height="224" alt="image" src="https://github.com/user-attachments/assets/da8154cf-9859-45c3-8df5-ee27cd87a658" />
- Paso 2
<img width="829" height="115" alt="image" src="https://github.com/user-attachments/assets/001ac66a-06e1-430d-8e6b-7050a3b947c0" />
Verificación del index.php
<img width="921" height="165" alt="image" src="https://github.com/user-attachments/assets/2b792efb-764f-4cf7-ae3e-d708708a671d" />

## Análisis Comparativo (Conclusiones)

- Mantenibilidad: Considero que este tipo de herramientas son eficientes para el manejo y mantenibilidad de un proyecto, ya que este permite que no se tenga que trabajar excesivamente con archivos de estructura, y se manejan de manera automática en un entorno de desarollo colaborativo.
- Eficiencia de Memoria: El sistema de Lazy Loading es efectivo porque permite que no se carguen todos los objetos de un sistema, sino que se apliquen los necesarios dependiendo de la labor solicitada
- Estandarización: Mantener un estándar promueve la portabilidad de un trabajo a distintos departamentos de un área, y ayuda a la comunidad programadora en general, permitiendo que un grupo de personas dominen un campo y se puedan crear soluciones de manera más rápida y robusta.  









