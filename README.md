# ДЬЯОЛ — Трекер Устройств по IMEI

Симулятор отслеживания устройств по номеру IMEI. **Только симуляция** — реального отслеживания нет.

## Возможности

- Цветной ASCII баннер
- Проверка IMEI (15 цифр)
- Анимация отслеживания с прогресс-баром
- Фейковая анимация силы сигнала
- Интерактивная ASCII карта со сканированием
- Запрос оплаты в USDC (5 минут обратный отсчёт)
- Сохранение результатов в `tracking_result.json`
- Локации: Кения/Танзания (97% Танзания)
- Обфусцированный исходный код

---

## Как скомпилировать и запустить

### Linux / macOS

**Шаг 1: Установите GCC (если нет)**

Ubuntu/Debian:
```bash
sudo apt update
sudo apt install gcc -y
```

Fedora:
```bash
sudo dnf install gcc -y
```

Arch Linux / Manjaro:
```bash
sudo pacman -S gcc
```

macOS (установите Xcode Command Line Tools):
```bash
xcode-select --install
```

**Шаг 2: Скомпилируйте**

```bash
gcc -o imei_track imei_track.c
```

**Шаг 3: Запустите**

```bash
./imei_track
```

**Быстрый тест (пайпом):**
```bash
echo "356938035643809" | ./imei_track
```

---

### Windows (WSL — рекомендуется)

WSL (Windows Subsystem for Linux) уже есть в Windows 10/11.

**Шаг 1: Включите WSL (если не включён)**

Откройте CMD от администратора:
```cmd
wsl --install
```
Перезагрузите компьютер. При первом запуске WSL запросит имя пользователя и пароль.

**Шаг 2: Установите GCC в WSL**

Откройте WSL и выполните:
```bash
sudo apt update
sudo apt install gcc -y
```

**Шаг 3: Скопируйте файл imei_track.c в папку Windows**

Например, в `C:\Users\ВашеИмя\Desktop\`

**Шаг 4: В WSL перейдите в эту папку и скомпилируйте**

```bash
cd /mnt/c/Users/ВашеИмя/Desktop/
gcc -o imei_track imei_track.c
```

**Шаг 5: Запустите**

```bash
./imei_track
```

---

### Windows (Visual Studio — если уже установлен)

**Шаг 1: Откройте "Developer Command Prompt for VS"**

Найдите в меню Пуск.

**Шаг 2: Скомпилируйте**

```cmd
cl imei_track.c
```

**Шаг 3: Запустите**

```cmd
imei_track.exe
```

---

### Windows (онлайн компилятор — без установки)

**Шаг 1: Откройте браузер**

Перейдите на https://www.onlinegdb.com/online_c_compiler

**Шаг 2: Вставьте код**

Скопируйте содержимое `imei_track.c` в редактор.

**Шаг 3: Нажмите "Run"**

Программа запустится в браузере.

**Шаг 4: Скачайте .exe (опционально)**

Нажмите "Download" для получения исполняемого файла.

---

### Windows (MinGW — портативный, без установки)

**Шаг 1: Скачайте MinGW**

Перейдите на https://github.com/niXman/mingw-builds-binaries/releases
Скачайте архив с `x86_64` и `posix` в названии.

**Шаг 2: Распакуйте**

Распакуйте, например, в `C:\mingw64`

**Шаг 3: Добавьте в PATH**

Откройте CMD:
```cmd
set PATH=C:\mingw64\bin;%PATH%
```

Или добавьте permanently: ПКМ по "Этот компьютер" → Свойства → Доп. параметры → Переменные среды → Path → Добавить `C:\mingw64\bin`

**Шаг 4: Скомпилируйте**

```cmd
gcc -o imei_track.exe imei_track.c
```

**Шаг 5: Запустите**

```cmd
imei_track.exe
```

---

## Файлы

| Файл | Описание |
|------|----------|
| `imei_track.c` | Исходный код (分享 этот файл) |
| `imei_track` | Скомпилированный бинарник (Linux) |
| `imei_track.exe` | Скомпилированный бинарник (Windows) |
| `tracking_result.json` | Результаты (создаётся автоматически) |
| `README.md` | Эта инструкция |

## Тестовые IMEI

```
356938035643809
123456789012345
987654321098765
```

## Формат JSON

Результаты сохраняются в `tracking_result.json`:
```json
{
  "timestamp": "2026-06-27T13:08:37",
  "imei": "356938035643809",
  "carrier": "Vodacom TZ",
  "status": "Онлайн",
  "cell_id": "0xD788",
  "lac": "0xD321",
  "location": {
    "country": "Танзания",
    "city": "Dar es Salaam",
    "country_code": "+255",
    "latitude": -6.792400,
    "longitude": 39.208300,
    "lat_dir": "N",
    "lon_dir": "E"
  },
  "signal": {
    "frequency": 983,
    "network": "LTE",
    "band": 9
  },
  "simulation": true
}
```

## Отказ от ответственности

Этот инструмент предназначен **только для образовательных и симуляционных целей**. Он не выполняет реальное отслеживание устройств. Все данные случайны и вымышлены.
