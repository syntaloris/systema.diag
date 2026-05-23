# SYSTEMA.diag

Полнофункциональное одностраничное веб-приложение для детального анализа параметров компьютера, браузера, сети и устройства — прямо в браузере.

---

## 🚀 Быстрый старт

1. Скачай файл `systema_diag.html`
2. Открой его в любом современном браузере (Chrome, Firefox, Edge, Safari)
3. Всё работает офлайн — интернет не нужен

```bash
git clone https://github.com/syntaloris/systema-diag.git
cd systema-diag
# Просто открой systema_diag.html в браузере
```

---

## 📋 Что показывает

### 🖥 Процессор & Нагрузка (`CPU & Load`)

| Параметр | Описание |
|----------|----------|
| **Текущая нагрузка** | Процент загрузки CPU, измеряется через интенсивные вычисления в реальном времени |
| **Логических ядер** | `navigator.hardwareConcurrency` — количество логических процессоров |
| **Архитектура** | x86 / ARM / unknown (из Client Hints API или User Agent) |
| **Оценочная частота** | Эвристическая оценка тактовой частоты через бенчмарк |
| **Платформа (UA)** | `navigator.platform` — платформа из User Agent |
| **Device Memory** | `navigator.deviceMemory` — объём RAM устройства (ГБ) |
| **CPU Class** | Классификация: High-end (8+ ядер) / Mid-range (4–7) / Entry-level (<4) |
| **График нагрузки** | Живой график CPU за последние 60 секунд |

---

### 🧠 Память (`RAM`)

| Параметр | Описание |
|----------|----------|
| **JS Heap Used** | Использованная память JavaScript Heap (Chrome/Edge only) |
| **Всего (Device Memory)** | Общий объём RAM устройства через Device Memory API |
| **JS Heap Limit** | Максимальный лимит JS Heap |
| **JS Heap Allocated** | Выделенная память JS Heap |
| **Storage Quota** | Квота хранилища для origin |
| **Storage Used** | Использованное хранилище |

---

### ⚡ Батарея (`Battery`)

| Параметр | Описание |
|----------|----------|
| **Уровень заряда** | Процент заряда батареи (0–100%) |
| **Статус** | Заряжается / От батареи |
| **Время до полного** | Оценка времени до 100% заряда |
| **Время до разряда** | Оценка времени до 0% заряда |
| **Battery API** | Доступен / Нет / Ошибка |

> ⚠️ Battery API доступен не во всех браузерах (Firefox отключил, Safari ограничил).

---

### 🖼 Экран (Screen Object) — `PHYSICAL`

| Параметр | Описание |
|----------|----------|
| **screen.width** | Физическое разрешение экрана по ширине (пиксели) |
| **screen.height** | Физическое разрешение экрана по высоте (пиксели) |
| **screen.availWidth** | Доступная ширина (без панели задач/дока) |
| **screen.availHeight** | Доступная высота (без панели задач/дока) |
| **screen.availLeft** | Отступ слева от начала виртуального экрана |
| **screen.availTop** | Отступ сверху от начала виртуального экрана |
| **screen.colorDepth** | Глубина цвета (обычно 24-bit) |
| **screen.pixelDepth** | Глубина пикселя (обычно 24-bit) |
| **Ориентация** | Тип ориентации: `landscape-primary`, `portrait-primary` и т.д. |
| **Угол поворота** | Угол поворота экрана в градусах (0, 90, 180, 270) |
| **Мониторов** | Эвристика количества мониторов по `availLeft/availTop` |

> 💡 **Важно:** `screen.width/height` показывают **физическое разрешение** монитора. `window.innerWidth/Height` — размер видимой области браузера. Это разные вещи.

---

### 📐 Viewport & Окно — `VIEWPORT`

