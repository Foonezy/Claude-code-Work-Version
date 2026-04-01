<div align="center">

<img src="https://capsule-render.vercel.app/api?type=soft&color=0:0d1117,50:161b22,100:21262d&height=200&section=header&text=Claude%20Code&fontSize=70&fontColor=58a6ff&animation=fadeIn&fontAlignY=40&desc=Скомпилированная%20версия.%20Без%20сборки.%20Без%20ожиданий.&descSize=16&descAlignY=70&descColor=8b949e" />

<br>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=20&duration=4000&pause=1000&color=58a6ff&center=true&vCenter=true&width=700&lines=Компилированная+версия+Claude+Code;Просто+запусти+Claude.bat;Работает+из+коробки+—+как+всё+должно+быть" />

</div>

---

<div align="center">

**[О проекте](#о-проекте)** • **[Требования](#требования)** • **[Установка](#установка)** • **[Запуск](#запуск)** • **[Конфигурация](#конфигурация)** • **[Переменные окружения](#переменные-окружения)** • **[Архитектура](#архитектура)** • **[Дисклеймер](#важно)**

</div>

---

## О проекте

<div align="center">

*Иногда вещи появляются там, где их не ждали.*

</div>

<br>

Это — **скомпилированная версия Claude Code**, которая обычно остаётся за замкнутыми дверями корпоративных репозиториев Anthropic. 

Что-то где-то утекло. Кто-то что-то забыл закрыть. Кто-то нажал не ту кнопку. Результат — перед вами: полностью работающий продукт, который обычно требует лицензий, подписок, корпоративных соглашений и пары недель бюрократии.

Здесь ничего этого нет. Только исполняемый файл и честная работа.

Мы не будем делать вид, что это «официальный релиз». Мы не будем притворяться, что всё по правилам. Но мы также не будем притворяться, что это не работает — потому что работает прекрасно.

<br>

<div align="center">

**Ирония судьбы:** *самые качественные инструменты часто оказываются там, где их не ищут.*

</div>

---

## Требования

### Обязательные

| Компонент | Требование | Примечание |
|-----------|------------|------------|
| **API Key Anthropic** | `ANTHROPIC_API_KEY` | Получить на [console.anthropic.com](https://console.anthropic.com) [^14^] |
| **Операционная система** | Windows 10/11 | Для Linux/macOS используйте оригинальный CLI |
| **Интернет-соединение** | Стабильное | Для API-запросов к Anthropic |
| **Кредиты на аккаунте** | Минимум $5 | Пополнение через банковскую карту [^14^] |

### Опциональные

| Компонент | Назначение |
|-----------|------------|
| `CLAUDE_CONFIG_DIR` | Кастомная директория конфигурации |
| `HTTP_PROXY` / `HTTPS_PROXY` | Если работаете через корпоративный прокси [^20^] |

---

## Установка

### 1. Получение API ключа

Перейдите на [console.anthropic.com](https://console.anthropic.com) и создайте аккаунт разработчика:

1. Зарегистрируйтесь / войдите в систему
2. Перейдите в раздел **Settings > Billing**
3. Пополните баланс минимум на **$5** [^14^]
4. Создайте API ключ в разделе **API Keys**
5. **Скопируйте ключ** — он показывается только один раз [^21^]

### 2. Настройка переменных окружения

**Временно (только текущая сессия):**

```cmd
# Windows CMD
set ANTHROPIC_API_KEY=sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# Windows PowerShell
$env:ANTHROPIC_API_KEY="sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
Постоянно (системные переменные):
cmd
Copy
# Откройте System Properties → Advanced → Environment Variables
# Создайте новую переменную пользователя:
# Имя: ANTHROPIC_API_KEY
# Значение: ваш_ключ_api
3. Распаковка архива
bash
Copy
# Распакуйте содержимое в удобную директорию
# Рекомендуется: C:\Tools\Claude\ или %USERPROFILE%\Claude\
Запуск
<div align="center">
<table>
<tr>
<td align="center" width="300" bgcolor="#21262d">
Способ 1: Прямой запуск
</td>
<td align="center" width="400">
bash
Copy
Claude.bat
</td>
</tr>
<tr>
<td align="center" bgcolor="#21262d">
Способ 2: Через терминал
</td>
<td align="center">
bash
Copy
# Перейдите в директорию
cd C:\Tools\Claude

# Запустите
.\Claude.bat
</td>
</tr>
<tr>
<td align="center" bgcolor="#21262d">
Способ 3: С проверкой
</td>
<td align="center">
bash
Copy
# Проверьте, видит ли система API ключ
echo %ANTHROPIC_API_KEY%

# Затем запускайте
Claude.bat
</td>
</tr>
</table>
</div>
Конфигурация
Файлы настроек
Claude Code использует следующие файлы конфигурации :
Table
Файл	Расположение	Назначение
claude.json	~/.claude/ или %USERPROFILE%\.claude\	Глобальные настройки
settings.json	Директория проекта	Локальные настройки проекта
.claude/	Директория проекта	Плагины, хуки, память
Ключевые параметры
JSON
Copy
// ~/.claude/claude.json
{
  "customApiKeyResponses": {
    "approved": ["xxxxxxxxxxxxxxxxxxxx"],
    "rejected": []
  },
  "hasCompletedOnboarding": true,
  "theme": "dark",
  "shiftEnterKeyBindingInstalled": true,
  "autoConnectIde": false,
  "autoInstallIdeExtension": false
}
Переменные окружения
Основные (Authentication)
Table
Переменная	Описание	Пример
ANTHROPIC_API_KEY	API ключ для аутентификации 	sk-ant-api03-...
ANTHROPIC_AUTH_TOKEN	Кастомный токен авторизации	Bearer токен
ANTHROPIC_BASE_URL	Кастомный endpoint (для прокси) 	https://proxy.company.com
Модели и производительность
Table
Переменная	Описание	Значения
CLAUDE_CODE_MAX_OUTPUT_TOKENS	Максимум токенов в ответе	4096, 8192, 16384
CLAUDE_CODE_MAX_RETRIES	Количество ретраев при ошибках API	10 (по умолчанию)
API_TIMEOUT_MS	Таймаут API запросов	600000 (10 минут)
CLAUDE_CODE_EFFORT_LEVEL	Уровень усилий модели	low, medium, high, max 
Поведение и безопасность
Table
Переменная	Описание
CLAUDE_CODE_DISABLE_TELEMETRY	Отключить телеметрию (1)
CLAUDE_CODE_DISABLE_AUTOUPDATER	Отключить автообновления (1)
CLAUDE_CODE_SUBPROCESS_ENV_SCRUB	Удалить credentials из subprocess (1) 
DISABLE_PROMPT_CACHING	Отключить кэширование промптов (1)
Прокси и сеть
Table
Переменная	Описание
HTTP_PROXY	HTTP прокси сервер
HTTPS_PROXY	HTTPS прокси сервер
CLAUDE_CODE_CLIENT_CERT	Путь к клиентскому сертификату (mTLS)
CLAUDE_CODE_CLIENT_KEY	Путь к приватному ключу 
Архитектура
Что внутри
Table
Компонент	Описание	Технологии
Исполняемое ядро	Скомпилированный бинарник Claude Code	Node.js + pkg
Runtime	Все зависимости Node.js	Встроенный
API Client	Клиент для Anthropic API	Native fetch / axios
Terminal UI	Интерфейс терминала	Ink / React
Claude.bat	Точка входа для Windows	Batch + PowerShell
Структура директорий
plain
Copy
Claude/
├── Claude.bat              # Точка входа
├── bin/
│   └── claude.exe          # Основной бинарник
├── node_modules/           # Встроенные зависимости (read-only)
├── resources/              # Ресурсы и ассеты
└── .claude/                # Конфигурация (создаётся при первом запуске)
    ├── claude.json         # Глобальные настройки
    ├── plugins/            # Плагины MCP
    └── history/            # История сессий
Поток данных
plain
Copy
┌─────────────┐     ┌─────────────┐     ┌─────────────────┐
│  Claude.bat │────→│ claude.exe  │────→│ Anthropic API   │
│  (launcher) │     │ (core)      │     │ api.anthropic.com│
└─────────────┘     └─────────────┘     └─────────────────┘
                           │
                           ↓
                    ┌─────────────┐
                    │  ~/.claude/ │
                    │ (config)    │
                    └─────────────┘
Контекст
<div align="center">
Почему это забавно
</div>

Есть что-то поэтичное в том, как работает мир технологий. Компании тратят миллионы на маркетинг, лицензии, системы контроля доступа. А потом какой-то файл оказывается в неправильной папке, и вся эта инфраструктура превращается в декорации.
Этот репозиторий — не про взлом. Не про кражу. Это про случайность, которая оказалась полезнее маркетинговой машины.
Если вы здесь — значит, вы понимаете ценность инструментов, которые просто работают. Без регистрации, без SMS, без «свяжитесь с отделом продаж».
Важно
<div align="center">
<table>
<tr>
<td align="center" bgcolor="#da3633" style="color: white;">
⚠️ ДИСКЛЕЙМЕР
</td>
</tr>
<tr>
<td>
Правовой статус:
Этот репозиторий содержит скомпилированное программное обеспечение Anthropic
Все права на исходный код и торговые марки принадлежат Anthropic PBC
Автор не претендует на право собственности на Claude Code
Использование:
Только для ознакомительных и образовательных целей
Требуется собственный API ключ Anthropic с оплаченными кредитами
Коммерческое использование рекомендуется через официальные каналы
Безопасность:
Храните ANTHROPIC_API_KEY в безопасности
Не коммитьте ключи в репозитории 
Используйте .env файлы осторожно — Claude Code автоматически загружает их 
Поддержка:
Официальная документация: code.claude.com/docs
Сообщество: GitHub Discussions
</td>
</tr>
</table>
</div>
<div align="center">
<img src="https://capsule-render.vercel.app/api?type=wave&color=0:0d1117,50:161b22,100:21262d&height=120&section=footer&animation=fadeIn" />

<sup><sub>
</div>
