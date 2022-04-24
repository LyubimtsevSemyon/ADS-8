# Алгоритмы и структуры данных (ADS-8)

![GitHub pull requests](https://img.shields.io/github/issues-pr/NNTU-CS/ADS-8)
![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed/NNTU-CS/ADS-8)

Срок выполнения задания:

**до 8 мая** 

![Relative date](https://img.shields.io/date/1652043600)

## Задание

> Написать программную реализацию решения задачи про круговой поезд с лампочками

## Пояснение

Формулировка задачи про поезд:

> Представьте себе замкнутую по окружности железную дорогу. По ней едет поезд, последний вагон которого скреплён с первым так, что внутри можно свободно перемещаться между вагонами. Вы оказались в одном случайном вагоне и ваша задача — подсчитать их общее количество. В каждом вагоне можно включать или выключать свет, но начальное положение переключателей случайное и заранее неизвестно. Все вагоны внутри выглядят строго одинаково, окна закрыты так, что невозможно посмотреть наружу, движение поезда равномерное. Помечать вагоны как-либо, кроме включения или выключения света, нельзя. Количество вагонов конечно.

<img src="./images/train.png" alt="train" width="50%"/>

## Программная реализация

В данной реализации используется класс **Train**, в котором содержится связанный список вагонов (**Cage**)

```cpp
class Train {
 private:
   struct Cage {
      bool light; // состояние лампочки
      Cage *next;
      Cage *prev;
   };
   int countOp; // счетчик шагов (число переходов из вагона в вагон)
   Cage *first; // точка входа в поезд (первый вагон)
 public:
   Train(); 
   void addCage(bool light); // добавить вагон с начальным состоянием лампочки
   int getLength();          // вычислить длину поезда
   int getOpCount();         // вернуть число переходов (из вагона в вагон)
};
```

Поясним основные элементы класса **Train**. Поезд организуется как двусвязный циклический список из вагонов (структура **Cage**). В каждом вагоне мы храним **true**, если свет включен и **false**, если выключен. Поезд может состоять минимум из 2-х вагонов.

При добавлении в поезд вагона мы передаем параметром состояние его лампочки (**addCage**). Метод **getLength** вычисляет длину поезда самым простым (и нерациональным способом!) Движения человека по поезду должны учитываться в переменной **countOp**, в которую заносятся все шаги из вагона в вагон.

Метод **getOpCount** возвращает общее число шагов. 

## Состав проекта

В проект должен входить заголовочный файл **include/train.h**


   