| Параметр | Описание |
|----------|----------|
| **window.innerWidth** | Ширина viewport'а (видимая область контента) |
| **window.innerHeight** | Высота viewport'а |
| **window.outerWidth** | Ширина всего окна браузера (с рамками и панелями) |
| **window.outerHeight** | Высота всего окна браузера |
| **window.screenLeft / screenX** | Позиция окна по X на экране |
| **window.screenTop / screenY** | Позиция окна по Y на экране |
| **window.devicePixelRatio** | Соотношение физических пикселей к CSS-пикселям |
| **Visual Viewport** | Размер визуального viewport'а (с учётом зума) |
| **Visual Scale** | Текущий масштаб страницы |
| **Visual Offset** | Смещение visual viewport относительно layout viewport |
| **Aspect Ratio** | Соотношение сторон viewport'а + классификация |

---

### 🎨 Цвет & Медиа — `MEDIA`

| Параметр | Описание |
|----------|----------|
| **Color Scheme** | Предпочтение пользователя: Dark / Light |
| **Reduced Motion** | Пользователь предпочитает уменьшенную анимацию |
| **High Contrast** | Высокий контраст включён |
| **Forced Colors** | Принудительные цвета системы |
| **Inverted Colors** | Инвертированные цвета |
| **Monochrome** | Монохромный режим |
| **HDR / Dynamic Range** | Поддержка HDR-контента |
| **Display Mode** | Режим отображения: Browser / Standalone (PWA) / Fullscreen |
| **Pointer / Hover** | Тип указателя: fine (мышь) / coarse (тач) + hover поддержка |
| **PPI (estimate)** | Плотность пикселей на дюйм (эвристика через DPR) |

---

### 🎮 GPU Рендерер — `RENDERER`

| Параметр | Описание |
|----------|----------|
| **Unmasked Renderer** | Реальное имя видеокарты (через `WEBGL_debug_renderer_info`) |
| **Unmasked Vendor** | Реальный vendor GPU |
| **WebGL Version** | Версия WebGL контекста |
| **GLSL Version** | Версия шейдерного языка |
| **Vendor (masked)** | Маскированный vendor (без расширения) |
| **Renderer (masked)** | Маскированный renderer |
| **Hardware Accel** | Аппаратное ускорение включено |
| **WebGL Context** | WebGL 1.0 / 2.0 |
| **Extensions Count** | Количество доступных WebGL-расширений |

> ⚠️ В некоторых браузерах `WEBGL_debug_renderer_info` заблокировано для приватности — тогда показывается "Заблокировано".

---

### 📐 WebGL Limits — `LIMITS`

| Параметр | Описание |
|----------|----------|
| **Max Texture Size** | Максимальный размер 2D-текстуры |
| **Max Viewport** | Максимальные размеры viewport'а |
| **Max Cube Map** | Максимальный размер cubemap-текстуры |
| **Max Renderbuffer** | Максимальный размер renderbuffer |
| **Max Anisotropy** | Максимальная анизотропная фильтрация |
| **Max Draw Buffers** | Максимальное количество буферов рендеринга |
| **Max Color Attachments** | Максимум color attachments |
| **Max Samples (MSAA)** | Максимальное количество сэмплов для MSAA |
| **Max 3D Texture** | Максимальный размер 3D-текстуры (WebGL2) |

---

### 🔢 WebGL Shaders — `SHADERS`

| Параметр | Описание |
|----------|----------|
| **Max Vertex Attribs** | Максимум vertex attributes |
| **Max Vertex Uniforms** | Максимум uniform-переменных в vertex shader |
| **Max Fragment Uniforms** | Максимум uniform-переменных в fragment shader |
| **Max Varying Vectors** | Максимум varying-векторов |
| **Max Tex Units (FS)** | Максимум texture image units во fragment shader |
| **Max Tex Units (VS)** | Максимум texture image units в vertex shader |
| **Max Combined Tex** | Общий максимум texture units |
| **Aliased Point Size** | Диапазон размеров точек |
| **Aliased Line Width** | Диапазон ширины линий |

---

### 💻 ОС & Платформа — `OS`

| Параметр | Описание |
|----------|----------|
| **ОС (detected)** | Автоматически определённая ОС по User Agent + Client Hints |
| **ОС (UserAgentData)** | ОС из `navigator.userAgentData.platform` (Client Hints API) |
| **Платформа** | `navigator.platform` — платформа из UA |
| **User Agent** | Полная строка User Agent |
| **App Version** | `navigator.appVersion` |
| **App CodeName** | `navigator.appCodeName` |
| **Product** | `navigator.product` |
| **Product Sub** | `navigator.productSub` |
| **Vendor** | `navigator.vendor` |
| **Build ID** | `navigator.buildID` (Firefox) |
| **oscpu** | `navigator.oscpu` (Firefox-only) |

