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

## Когда какой

Как фазы и подэтапы устроены — в [этапах](docs/stages.md).

### 1.2 Сформулировать проблему

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Point of View](skills/point-of-view/SKILL.md) | Чью проблему мы решаем и почему? | Дизайн-мышление |
| [Идеальный конечный результат](skills/ideal-final-result/SKILL.md) | Какое состояние системы было бы идеальным? | ТРИЗ |
| [Пять почему](skills/five-whys/SKILL.md) | Какая причина стоит за этим проявлением? | Самостоятельные методики |
| [Формы Платона](skills/platonic-forms/SKILL.md) | Что останется, если убрать все случайные черты этих вещей? | |

### 1.3 Сгенерировать гипотезы

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Метод исключения](skills/elimination-method/SKILL.md) | Что будет, если убрать привычный элемент? | Латеральное мышление |
| [Inversion](skills/inversion/SKILL.md) | Как гарантированно сделать хуже, и что из этого следует? | Латеральное мышление |
| [Conflict Resolution Diagram](skills/conflict-resolution-diagram/SKILL.md) | Две стороны тянут в разные стороны, и обе нужны? | ТОС |
| [Zwicky box](skills/zwicky-box/SKILL.md) | Какие сочетания параметров мы ещё не смотрели? | Problem solving |
| [Бисоциация](skills/bisociation/SKILL.md) | Что нового появится, если посмотреть на это двумя разными логиками? | |
| [Концептуальное смешение](skills/conceptual-blending/SKILL.md) | Что появится, если смешать две концепции в одну? | |

### 1.4 Выбрать и сформулировать гипотезу

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Плюс, минус, интересно](skills/plus-minus-interesting/SKILL.md) | Идею пока нельзя ни принять, ни отвергнуть? | Латеральное мышление |
| [How / Now / Wow](skills/how-now-wow/SKILL.md) | Какие идеи оригинальны и насколько легко их реализовать? | Самостоятельные методики |
| [MoSCoW](skills/moscow/SKILL.md) | Насколько необходим каждый элемент для достижения цели? | Самостоятельные методики |
| [RICE](skills/rice/SKILL.md) | Что даст больше эффекта относительно затрат? | Самостоятельные методики |
| [One-pager Hypothesis](skills/one-pager-hypothesis/SKILL.md) | Какое предположение мы можем проверить? | |

### 2.1 Приземлить гипотезу

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Извлечение принципа](skills/principle-extraction/SKILL.md) | Что здесь работает независимо от того, как это сделано? | Латеральное мышление |
| [Фокусирование на различии](skills/focus-on-difference/SKILL.md) | Два похожих случая расходятся, и мы считаем это мелочью? | Латеральное мышление |

### 2.2 Выбрать метод и метрики

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Дизайн эксперимента](skills/design-of-experiment/SKILL.md) | Как проверить один вопрос, не смешав факторы? | |

### Фаза 3. Принять решение

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Fail-fast Checklist](skills/fail-fast-checklist/SKILL.md) | Чему мы научились, если предположение оказалось неверным? | |
| [Плюс, минус, интересно](skills/plus-minus-interesting/SKILL.md) | Идею пока нельзя ни принять, ни отвергнуть? | Латеральное мышление |

### Без этапа

