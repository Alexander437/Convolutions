# Свертки

<div align="center">
  <img src="https://www.machinelearningmastery.ru/img/0-106879-17637.jpeg"/>
</div>




Свертки являются ключевым элементом всех нейросетевых моделей для компьютерного зрения. 
На сегодняшний день именно эти модели применяются в:

  - робототехнике (наш случай)
  - системах автоматического управления транспортными средствами
  - фотокамерах современных смартфонов
  - различных системах распознавания текста и цифр на избражении
  - поисковых системах (таких, как Google и Yandex) и т.д.

Пракически во всех нетривиальных задачах машинного зрения на сегодняшний день
используются сверточные нейронные сети, и, если мы сталкиваемся с очередной из 
них, то, скорее всего, она была или будет решена с помощью сверток.

Здесь я попытался наглядно представить свертки. Все картинки - это реальные 
графики сверток нейронной сети ResNet18 (ResNet - одна из самых популярных 
сверочных нейросетей, первая по-насоящему глубокая сеть)

Свертки представляют из себя многомерные массивы. На самом деле в этой 
конструкции нет ничего сложного. Посмотрим на свертки 3х7х7, находящиеся на
нулевом слое сети, после интерполяции (очень грубо говоря сглаживания):


<div align="center">
  <img src="https://github.com/Alexander437/Convolutions/blob/main/Images/conv_3d.png?raw=true"/>
</div>



Как видно, это просто 3 матрицы размером 7х7 (3 маленьких таблички с числами).
Причем каждая матрица применяется к своему каналу (а в исходном RGB-изображении
3 канала: Red, Green, Blue).

Обобщим приведенную свертку. На более глубоких слоях применяются свертки с 
большим количеством каналов (их может быть действительно много: 256, 512...)
Рассмотрим свертку Сх3х3:


<div align="center">
  <img src="https://github.com/Alexander437/Convolutions/blob/main/Images/conv.png?raw=true"/>
</div>



Посмотрим на несколько сверток первого слоя:



<div align="center">
  <img src="https://github.com/Alexander437/Convolutions/blob/main/Images/color_weights_interpolation.png?raw=true"/>
</div>

Если внимательно посмотреть на картинку, становится поняно, что делают свертки:
они выделяют локальные признаки на изображении, такие как линии и точки разных
цветов и форм.

А вот так выглядит множесво сверок на других слоях. Их нужно воспринимать,
как массивы с числами от 0 до 1, где величина числа характеризуется яркостью:


<div align="center">
  <img src="https://github.com/Alexander437/Convolutions/blob/main/Images/filters_resnet.png?raw=true"/>
</div>



Рассмотрим результат работы нейросети.
Здесь нейросеть выделяет ключевые точки, характеризующие позу и жесты человека:


<div align="center">
  <img src="https://github.com/Alexander437/Convolutions/blob/main/Images/cm.png?raw=true"/>
</div>



А здесь нейросеть определяет связи между ключевыми точками:




<div align="center">
  <img src="https://github.com/Alexander437/Convolutions/blob/main/Images/paf.png?raw=true"/>
</div>