---

### 🔧 Устройство & Железо — `DEVICE`

| Параметр | Описание |
|----------|----------|
| **CPU Cores** | Количество логических ядер |
| **Device RAM** | Объём RAM устройства (ГБ) |
| **Max Touch Points** | Максимальное количество одновременных касаний |
| **Touch Support** | Поддержка тач-ввода |
| **Keyboard API** | Доступность Keyboard API |
| **Virtual Keyboard** | Доступность Virtual Keyboard API |
| **PDF Viewer** | Встроенный / внешний PDF-просмотрщик |
| **WebDriver** | Обнаружение автоматизации (Selenium/Puppeteer) |
| **Standalone (PWA)** | Запущено ли как PWA |
| **Mobile** | Определение мобильного устройства |
| **Tablet** | Определение планшета |

---

### 🕒 Время & Локаль — `TIME`

| Параметр | Описание |
|----------|----------|
| **Timezone** | Часовой пояс (IANA, например `Europe/Moscow`) |
| **Timezone Offset** | Смещение от UTC в часах |
| **Locale Date** | Текущая дата в локальном формате |
| **ISO String** | Дата в ISO 8601 формате |
| **Performance.now()** | Время с момента загрузки страницы (высокоточное) |
| **Epoch Time** | Unix timestamp (миллисекунды с 1970) |
| **Intl.DateTimeFormat** | Поддержка форматирования дат |
| **Intl.NumberFormat** | Поддержка форматирования чисел |
| **Intl.Collator** | Поддержка сравнения строк |
| **Intl.PluralRules** | Поддержка правил множественного числа |
| **Intl.RelativeTime** | Поддержка относительного времени |

---

### 🌐 Соединение — `NET`

| Параметр | Описание |
|----------|----------|
| **Effective Type** | Эффективный тип сети: `4g`, `3g`, `2g`, `slow-2g` |
| **Downlink** | Предполагаемая скорость скачивания (Mbps) |
| **Downlink Max** | Максимальная скорость скачивания |
| **RTT (Ping)** | Round-trip time в миллисекундах |
| **Save Data** | Включён ли режим экономии трафика |
| **Connection Type** | Тип подключения: `wifi`, `cellular`, `ethernet` и т.д. |
| **Онлайн** | Есть ли интернет-соединение |
| **Local IP (WebRTC)** | Локальный IP-адрес через WebRTC ICE |
| **Network Info API** | Доступен ли Network Information API |

---

### 📡 URL & Протокол — `URL`

| Параметр | Описание |
|----------|----------|
| **Протокол** | `http:` / `https:` / `file:` и т.д. |
| **Хост** | Хост и порт текущей страницы |
| **Порт** | Порт (443 для HTTPS, 80 для HTTP) |
| **Путь** | Путь URL |
| **Secure Context** | Запущено ли в secure context |
| **Referrer** | Referrer текущей страницы |
| **CSP** | Есть ли Content Security Policy |
| **Feature Policy** | Доступен ли Feature Policy |
| **Permissions Policy** | Доступен ли Permissions Policy |

---

### ⏱ Performance Timing — `TIMING`

| Параметр | Описание |
|----------|----------|
| **TTFB** | Time To First Byte — время до первого байта ответа |
| **DNS Lookup** | Время DNS-разрешения |
| **TCP Connect** | Время TCP-handshake |
| **SSL Handshake** | Время TLS/SSL-handshake |
| **Response Time** | Время получения ответа |
| **DOM Processing** | Время обработки DOM |
| **Load Event** | Время до события `load` |
| **Total Resources** | Количество загруженных ресурсов |
| **Navigation Type** | Тип навигации: `navigate`, `reload`, `back_forward` |

---

### 🌍 Браузер — `APP`

