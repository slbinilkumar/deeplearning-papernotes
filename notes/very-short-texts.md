- Ссылка на статью: [arXiv](http://arxiv.org/abs/1607.00570)

В данной статье предлагается метод для получения векторного представления коротких текстов (10-30 слов).
Семантически близкие тексты должны быть близкими и в векторном пространстве.

Тексты t_1, t_2 считаются похожими, если d(t_1, t_2) < T, где d - функция расстояния (косинусное расстояние,
евклидово расстояние и т.д.), T - порог.

Текст t представляется как взвешенная сумма векторов слов. Подбор оптимальных
весов в этой сумме и является ключевой задачей статьи.

Для подбора весов они предлагают т.н. median-based loss:
берется батч, где в батче половина пар текстов являются похожими, а другая наоборот.
Считается медиана по парам текстов в батче. Далее используя эту медиану они строят
median-based loss (измененная cross-entropy).

Изначально их метод ориентирован на тексты фиксированной длинны. Для работы с
текстами разной длины они предлагают подход с использованием линейной интерполяции.

Данные для оценки качества предложенного метода авторы статьи генерировали
автоматически. Для генерации похожих пар текстов они брали начало параграфа из
википедии, пропускали 2 слова в нем и брали конец параграфа. Для получение
непохожих пар текстов брались параграфы из разных статей.
Также они брали новостные ленты из твиттера - искали похожие по хэштэгам и словам.

Эксперименты показывают не очень большой прирост по сравнению с бэйслайном (подсчет
средне-арифметического векторного представления или min/max по измерениям).
Также имеется плохо документированный код: https://github.com/cedricdeboom/RepresentationLearning
