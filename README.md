# 🚀 Laravel Project Setup with Docker, Breeze, Jetstream & Swagger

## 📌 Requisitos
- Docker & Docker Compose
- Node.js & npm
- Composer

## 🛠 Instalación

### 1️⃣ Crear el Proyecto con Laravel Sail
```sh
curl -s "https://laravel.build/nombre_proyecto?with=mysql,mailpit" | bash
```

### 2️⃣ Arrancar el Contenedor y Migrar la Base de Datos
```sh
./vendor/bin/sail artisan migrate
```

### 3️⃣ Instalar Laravel Breeze (Autenticación Simple)
```sh
composer require laravel/breeze --dev
./vendor/bin/sail php artisan breeze:install
./vendor/bin/sail php artisan migrate
```

### 4️⃣ Instalar Laravel Jetstream (Autenticación Avanzada)
```sh
composer require laravel/jetstream
./vendor/bin/sail php artisan jetstream:install livewire
```

### 5️⃣ Instalar Dependencias Frontend
```sh
npm install
npm run build
```

### 6️⃣ Modificar `docker-compose.yml`
Busca la siguiente línea:
```yaml
laravel.test:
    build:
        context: './vendor/laravel/sail/runtimes/8.3'
```

Reemplázala por:
```yaml
laravel.test:
    build:
        context: './docker'
```

### 7️⃣ Instalar Guzzle para Peticiones HTTP
```sh
composer require guzzlehttp/guzzle
```

### 8️⃣ Instalar Sanctum para Autenticación API
```sh
composer require laravel/sanctum
./vendor/bin/sail php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```

### 9️⃣ Instalar Swagger para Documentación de la API
```sh
composer require "darkaonline/l5-swagger"
./vendor/bin/sail php artisan vendor:publish --provider "L5Swagger\L5SwaggerServiceProvider"
./vendor/bin/sail php artisan l5-swagger:generate
```

## 🚀 ¡Listo para Codificar!
Tu proyecto Laravel está configurado con Docker, autenticación, API y documentación lista. 🎉