| Параметр | Описание |
|----------|----------|
| **Язык** | Предпочтительный язык пользователя |
| **Языки (все)** | Все предпочтительные языки |
| **Кодировка** | Кодировка документа |
| **Cookies** | Включены ли cookies |
| **Do Not Track** | Запрос на отслеживание |
| **PDF Viewer** | Тип PDF-просмотрщика |
| **WebDriver** | Обнаружение автоматизации |
| **Standalone (PWA)** | Режим PWA |
| **Java Enabled** | Включён ли Java |

---

### 🔒 Безопасность — `SEC`

| Параметр | Описание |
|----------|----------|
| **Secure Context** | Secure context (HTTPS / localhost / file) |
| **HTTPS** | Используется ли HTTPS |
| **Sandbox** | Есть ли sandbox-политика |
| **CSP** | Content Security Policy |
| **Permissions Policy** | Permissions Policy (бывший Feature Policy) |
| **Credential Mgmt** | Credential Management API |
| **WebAuthn** | Web Authentication API (FIDO2) |
| **Payment Handler** | Payment Handler API |
| **Clipboard Read** | Чтение буфера обмена |
| **Clipboard Write** | Запись в буфер обмена |

---

### 📦 Хранилища — `STORE`

| Параметр | Описание |
|----------|----------|
| **LocalStorage** | Доступен ли localStorage |
| **SessionStorage** | Доступен ли sessionStorage |
| **IndexedDB** | Доступен ли IndexedDB |
| **Quota** | Квота хранилища |
| **Usage** | Использованное хранилище |
| **Persisted** | Сохраняется ли хранилище при очистке |
| **Cache API** | Cache API для Service Workers |
| **OPFS** | Origin Private File System |
| **Origin Private FS** | Альтернативная проверка OPFS |

---

### 🎵 Аудио — `AUDIO`

| Параметр | Описание |
|----------|----------|
| **AudioContext** | Доступен ли Web Audio API |
| **Sample Rate** | Частота дискретизации (Hz) |
| **Max Channels** | Максимальное количество аудиоканалов |
| **State** | Состояние AudioContext |
| **Base Latency** | Базовая задержка аудио |
| **Output Latency** | Задержка вывода |
| **SinkId** | ID аудиовыхода |
| **Audio Output Select** | Возможность выбора аудиовыхода |

---

### 📹 Видео & Камера — `VIDEO`

| Параметр | Описание |
|----------|----------|
| **WebRTC** | Доступен ли WebRTC |
| **getUserMedia** | Доступен ли доступ к камере/микрофону |
| **MediaRecorder** | Доступна ли запись медиа |
| **Picture-in-Picture** | Доступен ли PiP режим |
| **Canvas captureStream** | Захват canvas как видеопоток |
| **ImageCapture** | API для захвата изображений с камеры |
| **WebCodecs** | Низкоуровневый API для кодеков |
| **MediaSource** | Media Source Extensions (DASH/HLS) |

---

### 📡 Геолокация & Сенсоры — `SENSORS`

| Параметр | Описание |
|----------|----------|
| **Широта / Долгота** | GPS-координаты (по кнопке) |
| **Точность** | Точность позиционирования в метрах |
| **Device Orientation** | API ориентации устройства |
| **Device Motion** | API движения устройства |
| **Ambient Light** | Датчик освещённости |
| **Proximity** | Датчик приближения |

> ⚠️ Геолокация требует разрешения пользователя. Остальные сенсоры — только на мобильных устройствах.

---

## ⚠️ Ограничения

| Функция | Ограничение |
|---------|-------------|
| **Температура CPU** | ❌ Недоступна в браузере (требует нативный доступ) |
| **Напряжение / вентиляторы** | ❌ Недоступна в браузере |
| **Использование RAM** | ⚠️ Только JS Heap (Chrome/Edge), не общая RAM |
| **Батарея** | ⚠️ Firefox отключил Battery API |
| **GPU Renderer** | ⚠️ Может быть заблокирован для приватности |
| **Геолокация** | ⚠️ Требует разрешения пользователя |
| **WebRTC IP** | ⚠️ Может не работать при блокировке WebRTC |
