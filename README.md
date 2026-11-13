# poco-x3-pro-iphone-boot
iPhone bootlogo and Magisk bootanimation for POCO X3 Pro (vayu/bhima)


# ENG=

# POCO X3 Pro (`vayu` / `bhima`) — iPhone Bootlogo & Bootanimation

Complete Apple-style boot sequence for **POCO X3 Pro** running custom ROMs with **Magisk**.
* **`logo_apple.img`** — replaces the first bootloader splash screen (removes the yellow `POCO` text, `Powered by Android`, and the unlocked padlock icon). `FASTBOOT` and system warning screens stay untouched.
* **`iPhone_Boot_Magisk.zip`** — systemless Magisk module that replaces `/system/media/bootanimation.zip`.

> **WARNING:** Flash `logo_apple.img` **ONLY** on **POCO X3 Pro (`vayu` / `bhima`)**. Do not use it on POCO X3 NFC or any other device. Always make a backup before flashing.

## Where to get the files
Download both files (`logo_apple.img` and `iPhone_Boot_Magisk.zip`) from the **[Releases](../../releases)** section on the right (or directly from this repository).

## Part 1: Installing the Bootanimation (Magisk)
1. Download **`iPhone_Boot_Magisk.zip`** onto your phone.
2. Open the **Magisk** app.
3. Go to the **Modules** tab at the bottom right.
4. Tap **Install from storage** and select **`iPhone_Boot_Magisk.zip`**.
5. Once flashed, tap **Reboot**.

*(Note: If your custom ROM uses `/system/product/media/` instead of `/system/media/`, unpack the zip, move `bootanimation.zip` to `system/product/media/`, and re-zip it with **Store / No compression** mode).*

## Part 2: Flashing the Bootloader Splash (`logo_apple.img`)

### Step 1: Backup your stock `logo` partition (Mandatory)
Open **Termux** (or ADB shell) on your phone and run:
```bash
su
dd if=/dev/block/bootdevice/by-name/logo of=/sdcard/Download/logo_stock.img
```
Save `logo_stock.img` to your PC in case you ever want to revert back.

### Step 2: Flash `logo_apple.img` via Fastboot
1. Power off your phone completely.
2. Hold **Power + Volume Down** until the orange **`FASTBOOT`** screen appears.
3. Connect the phone to your PC via USB cable.
4. Open a terminal / command prompt in the folder with `logo_apple.img` and check connection:
   ```bash
   fastboot devices
   ```
5. Flash the new splash screen:
   ```bash
   fastboot flash logo logo_apple.img
   ```
6. Reboot the device:
   ```bash
   fastboot reboot
   ```

## How to restore the original POCO logo
If you want to go back to the stock splash screen at any time, boot into Fastboot and flash your backup:
```bash
fastboot flash logo logo_stock.img
fastboot reboot
```

---
---
# RU=

# POCO X3 Pro (`vayu` / `bhima`) — Заставка и анимация включения в стиле iPhone

Полная замена экрана загрузки для **POCO X3 Pro** на кастомных прошивках с **Magisk**.
* **`logo_apple.img`** — заменяет самый первый экран загрузчика (убирает желтую надпись `POCO`, `Powered by Android` и замочек разблокированного загрузчика). Экраны `FASTBOOT` и системных предупреждений остаются нетронутыми.
* **`iPhone_Boot_Magisk.zip`** — системлесс-модуль Magisk, который безопасно подменяет `/system/media/bootanimation.zip`.

> **ВНИМАНИЕ:** Прошивайте `logo_apple.img` **СТРОГО** на **POCO X3 Pro (`vayu` / `bhima`)**. Не используйте этот файл на POCO X3 NFC или других смартфонах. Обязательно сделайте резервную копию перед прошивкой.

## Где скачать файлы
Скачайте оба файла (`logo_apple.img` и `iPhone_Boot_Magisk.zip`) во вкладке **[Releases](../../releases)** справа (или напрямую из этого репозитория).

## Часть 1: Установка анимации загрузки (через Magisk)
1. Скачайте **`iPhone_Boot_Magisk.zip`** на телефон.
2. Откройте приложение **Magisk**.
3. Перейдите во вкладку **Модули (Modules)** в правом нижнем углу.
4. Нажмите **Установить из хранилища (Install from storage)** и выберите **`iPhone_Boot_Magisk.zip`**.
5. После установки нажмите **Перезагрузить (Reboot)**.

*(Примечание: если ваша кастомная прошивка хранит анимацию по пути `/system/product/media/` вместо `/system/media/`, распакуйте архив, перенесите `bootanimation.zip` в папку `system/product/media/` и запакуйте обратно строго **Без сжатия / Store**).*

## Часть 2: Прошивка первого экрана загрузки (`logo_apple.img`)

### Шаг 1: Сделайте бекап родного раздела `logo` (Обязательно)
Откройте **Termux** на телефоне и выполните команды:
```bash
su
dd if=/dev/block/bootdevice/by-name/logo of=/sdcard/Download/logo_stock.img
```
Скопируйте файл `logo_stock.img` из папки `Download` на ПК на случай, если захотите вернуть заводской вид.

### Шаг 2: Прошейте `logo_apple.img` через Fastboot
1. Полностью выключите телефон.
2. Зажмите **Кнопку питания + Громкость вниз**, пока на экране не появится оранжевая надпись **`FASTBOOT`**.
3. Подключите смартфон к ПК по USB-кабелю.
4. Откройте терминал / командную строку в папке с файлом `logo_apple.img` и проверьте подключение:
   ```bash
   fastboot devices
   ```
5. Прошейте новый логотип:
   ```bash
   fastboot flash logo logo_apple.img
   ```
6. Перезагрузите устройство:
   ```bash
   fastboot reboot
   ```

## Как вернуть оригинальный логотип POCO
Если в любой момент захотите вернуть заводскую заставку, загрузитесь в режим Fastboot и прошейте свой бекап:
```bash
fastboot flash logo logo_stock.img
fastboot reboot
```
