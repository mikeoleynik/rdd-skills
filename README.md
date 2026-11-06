# rdd-skills

Скиллы для Research Driven Development: приёмы, которыми уменьшают неопределённость перед существенным решением.

**Research-first** — это инженерная и продуктовая философия, утверждающая, что перед написанием рабочего кода или проектированием архитектуры необходимо исследовать пространство неопределенности, снизить риски и изучить существующий опыт

**Research Driven Development (RDD)** — это системный фреймворк и жизненный цикл управления неопределенностью в разработке, который превращает хаотичные эксперименты в управляемый конвейер генерации проверенных знаний. Если Research-first — это идеология («зачем мы сначала исследуем»), то RDD — это методология («как именно мы это делаем этап за этапом»).

Как принцип, методология, матрица «что × как» и сценарий работы складываются — в [Research-first и RDD](docs/research-driven-development.md).

Каждый скилл пишет артефакт в `.rdd/` того репозитория, где его вызвали.

Плагин обновляется сам. [skills.sh](https://skills.sh) копирует файлы в проект, и их обновляют вручную. На одного агента выбирай один способ: оба сразу поставят каждый скилл дважды.

## Установка

Репозиторий ещё не опубликован. Пока ставится с локального пути:

```bash
npx skills@latest add /home/mikeoil/rdd/rdd-skills
```

После публикации на GitHub адрес в командах ниже — `<owner>/rdd-skills`.

### Cursor и любой агент из skills.sh

```bash
npx skills@latest add <owner>/rdd-skills -a cursor
```

Без `-a` установщик спросит, в какие агенты ставить. Чтобы взять один скилл:

```bash
npx skills@latest add <owner>/rdd-skills --skill five-whys
```

Обновление: `npx skills@latest update`. Новый скилл подхватывается повторным `add`.

### Codex

```bash
codex plugin marketplace add <owner>/rdd-skills
codex plugin add rdd-skills@rdd-skills
```

Обновляется при запуске.

### GitHub Copilot (CLI и VS Code)

```bash
copilot plugin marketplace add <owner>/rdd-skills
copilot plugin install rdd-skills@rdd-skills
```

Один раз добавь в `~/.copilot/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "rdd-skills": {
      "source": { "source": "github", "repo": "<owner>/rdd-skills" },
      "autoUpdate": true
    }
  }
}
```

В VS Code: **Chat: Install Plugin From Source** и URL репозитория.

### Claude Code

```bash
claude plugin marketplace add <owner>/rdd-skills
claude plugin install rdd-skills@rdd-skills
```

Либо тот же `npx skills add`, если нужен редактируемый файл, а не подписка на плагин.

### Gemini CLI

```bash
gemini skills install https://github.com/<owner>/rdd-skills.git --path skills
```

Повтор команды обновляет файлы.

## Скиллы

| Команда | Что пишет |
| --- | --- |
| `/five-whys` | `.rdd/five-whys/<проблема>.md` — цепочка от одного наблюдаемого проявления до причины, на которую можно подействовать, и две меры: на корень и на симптом |
| `/zwicky-box` | `.rdd/zwicky-box/<задача>.md` — ящик Цвикки: параметры, значения, число сочетаний и сырые сочетания, включая странное |
| `/one-pager-hypothesis` | `.rdd/one-pager-hypothesis/<гипотеза>.md` — одна гипотеза, проблема, основания, проверка и наблюдаемые критерии |
| `/fail-fast-checklist` | `.rdd/fail-fast-checklist/<проверка>.md` — ожидание, факт, вердикт, новый факт и следующий шаг |
| `/ishikawa-diagram` | `.rdd/ishikawa-diagram/<эффект>.md` — эффект, категории-кости, причины и разбор кандидатов |
| `/abstraction-laddering` | `.rdd/abstraction-laddering/<формулировка>.md` — лестница формулировки: вверх зачем, вниз как это выглядит |
| `/conflict-resolution-diagram` | `.rdd/conflict-resolution-diagram/<конфликт>.md` — грозовая туча: требования, потребности, общая цель, допущение и решение на обе стороны |
| `/productive-thinking-model` | `.rdd/productive-thinking-model/<проблема>.md` — шесть шагов: ситуация, успех, каталитические вопросы, решение и план ресурсов |
| `/inversion` | `.rdd/inversion/<предмет>.md` — худшее решение, почему оно плохо, и хорошее решение из этих причин |
| `/point-of-view` | `.rdd/point-of-view/<фокус>.md` — кто, в какой ситуации, какая потребность и почему |

Каталог `.rdd/` появляется при первой записи. Его коммитят вместе с репозиторием: следующее решение читает записанное свидетельство.
