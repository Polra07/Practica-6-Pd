# Lector RFID con ESP32-S3 y MFRC522

Este proyecto implementa un lector de tarjetas RFID utilizando el lector MFRC522 y una placa ESP32-S3.

## Objetivo

Detectar tarjetas RFID, mostrar su UID, identificar el tipo de tarjeta, e intentar autenticarse en el sector 0 para leer las claves A y B.

## Componentes

- **ESP32-S3**
- **Lector RFID MFRC522**
- **Conexiones SPI personalizadas**

## Conexiones

| Componente MFRC522 | Pin ESP32-S3 |
|--------------------|--------------|
| SDA (SS)           | GPIO5        |
| RST                | GPIO4        |
| SCK                | GPIO36       |
| MOSI               | GPIO35       |
| MISO               | GPIO37       |

## Funcionamiento

1. **Inicialización**:
   - Configura la interfaz SPI con pines personalizados.
   - Inicializa el lector MFRC522.
   - Carga una clave por defecto (FF FF FF FF FF FF) para autenticación.

2. **Lectura RFID**:
   - Comprueba si hay una tarjeta presente.
   - Si la hay, lee su UID y lo muestra por el puerto serie.
   - Identifica el tipo de tarjeta.
   - Intenta autenticarse en el sector 0 con la clave A por defecto.
   - Si la autenticación tiene éxito, muestra la clave A y la clave B del bloque correspondiente.

3. **Cierre**:
   - Detiene la comunicación con la tarjeta tras cada ciclo.

## Requisitos

- Librería `MFRC522` de Miguel Balboa (disponible en el Gestor de Librerías de Arduino)
- Plataforma ESP32-S3
