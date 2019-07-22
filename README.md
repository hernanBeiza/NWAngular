# NWAngular

Ejemplo de Aplicación de escritorio con Angular y NWJS

## Tecnologías

- NPM
- Angular 7
- NWJS

## Desarrollo

Para levantar el servidor de desarrollo, ejecutar: 

`npm start`

## Instalación

Ejecutar 

`npm install`

## Compilación proyecto Angular Normal

Ejecutar 

`npm run build`

## Compilación proyecto Angular para aplicación de escritorio

Esta compilación es escpacial ya que queda en una carpeta específica para que NW ocupe en la compilación. Para ello se debe ejecutar 

`npm run build:ng`

## Compilación aplicación escritorio

Primero se debe ejcutar la compilación Angular, la cual dejará los archivos en la carpeta `dist-ng`:

`npm run build:ng`

Y después: 

`npm run build:nw`

La compilación Angular quedará en la carpeta `dist-ng`. Luego NWJS tomará esos archivos y creará la aplicación de escritorio en la carpeta `dist`, en el cual se encontrarán un ZIP y la aplicación ejecutable.

La plataforma de salida se configura por línea de comandos, en el script npm build:nw, como en el siguiente ejemplo

`
build --concurrent --tasks mac-x64 --mirror https://dl.nwjs.io/ .
`

Para más detalles revisar el archivo **package.json**

## Limpiar carpetas

Para limpiar las carpetas ejecutar:

`npm run clean`

## Configuración Proyecto NW

La configuración del compportamiento de la aplicación de escritori ose puede cambiar en el archivo **package.json**. Las propiedades importantes son:

```
  "main": "http://localhost:8964",
  "node-remote": "http://localhost:8964",
  "node-main": "",  
  "window": {
    "icon": "./icons/icon32x32.png"
  },
  "build": {
    "nwVersion": "v0.39.2",
    "nwFlavor": "normal",
    "targets": [
      "zip",
      "nsis7z"
    ],
    "files": [
      "**/*"
    ],
    "excludes": [
    ],
    "strippedProperties": [
      "chromium-args",
      "scripts",
      "devDependencies",
      "build"
    ],
    "overriddenProperties": {
      "main": "http://localhost:8965",
      "node-remote": "http://localhost:8965",
      "node-main": "server.js"
    },
    "win": {
      "icon": "./icons/icon.ico"
    },
    "mac": {
      "icon": "./icons/icon.icns"
    },
    "nsis": {
      "icon": "./icons/icon.ico",
      "unIcon": "./icons/icon.ico",
      "languages": [
        "English"
      ],
      "diffUpdaters": false,
      "hashCalculation": true
    }
  }
```  

## Futuro

- Automatizar aún más los scripts