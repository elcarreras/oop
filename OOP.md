# Экзамен ООП

## 1. Понятие объектно-ориентированного программирования (ООП). Основные принципы ООП. Наследование, агрегация, композиция. Примеры реализации принципов ООП в ЯП C#.
**ООП** - это парадигма программирования, основанная на объектах, которые объединяют данные (поля, свойства) и поведение (методы).

### **4 основынх принципа ООП:**
1)	**Абстракция** – упрощение сложной системы путем выделения наиболее важных характеристик и игнорирования второстепенных. В ООП абстракция реализуется через создание классов, которые представляют собой обобщенные модели объектов.
```C#
// Абстракция (интерфейс)
public interface IShape {
    double GetArea();  // Абстрактный метод
}
```

2) **Инкапсуляция** – скрытие внутренней реализации объекта и предоставления безопасного интерфейса для работы с ним. 
2)	**Наследование** – возможность создать новый класс на основе существующих с повторным использованием кода
работы с ним. 
```C#
// Инкапсуляция и наследование
public class Rectangle : IShape {
    private double _width;  // Инкапсуляция (private поле)
    private double _height;

    public Rectangle(double width, double height) {
        _width = width;
        _height = height;
    }
    
    // Реализация интерфейса
    public double GetArea() => _width * _height;  
}
```
3)	**Полиморфизм** – возможность объектов  одинаковым интерфейсом иметь разную реализацию 
```C#
// Полиморфизм (разные реализации одного интерфейса)
public class Circle : IShape {
    private double _radius;

    public Circle(double radius) => _radius = radius;

    public double GetArea() => Math.PI * _radius * _radius;
}
```
Использование кода принципов ООП вместе:
```C#
// Использование
var canvas = new Canvas();
canvas.AddShape(new Rectangle(10, 20));  // Полиморфизм
canvas.AddShape(new Circle(5));

foreach (var shape in canvas.Shapes) {
    Console.WriteLine($"Area: {shape.GetArea()}");
}
```


### **Наследование, агрегация и композиция:**

1) **Наследование** - класс-наследник (подкласс) получает все поля и методы родительского класса.
```C#
public class Animal {
    public void Eat() => Console.WriteLine("Eating...");
}

public class Dog : Animal {  // Наследование
    public void Bark() => Console.WriteLine("Barking...");
}

var dog = new Dog();
dog.Eat();  // Метод родителя
dog.Bark(); // Свой метод
```
2) **Агрегация** - Объект содержит другой объект, но они могут существовать независимо.
```C#
public class Student {
    public string Name { get; set; }
}

public class University {
    public List<Student> Students { get; set; }  // Агрегация
}
```
3) **Композиция** - Объект владеет другим объектом, и зависимый объект не существует без основного.
```C#
public class Room {
    public string Type { get; set; }
}

public class House {
    public List<Room> Rooms { get; } = new List<Room>();  // Композиция
    
    public House() {
        Rooms.Add(new Room { Type = "Bedroom" });  // Комната создается внутри дома
    }
}
```