# Autocarga de Composer 

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
En este caso, se está haciendo un documento sencillo que tiene una clase User y una base de datos ProductModel, y que imprimen datos almacendos en cada objeto en un archivo index.php

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








