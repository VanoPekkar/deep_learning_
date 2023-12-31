# Глубокое обучение, кейс 1. Распознавание Дорожных Знаков. Команда 31

## Содержание

- `train_models.ipynb` - ноутбук с обучением моделей
- `roboflow.ipynb` - загрузка модели в roboflow
- `dataset` - папка с набором данных для обучения

## Датасет

В качестве датасета был выбран [открытый датасет с kaggle](https://www.kaggle.com/datasets/valentynsichkar/traffic-signs-dataset-in-yolo-format/data). Он содержит размеченные изображения с видеорегистратора. Разметка включает в себя положение знаков на изображении и принадлежность к одному из 4 классов:

1. Запрещающий (prohibitory)
2. Опасность (danger)
3. Обязывающий (mandatory)
4. Другое (other)

## Процесс обучения

В качестве моделей тестировались модели из библиотеки [Ultralytics](https://www.ultralytics.com/). Для тестов использовались 3 модели:

1. [YOLO8 nano](https://docs.ultralytics.com/models/yolov8/)
2. [YOLO8 small](https://docs.ultralytics.com/models/yolov8/)
3. [RTDETR-L](https://docs.ultralytics.com/models/rtdetr/)

Для всех моделей был проведен подбор гиперпараметров. Подробные результаты можно найти в отчетах wandb:

1. [Отчет YOLO8 nano](https://api.wandb.ai/links/burobaslo/avuj848m)
2. [Отчет YOLO8 small](https://api.wandb.ai/links/burobaslo/2i9835hj)
3. [Отчет RTDETR-L](https://api.wandb.ai/links/burobaslo/l6qmye4t)

## Результаты

В таблице ниже представлены результаты пяти экспериментов для каждой из моделей с лучшим набором гиперпараметров с точки зрения метрики mAP50.

| Модель    | precision | recall | mAP50 | скорость (мс) | 
|-----------|---------------|---------------|---------------|---------------|
| yolo8n    | 0.9     | 0.854     | 0.91     | 3.32     |
| yolo8s    | 0.952     | 0.922     | 0.964     | 4.92     |
| rtdetr-l  | 0.972     | 0.948     | 0.978     | 17.65     |

В качестве финальной модели, на которой достигается баланс между скоростью и качеством, была выбрана yolo8s.

## Демонстрация

Для демонстрации работы используется сервис Roboflow. Протестировать модель на изображениях или видео с youtube можно по [ссылке](https://universe.roboflow.com/burobaslo/yolo8s_signs/model/2).


