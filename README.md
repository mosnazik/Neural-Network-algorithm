# Neural-Network-algorithm
## Задачи со спецкурса по темам:
1. Построение с помошью простых нейронных сетей, типа Sequential и полносвязными слоями, регрессионной модели.
   - [X] ***Задача*** Прогнозирование цилиндрической змеи в 3d с помощью разного количества Dense слоёв.
2. С использованием предобученных нейронных сетей, которые необходимо дообучить на своих данных, получить вектора фичей, для которых использовать стандартные алгоритмы машинного обучения.
   - [X] ***Задача*** С помощью сети VGG16 получается вектор фичей для набора Fashion MNIST, который кластеризуется с помощью KMeans. 
3. Классификатор с помощью чисто нейронных сетей.
   - [X] ***Задача*** С помощью добавления слоев к VGG и обучения на данных Fashion MNIST сделать нейронную сеть, которая классифицирует одежду.
4. Используя разные нейронные сети для работы с изображениями, написать алгоритм определения объекта на изображении. Нарисовать прямоугольную рамку и класс объекта на изображении.
   - [X] ***Задача*** С помошью сети YOLO, обученной на данных одежды, написан алгоритм выделяющий рамкой одежду на изображении с категорией и вероятностью. 
5.  Сегментация изображение. Обведение контура объекта на изображении.
   - [X] ***Задача*** Сегментация одежды с помощью нейронной сети Unet и получение масок изображений.
6. Генерация изображения. Обучение в нейронной сети GAN дискриминатора и генератора итеративно каждый по очереди.
   - [] ***Задача***
## Данные

| Задача | Данные | Откуда |
|---|---|---|
| 1 | Синтетическое облако точек | Генерируется в ноутбуке функцией `cylinder()`, ничего скачивать не нужно |
| 2 | Fashion-MNIST | Скачивается автоматически: `tf.keras.datasets.fashion_mnist.load_data()` |
| 3 | Fashion-MNIST | То же самое |
| 4 | Colorful Fashion Dataset for Object Detection (10 классов одежды, YOLO-разметка) | [Kaggle](https://www.kaggle.com/datasets/nguyngiabol/colorful-fashion-dataset-for-object-detection) |
| 5 | People Clothing Segmentation (1000 изображений, 59 классов, маски) | [Kaggle](https://www.kaggle.com/datasets/rajkumarl/people-clothing-segmentation) |

Предобученные веса (VGG16 ImageNet, `yolov8m.pt`, EfficientNet-B4 ImageNet) скачиваются
автоматически при первом запуске — нужен интернет.

### Как скачать данные

Нужен [Kaggle API-токен](https://www.kaggle.com/docs/api) в `~/.kaggle/kaggle.json`.

```bash
pip install kaggle

# Задача 4
kaggle datasets download -d nguyngiabol/colorful-fashion-dataset-for-object-detection \
    -p data/colorful_fashion --unzip

# Задача 5
kaggle datasets download -d rajkumarl/people-clothing-segmentation \
    -p data/people_clothing --unzip
```

### Ожидаемая структура
 
````
Neural-Network-algorithm/
├── data/
│   ├── colorful_fashion/
│   │   ├── JPEGImages/            # *.jpg
│   │   ├── Annotations_txt/       # *.txt в формате YOLO
│   │   └── ImageSets/Main/
│   │       ├── trainval.txt
│   │       └── test.txt
│   └── people_clothing/
│       ├── labels.csv
│       ├── jpeg_images/IMAGES/    # *.jpeg
│       └── jpeg_masks/MASKS/      # *.jpeg
├── examples/                      # свои картинки для инференса (в репозитории)
└── notebooks/
````
 
Если данные лежат в другом месте, путь можно переопределить переменной окружения:
 
```bash
export DATA_DIR=/path/to/data     # Windows: set DATA_DIR=D:\data
jupyter notebook
```
 
### Окружение
 
Задачи 1–3 используют TensorFlow, задачи 4–5 — PyTorch. Ставить лучше в разные окружения:
 
```bash
pip install -r requirements-tf.txt      # задачи 1-3
pip install -r requirements-torch.txt   # задачи 4-5
```

Со спецкурсом можно ознакомиться по ссылке:https://scs.math.msu.ru/ru/node/5618

Сайт автора курса:http://машинноезрение.рф/
