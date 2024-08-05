# K-means Кластеризация

## Описание

K-means — это популярный алгоритм кластеризации, который делит набор данных на \( k \) кластеров. Цель алгоритма — минимизировать сумму квадратов расстояний между точками данных и центроидами кластеров.

## Применение

K-means может быть использован в различных областях, таких как:

- **Анализ данных**: Группировка данных для выявления скрытых паттернов и сегментов.
- **Распознавание образов**: Кластеризация изображений или звуковых сигналов для их классификации.
- **Обработка текстов**: Группировка документов по темам.
- **Маркетинг**: Сегментация клиентов для персонализированного маркетинга.

## Формулы

### Назначение кластеров

Для каждой точки данных \( x_i \) находим ближайший центроид \( c_j \):

\[ 
j = \arg\min_k \| x_i - c_k \|^2 
\]

где \(\| x_i - c_k \|\) — это Евклидово расстояние между точкой данных \( x_i \) и центроидом \( c_k \).

### Обновление центроидов

Центроиды пересчитываются как среднее значение всех точек, принадлежащих данному кластеру:

\[ 
c_j = \frac{1}{|C_j|} \sum_{x_i \in C_j} x_i 
\]

где \( C_j \) — множество точек, принадлежащих кластеру \( j \), и \( |C_j| \) — количество точек в кластере \( j \).

## Использование

1. Установите зависимости (если необходимо).
2. Запустите `kmeans_analytic.py` для выполнения кластеризации.

### Пример

```python
import numpy as np
from kmeans_analytic import kmeans

# Генерация примерных данных
coords = np.concatenate([np.random.randn(100, 2) + np.array([1, 2]),
                         np.random.randn(100, 2) + np.array([-5, 4]),
                         np.random.randn(150, 2) + np.array([3, -5])], axis=0)

# Количество кластеров
k = 3

# Выполняем кластеризацию
centroids, labels = kmeans(coords, k)

print("Координаты центроидов:", centroids)
print("Метки кластеров:", labels)

# Визуализация
import matplotlib.pyplot as plt

plt.scatter(coords[:, 0], coords[:, 1], c=labels, cmap='viridis')
plt.scatter(centroids[:, 0], centroids[:, 1], c='red', marker='x')
plt.show()



