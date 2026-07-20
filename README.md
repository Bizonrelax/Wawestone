# Wawestone ♟️

[Русский](#русский) | [English](#english)

---

## Русский

### Короткое описание
**Wawestone** — экспериментальный шахматный движок, основанный на отказе от перебора вариантов и статического веса фигур. Проект исследует возможность свернуть дерево игры через выявление аналитических инвариантов геометрии доски.

### 💡 Идея проекта
В отличие от классического подхода (рекурсивный перебор ходов или эвристическая оценка нейросетей), данный движок рассматривает позицию как систему взаимодействующих пространств. Каждое пространство содержит множество **мономов** — потенциальных векторов движения без учёта текущих препятствий.

Ключевая метрика — **Сила Клеточного Спектра (СКС)**. Она отражает распределение количества фигур, способных достичь каждой клетки за $k$ ходов при условии абсолютной прозрачности поля (правило КСТ). Многоуровневый анализ СКС позволяет выявлять скрытые темповые преимущества и детерминированно предсказывать исход эндшпиля без построения классического дерева вариантов.

### ⚡ Преимущества и особенности
* **Вычислительная скорость:** Оценка позиции сводится к эффективным операциям над битовыми масками, исключая ресурсоемкий рекурсивный поиск.
* **Математическая прозрачность:** Алгоритм полностью детерминирован. Логика оценки прозрачна и объяснима на любом этапе.
* **Энергетический подход:** Сила позиции измеряется исключительно динамической достижимостью клеток, а не номинальной ценностью фигур.
* **Низкие системные требования:** Движок оптимизирован для работы на одном процессорном ядре с минимальным потреблением памяти.

### 🛠️ Текущие ограничения (Стадия PoC)
> ⚠️ **Важно:** Проект находится на этапе исследования математического концепта.

* На данный момент реализован только простейший эндшпиль $K+P \text{ vs } K$.
* Модели СКС-слоев пока рассчитывают статический потенциал и не учитывают взаимные блокировки или строгую очерёдность хода.
* Алгоритм ТУР использует упрощённую модель ключевых полей и пока не покрывает все тонкости оппозиции королей.
* Графический интерфейс разработан исключительно для визуальной отладки.

### 🚀 Перспективы развития
1. Расширение математической модели на все типы фигур и полную шахматную доску.
2. Реализация гибридного режима: глубокая статическая СКС-оценка в связке с ультра-неглубоким тактическим фильтром.
3. Применение в обучении: генерация тепловых карт контроля полей на основе СКС для визуального анализа партий.

### 📝 Лицензия
Проект распространяется под лицензией **The Unlicense**. Вы можете свободно копировать, изменять, публиковать, использовать, компилировать, продавать или распространять этот софт в любой форме — как в виде исходного кода, так и в виде скомпилированной программы. *Делай что хочешь.*

---

## English

### Short Description
**Wawestone** is an experimental chess engine that rejects move-tree search and traditional piece values. The project explores the possibility of collapsing the game tree by identifying analytical invariants of the board's geometry.

### 💡 Core Concept
Unlike the traditional approach (recursive move-tree generation or neural network heuristic evaluation), this engine treats a chess position as a system of interacting spaces. Each space contains a set of **monomials** — potential movement vectors without considering current obstacles.

The key metric is **Cellular Spectrum Strength (CSS)**. It represents the distribution of the number of pieces capable of reaching each square in $k$ moves, assuming absolute transparency of the field (the CST rule). Multilayered CSS analysis reveals hidden tempo advantages and deterministically predicts endgame outcomes without building a classic search tree.

### ⚡ Key Features
* **Computational Speed:** Position evaluation is reduced to efficient bitmask operations, eliminating resource-intensive recursive searches.
* **Mathematical Transparency:** The algorithm is fully deterministic. The evaluation logic is clear and explainable at any given step.
* **Energy-Based Approach:** Position strength is measured solely by dynamic square reachability rather than the nominal value of the pieces.
* **Low System Resource Usage:** The engine is optimized to run effectively on a single CPU core with minimal memory footprint.

### 🛠️ Current Limitations (PoC Stage)
> ⚠️ **Note:** The project is currently a mathematical proof of concept.

* Only the basic $K+P \text{ vs } K$ endgame is currently implemented.
* The CSS layer models calculate static potential and do not yet account for pieces blocking each other or strict turn order.
* The TUR algorithm uses a simplified model of key squares and does not yet cover all the nuances of king opposition.
* The graphical user interface is minimal and intended solely for debugging purposes.

### 🚀 Future Roadmap
1. Scaling the mathematical model to all piece types and the full chess board.
2. Implementing a hybrid mode: combining deep static CSS evaluation with an ultra-shallow tactical filter.
3. Educational application: generating control-zone heatmaps based on CSS for visual game analysis.

### 📝 License
This project is released under **The Unlicense**. You are free to copy, modify, publish, use, compile, sell, or distribute this software in any form — either as source code or as a compiled binary, for any purpose, commercial or non-commercial. *Do whatever you want.*