| Фреймворк | Когда применять | Откуда |
| --- | --- | --- |
| [Модель айсберга](skills/iceberg-model/SKILL.md) | Мы видим событие, но не то, что его держит? | Systems thinking |
| [Круги связей](skills/connection-circles/SKILL.md) | Как элементы системы влияют друг на друга? | Systems thinking |
| [Карта понятий](skills/concept-map/SKILL.md) | Как понятия этой темы связаны между собой? | Systems thinking |
| [Уравновешивающая петля обратной связи](skills/balancing-feedback-loop/SKILL.md) | Что возвращает систему к цели, когда она от неё уходит? | Systems thinking |
| [Усиливающая петля обратной связи](skills/reinforcing-feedback-loop/SKILL.md) | Что усиливает само себя от цикла к циклу? | Systems thinking |
| [Шесть шляп](skills/six-thinking-hats/SKILL.md) | Нужно посмотреть на одно решение с разных сторон? | Decision making |
| [Матрица Эйзенхауэра](skills/eisenhower-matrix/SKILL.md) | Что сделать сейчас, что запланировать, а что не делать? | Decision making |
| [Мышление второго порядка](skills/second-order-thinking/SKILL.md) | Что будет после первого следствия решения? | Decision making |
| [Матрица решений](skills/decision-matrix/SKILL.md) | Какой вариант сильнее, если у каждого свои плюсы? | Decision making |
| [Матрица влияние/усилие](skills/impact-effort-matrix/SKILL.md) | Где большой эффект при малом усилии? | Decision making |
| [Лестница умозаключений](skills/ladder-of-inference/SKILL.md) | На каких данных стоит этот вывод? | Decision making |
| [Модель трудного выбора](skills/hard-choice-model/SKILL.md) | Варианты трудно сравнить, и цена ошибки высока? | Decision making |
| [Цикл OODA](skills/ooda-loop/SKILL.md) | Ситуация меняется, и решение надо обновлять по ходу? | Decision making |
| [Cynefin](skills/cynefin-framework/SKILL.md) | Какой это тип ситуации и какой подход ей подходит? | Decision making |
| [Уверенность задаёт скорость или качество](skills/confidence-determines-speed-vs-quality/SKILL.md) | Гнать скорость или держать качество? | Decision making |
| [Ishikawa Diagram](skills/ishikawa-diagram/SKILL.md) | Какие причины могли дать этот эффект? | Problem solving |
| [Abstraction Laddering](skills/abstraction-laddering/SKILL.md) | Формулировка слишком узкая или слишком общая? | Problem solving |
| [Productive Thinking Model](skills/productive-thinking-model/SKILL.md) | Как пройти от ситуации к решению и плану? | Problem solving |
| [Деревья вопросов](skills/issue-trees/SKILL.md) | Проблему надо разложить: почему так или как это сделать? | Problem solving |
| [Первые принципы](skills/first-principles/SKILL.md) | Мы держимся за привычный способ вместо того, что действительно верно? | Problem solving |

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
| `/issue-trees` | `.rdd/issue-trees/<проблема>.md` — дерево «почему» (ветки на весь вопрос и фокус по данным) или дерево «как» (категории решения и идеи) |
| `/first-principles` | `.rdd/first-principles/<проблема>.md` — принципы, которые дальше не делятся, и решение, собранное из них |
| `/ideal-final-result` | `.rdd/ideal-final-result/<проблема>.md` — идеальный конечный результат: функция сама, на существующих ресурсах, отдельно от способа |
| `/six-thinking-hats` | `.rdd/six-thinking-hats/<решение>.md` — одно решение шестью шляпами: выгода, идеи, чувства, данные, худшие ходы и следующий ход |
| `/how-now-wow` | `.rdd/how-now-wow/<набор>.md` — идеи по оригинальности и простоте: Now, Wow, How и обычные трудные |
| `/eisenhower-matrix` | `.rdd/eisenhower-matrix/<набор>.md` — задачи по важности и срочности: сделать, запланировать, делегировать или не делать |
| `/second-order-thinking` | `.rdd/second-order-thinking/<решение>.md` — ближайшие следствия решения и «и что потом?», либо горизонты 10 минут, 10 месяцев и 10 лет |
| `/decision-matrix` | `.rdd/decision-matrix/<решение>.md` — баллы вариантов по факторам, веса и вариант с наибольшей суммой |
| `/design-of-experiment` | `.rdd/design-of-experiment/<эксперимент>.md` — план эксперимента под один вопрос: факторы, дизайн, метрики и допустимый вывод |
| `/moscow` | `.rdd/moscow/<набор>.md` — элементы по необходимости для одной цели: Must, Should, Could и Won't Have |
| `/impact-effort-matrix` | `.rdd/impact-effort-matrix/<набор>.md` — задачи по влиянию и усилию: Quick Wins, Major Projects, Fill-ins и Thankless Tasks |
| `/ladder-of-inference` | `.rdd/ladder-of-inference/<вывод>.md` — ступень вывода, спуск по вопросам к данным и сбор рассуждения вверх |
| `/hard-choice-model` | `.rdd/hard-choice-model/<решение>.md` — тип решения по влиянию исхода и сравнимости вариантов и подход этого типа |
| `/rice` | `.rdd/rice/<набор>.md` — Reach, Impact, Confidence, Effort, балл и порядок инициатив |
| `/elimination-method` | `.rdd/elimination-method/<предмет>.md` — исключённый элемент, последствия и другой способ получить его результат |
| `/ooda-loop` | `.rdd/ooda-loop/<ситуация>.md` — круг наблюдения, ориентировки, решения-гипотезы и действия; следующий круг начинается с обратной связи |
| `/cynefin-framework` | `.rdd/cynefin-framework/<ситуация>.md` — домен ситуации (простой, запутанный, сложный, хаотичный, замешательство) и подход этого домена |
| `/confidence-determines-speed-vs-quality` | `.rdd/confidence-determines-speed-vs-quality/<проблема>.md` — уверенность в важности проблемы и в решении; фокус на скорости, на качестве или на обоих |
| `/iceberg-model` | `.rdd/iceberg-model/<событие>.md` — событие, паттерны во времени, структуры и ментальные модели |
| `/connection-circles` | `.rdd/connection-circles/<система>.md` — до десяти элементов, стрелки прямых причин со знаком и замкнутые петли |
| `/concept-map` | `.rdd/concept-map/<понятие>.md` — вопрос фокуса, сущности от общего к частному и связи, которые читаются фразой |
| `/balancing-feedback-loop` | `.rdd/balancing-feedback-loop/<петля>.md` — цель, фактический уровень, разрыв и корректирующее действие, которое возвращает уровень к цели |
| `/reinforcing-feedback-loop` | `.rdd/reinforcing-feedback-loop/<петля>.md` — переменные, которые усиливают друг друга, выход цикла как вход следующего и внешнее влияние |
| `/bisociation` | `.rdd/bisociation/<проблема>.md` — две матрицы мышления, пересечение механизмов и идея, которой не было ни в одной |
| `/plus-minus-interesting` | `.rdd/plus-minus-interesting/<предмет>.md` — плюсы, минусы и интересные следствия одного объекта и вывод |
| `/principle-extraction` | `.rdd/principle-extraction/<решение>.md` — механизм решения, принцип без исходной реализации и перенос в два контекста |
| `/focus-on-difference` | `.rdd/focus-on-difference/<пара>.md` — общее двух объектов, фокусное различие, усиление, инверсия и гипотеза |
| `/conceptual-blending` | `.rdd/conceptual-blending/<задача>.md` — два входных пространства, родовое пространство, смешение и свойство, которого не было ни в одном |
| `/platonic-forms` | `.rdd/platonic-forms/<область>.md` — формы за воплощениями, что в них неизменно, и пара для следующего хода |

Каталог `.rdd/` появляется при первой записи. Его коммитят вместе с репозиторием: следующее решение читает записанное свидетельство.
