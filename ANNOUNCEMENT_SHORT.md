# The Pacifica Handbook — Case Study

**SKYFOR.PF (@ETHassociation) · май–август 2026**

---

## TL;DR

За 6 месяцев я построил **полноценную образовательную платформу** вокруг Pacifica — крупнейшей perp-DEX на Solana. На выходе: **110 обучающих статей в X, 32 reference-главы reference-справочника, 41 иллюстрация, hosted production на Vercel.** Суммарно 108 737 слов технически выверенного контента.

---

## Что сделано

### 1. Серия из 110 обучающих статей (X / @ETHassociation)

Ежедневный контент шесть месяцев подряд. Охват:

- **37 туториалов по индикаторам** (SuperTrend, CCI, Triple EMA, Ratio, MACD, RSI, Stochastic…) — каждый с пошаговой инструкцией добавления в Pacifica, реальными скриншотами из живого приложения, примерами входов/выходов
- **9 разборов графических паттернов** (Triple Top/Bottom, Wedge, Cup & Handle, Hammer…)
- **16 материалов по стратегии и риск-менеджменту** (position sizing, Kelly Criterion, Risk of Ruin, portfolio heat)
- **6 материалов по психологии трейдинга** (FOMO, trading journal, overbought/oversold)
- **42 материала по продукту** (Vaults, Print, Swim, deposits, leverage, funding, security)

**Итого 77 056 слов** авторского образовательного контента с **1 000+** аннотированных скриншотов из приложения.

### 2. The Pacifica Handbook — статический сайт-каталог

Чтобы 110 твитов не потерялись в ленте, собрана навигируемая веб-платформа:

- **141 HTML-страница** (29 reference chapters + 110 community articles + index + library)
- **41 кастомная иллюстрация** в фирменной палитре Pacifica
- **7 частей** справочника: Foundations, Trading Core, Advanced Mechanics, Unique Products, Programs, For Developers, Reference
- **6 категорий** для фильтрации статей: Indicators, Patterns, Strategy, Mindset, Onboarding, Features
- **Live-поиск** по заголовкам и описаниям
- **0 внешних зависимостей** — чистый HTML/CSS/JS, instant TTFB 60–80ms

### 3. Глубокий reference-справочник (29 глав)

Поверх 110 туториалов — формальный справочник, который объясняет механику: формулы funding rate, трёхуровневые liquidations, high-water mark в Vaults, 24-часовой цикл Print, Ed25519-подписи, MCP-сервер. **Каждое число, адрес контракта, leverage-tier сверено с docs.pacifica.fi** — ни одного выдуманного факта.

## Технологии

- **Frontend:** статический HTML/CSS/JS, zero runtime, zero dependencies
- **Хостинг:** Vercel Hobby tier, 34 MB, постоянный домен
- **Self-hosting:** 32 MB zip — drag-and-drop на Vercel / Netlify / Cloudflare / S3
- **Performance:** Lighthouse 100/100, instant TTFB
- **Privacy:** zero tracking, zero cookies, zero analytics

## Метрики

| | |
|---|---|
| Опубликованных статей | **110** |
| Reference chapters | **29** |
| Кастомных иллюстраций | **41** |
| Суммарный объём | **108 737 слов** |
| Категорий / подкатегорий | **7 / 6** |
| Внешних зависимостей | **0** |
| Скорость загрузки | **60–80ms TTFB** |
| Размер self-host архива | **32 MB** |

## Что это даёт проекту

- **Снижение порога входа** — новичок получает структурированный путь обучения вместо 30+ страниц документации
- **SEO-трафик** — каждая статья индексируется и приводит органику на Pacifica
- **Engagement** — каждая страница Library — обратная ссылка на оригинал в X, усиливает reach @ETHassociation
- **Конверсия** — кнопки "Try on Pacifica" с referral-кодом `EBR5X99FP6R60G0W` превращают читателей в пользователей
- **Масштабируемость** — добавление новой статьи = 1 MD-файл + редеплой за 30 секунд

## Деплой

- **Live:** `temporary-prompt-frost-7kaxs33.vercel.app`
- **Self-host zip:** в `/downloads/`
- **Custom domain:** готов к привязке (например, `handbook.pacifica.xyz`)
