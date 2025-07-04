# ESP-MONSTER v1.0.0

## Собранное устройство
![EspMonster](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/EspMonster.png)

## Функционал
| RF                          | WiFi                          | IR                          |
|-----------------------------|-------------------------------|-----------------------------|
| RF Jammer                   | Wifi Scan                     | Custom .ir files            |
| Scan/Copy                   | Analaizer                     | TV-B-Gone                   |
| Custom .sub files           | Ewil Portal                   | IR jammer                   |
| Save Signal                 | Custom HTML files             |                             |
| Custom range                |                               |                             |
| Spectrum                    |                               |                             |

## Необходимые комплектующие
| Компонент         | Количество | Ссылка на AliExpress                       |
|--------------------|------------|--------------------------------------------|
| ESP32 Wroom32      | 1 шт.      | [ESP32 Wroom32](https://aliexpress.ru/item/1005006826620736.html?sku_id=12000038429026888&spm=a2g2w.productlist.search_results.7.400a50fex56dp1) |
| CC1101             | 1 шт.      | [CC1101](https://aliexpress.ru/item/1005009185963141.html?sku_id=12000048230847372&spm=a2g2w.productlist.search_results.7.58f3562929ou2f) |
| Модуль SD-карты    | 1 шт.      | [SD Card Module](https://aliexpress.ru/item/1005006906986536.html?sku_id=12000038679692908&spm=a2g2w.productlist.search_results.1.32be21816nuSIL) |
| OLED-дисплей 0.96" | 1 шт.      | [OLED 0.96"](https://aliexpress.ru/item/1005006085392157.html?sku_id=12000035661592565&spm=a2g2w.productlist.search_results.0.d1532e96wuWLYd) |
| Кнопки             | 4 шт.      | [Кнопки](https://aliexpress.ru/item/1005006046180384.html?sku_id=12000035472972530&spm=a2g2w.productlist.search_results.0.36ea72eb7ejMDB) |
| ИК-светодиоды      | 3 шт.      | [IR LEDs](https://aliexpress.ru/item/1005003731923204.html?sku_id=12000026967708943&spm=a2g2w.productlist.search_results.8.6fb12a80Hy4Qg8) |
| Транзистор 2N2222A | 1 шт.      | [2N2222A](https://aliexpress.ru/item/1005009069169351.html?sku_id=12000047803537849&spm=a2g2w.productlist.search_results.0.45507f50LYswrn) |
| Резистор 10 Ом     | 1 шт.      | [10 Ohm Resistor](https://aliexpress.ru/item/1005009177180559.html?sku_id=12000048205104363&spm=a2g2w.productlist.search_results.10.133b4e5026aVX7) |

## Схема устройства
![Схема устройства](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/scheme.png)

## Пины устройства
| CC1101 | SD Card | Button | OLED | IR |
|--------|---------|--------|------|----|
| MOSI = 13 | CS = 23 | OK = 17 | SDA = 4 | D2 |
| MISO = 12 | MOSI = 21 | RIGHT = 5 | SCL = 15 | |
| SCK = 14 | MISO = 19 | LEFT = 18 | | |
| CSN = 25 | CLK = 22 | BACK = 33 | | |
| GDO0 = 16 | | | | |
| GDO2 = 32 | | | | |

## Требования к SD-карте
- SD-карты от Kingston и SanDisk (2–32 ГБ) работают идеально, некоторые другие могут не определяться.  
  ![Пример SD-карт](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo1.png)
- SD-карта **должна** быть отформатирована в FAT32.
- **НЕ ИСПОЛЬЗУЙТЕ УСТРОЙСТВО БЕЗ SD-КАРТЫ! SD-КАРТА ОБЯЗАТЕЛЬНА.**
- Не используйте файлы `.sub` и `.ir` с более чем 800 строками. Поддержка больших файлов будет добавлена в будущих обновлениях.
- Имена папок только на английском языке, так как поддержка кириллицы в прошивке отсутствует.

## Обязательные папки на SD-карте
- `BOOT LOGO`
- `EvilPortals/EvilPortalPassword`

![Обязательные папки](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo6.png)

## Установка кастомного загрузочного экрана
1. Выберите изображение в формате PNG или JPEG.
2. Измените размер изображения до 128x64 пикселей. Сделать это можно [здесь](https://www.iloveimg.com/ru/resize-image).
3. Скачайте [LCD Image Converter](https://sourceforge.net/projects/lcd-image-converter/), откройте его и выберите `File > Open` для загрузки вашего изображения 128x64.  
   ![Открытие файла в LCD Image Converter](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo2.png)
4. Перейдите в `Options > Conversion`, установите:
   - **Preset**: Monochrome
   - **Prepare > Type**: Monochrome
   - **Image > Block size**: 8-bit  
   ![Настройки Conversion](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo3.png)  
   ![Дополнительные настройки](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo4.png)
5. Нажмите кнопку **Show Preview** в левом нижнем углу и скопируйте все цифры.  
   ![Предпросмотр](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo5.png)
6. Вставьте эти цифры в `.txt` файл и поместите его в папку `BOOT LOGO` на SD-карте ESP-Monster.  
   ![Пример .txt файла](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo7.png)

- **Примечание**: В папке `BOOT LOGO` должен быть только один `.txt` файл с данными изображения.
- В папке `GOTOVIE LOGO` есть 8 готовых сконвертированных изображений.

## WiFi-функции
- Сканирование до 50 WiFi-сетей.
- **EvilPortal**: Можно выбрать кастомный HTML-файл и запустить EvilPortal. Данные сохраняются в папку `SD/EvilPortals/EvilPortalPassword`.
- Атаки на сети отсутствуют в версии 1.0.0, но будут добавлены в будущих обновлениях.

## Примечания
- **Версия 1.0.0 — тестовая**, возможны баги и лаги. Если нашли проблемы, сообщите мне в Telegram.
- **НЕ ИСПОЛЬЗУЙТЕ УСТРОЙСТВО БЕЗ SD-КАРТЫ! SD-КАРТА ОБЯЗАТЕЛЬНА.**
- **НЕ ИСПОЛЬЗУЙТЕ CC1101 БЕЗ АНТЕННЫ.**
- **НЕ ГЛУШИТЕ ЧУЖИЕ WI-FI СЕТИ.**
- **НЕ ИСПОЛЬЗУЙТЕ EVILPORTAL ДЛЯ КРАЖИ ПАРОЛЕЙ.**
- **НЕ ВЫКЛЮЧАЙТЕ ЧУЖИЕ ТЕЛЕВИЗОРЫ, КОНДИЦИОНЕРЫ И Т.Д.**
- **КОПИРОВАНИЕ ЧУЖИХ КЛЮЧЕЙ ЗАПРЕЩЕНО ЗАКОНОМ.**
- **ИСПОЛЬЗУЙТЕ УСТРОЙСТВО ТОЛЬКО В ОБРАЗОВАТЕЛЬНЫХ ЦЕЛЯХ!**

## Прошивка устройства, если сайт не работает
1. Откройте в браузере [web.esphome.io](https://web.esphome.io).  
   ![Сайт ESPHome](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo8.png)
2. Подключите ESP32 к компьютеру:
   - Удерживайте кнопку **Boot** на ESP32.
   - Удерживая Boot, подключите USB-кабель.
   - Нажмите кнопку **Reset** один раз, удерживая Boot, затем отпустите обе кнопки.
   - ESP32 готова к прошивке.
3. На сайте нажмите кнопку **Connect**.  
   ![Кнопка Connect](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo9.png)
4. Выберите порт, к которому подключена ESP32.  
   ![Выбор порта](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo10.png)
5. Нажмите **INSTALL**, выберите `.bin` файл прошивки ESP Monster v1.0.0 и нажмите **INSTALL**.  
   ![Установка прошивки](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo11.png)
6. Дождитесь завершения загрузки и нажмите кнопку **Reset** на ESP32.  
   ![Сброс после прошивки](https://github.com/deautherrr/ESPMONSTER-v1.0.0/raw/main/imagess/photo12.png)
