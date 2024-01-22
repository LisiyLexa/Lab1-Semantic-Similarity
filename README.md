# Семантическая схожесть предложений с использованием векторного представления

## Введение

Данный проект сосредотачивается на измерении семантической схожести между предложениями с использованием векторного представления. В проекте используются предварительно обученная модель векторного представления слов для создания векторов слов и предложений ([en_core_web_md](https://spacy.io/models/en#en_core_web_md)). Схожесть вычисляется с помощью [косинусового коэффициента](https://en.wikipedia.org/wiki/Cosine_similarity).

## Запуск кода

Скачайте файл **similarity.ipynb** и запустите его с использованием python-ноутбука ([Jupyter](https://jupyter.org), [Google Colab](https://colab.research.google.com/), [Kaggle](https://www.kaggle.com/) или другие).

Или можете открыть его сразу в Colab:
<br><br>
<a target="_blank" href="https://colab.research.google.com/github/LisiyLexa/Lab2-Semantic-Similarity/blob/main/similarity.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

В данном файле есть форма для проверки текстов:
![form](https://github.com/LisiyLexa/Lab1-Semantic-Similarity/assets/81087786/25d8a7b9-f243-42f4-ab67-86d36a0476e9)

## Используемые библиотеки

- spaCy
- numpy

## Принцип работы

Я использовал предобученную модель "en_core_web_md" от spaCy. Она была обучена на базе англоязычных новостей, телефонных разговоров, блогов, ток-шоу и т.п.

1. Текст разбивается на токены. _[подробнее о токенайзере spaCy](https://spacy.io/usage/linguistic-features#how-tokenizer-works)_
2. Каждый токен преобразуется в вектор с помощью блока `Tok2Vec`
3. Находится среднее всех векторов. Это и есть векторное представление текста.

Далее нужно сравнить получившиеся вектора. Есть несколько способов сравнить вектора:
- найти евклидовое расстояние между векторами
- найти косинус угла между векторами.

В данной работе используется второй способ.

## Результаты работы
### Пример похожих предложений
```python
text1 = "I walked with my dog today"
text2 = "Today i will walk in the park with my dog"
get_similarity(text1, text2)
```
```python terminal
>>> 0.7741187
```
### Пример разных предложений
```python
text1 = "I made sandwitch for breakfast"
text2 = "He washed his car yesterday"
get_similarity(text1, text2)
```
```python terminal
>>> 0.37142923
```
