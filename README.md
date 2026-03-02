# AJTBD Skills for Claude Code

Набор скиллов для проведения продуктовых исследований по методологии **Advanced Jobs To Be Done** прямо из Claude Code.

## Скиллы

| Команда | Назначение |
|---------|-----------|
| `/ajtbd-b2b-segments` | 5 привлекательных B2B-сегментов с Core Jobs, Big Jobs, TAM/SAM/SOM |
| `/ajtbd-b2c-segments` | 5 привлекательных B2C-сегментов с аналогичной структурой |
| `/ajtbd-job-graph` | Граф работ ниже уровнем к Core Job для сегмента |
| `/ajtbd-rat` | Top-5 рискованных предположений (RAT) с карточками рисков |
| `/ajtbd-landing` | Текст лендинга по структуре AJTBD |
| `/ajtbd-recruit` | Каналы и способы рекрута респондентов для интервью |

## Цепочка зависимостей

```
/ajtbd-b2b-segments ──┐
                      ├─→ .ajtbd/segments.md
/ajtbd-b2c-segments ──┘         │
                                ▼
                    /ajtbd-job-graph ──→ .ajtbd/job-graph.md
                                │              │
                    ┌───────────┼──────────────┘
                    ▼           ▼              ▼
            /ajtbd-landing  /ajtbd-rat  /ajtbd-recruit
```

Каждый скилл автоматически проверяет наличие артефактов предыдущих шагов в папке `.ajtbd/` проекта. Если зависимость отсутствует — скилл останавливается и подсказывает, какую команду запустить первой.

## Установка

Скопируйте директории скиллов в `~/.claude/skills/`:

```bash
cp -r ajtbd-*/ ~/.claude/skills/
```

## Использование

1. Откройте Claude Code в директории вашего проекта
2. Начните с сегментации: `/ajtbd-b2b-segments Описание продукта, сайт: example.com`
3. Детализируйте работы: `/ajtbd-job-graph`
4. Далее любой из: `/ajtbd-landing`, `/ajtbd-rat`, `/ajtbd-recruit`

Все результаты сохраняются в `.ajtbd/` вашего проекта.

## Авторство промптов

Промпты созданы Ваней Замесиным и Анной Шундеевой по методологии Advanced Jobs To Be Done.
Курс «Как делать продукт»: https://zamesin.ru/producthowto/
