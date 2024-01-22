# Семантическая схожесть предложений с использованием векторного представления

## Описание

Этот проект сосредотачивается на измерении семантической схожести между предложениями с использованием векторного представления. В проекте используются предварительно обученная модель векторного представления слов для создания векторов слов и предложений ([en_core_web_md](https://spacy.io/models/en#en_core_web_md)). Схожесть вычисляется с помощью [косинусового коэффициента](https://en.wikipedia.org/wiki/Cosine_similarity).

## Используемые библиотеки

- spaCy
- numpy

## Как работает

1. **Загружаем и импортируем нужные библиотеки**
```python
!pip install spacy -q
!python -m spacy download en_core_web_md
```
```python
import spacy
import numpy as np
nlp = spacy.load("en_core_web_md")
```
2. **Функция преобразования текста в вектор. Вектор предложения вычисляется как средний вектор его токенов.**
```python
def get_text_vector(text):
    doc = nlp(text)
    return doc.vector
```
3. **Функция для нахождения косинусового коэффициента**
```python
def cosine_similarity(vector1, vector2):
    return vector1.dot(vector2) / (vector1_norm := np.linalg.norm(vector1)) / (vector2_norm := np.linalg.norm(vector2))
```
4. **Вычисление схожести двух текстов**
```python
def get_similarity(text1, text2):
  vector1 = get_text_vector(text1)
  vector2 = get_text_vector(text2)
  similarity = cosine_similarity(vector1, vector2)
  return similarity
```

## Примеры
### Похожие предложения
```python
text1 = "I walked with my dog today"
text2 = "Today i will walk in the park with my dog"
get_similarity(text1, text2)
```
```python terminal
>>> 0.7741187
```
### Разные предложения
```python
text1 = "I made sandwitch for breakfast"
text2 = "He washed his car yesterday"
get_similarity(text1, text2)
```
```python terminal
>>> 0.37142923
```
## Запуск кода

Скачайте файл **similarity.ipynb** и запустите его с использованием python-ноутбука ([Jupyter](https://jupyter.org), [Google Colab](https://colab.research.google.com/), [Kaggle](https://www.kaggle.com/) или другие).

Или можете открыть его сразу в Colab:
<br><br>
<a target="_blank" href="https://colab.research.google.com/github/LisiyLexa/Lab2-Semantic-Similarity/blob/main/similarity.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

В данном файле есть форма для проверки текстов:
![form](https://github.com/LisiyLexa/Lab1-Semantic-Similarity/assets/81087786/25d8a7b9-f243-42f4-ab67-86d36a0476e9)
