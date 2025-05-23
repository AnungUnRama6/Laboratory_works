# Лабораторная работа №3: Продвинутые объекты в JavaScript

## Цель работы
Познакомиться с классами и объектами в JavaScript, научиться создавать классы, использовать конструкторы и методы, а также реализовать наследование.

## Условие
Создайте консольное приложение, моделирующее систему инвентаря, где можно добавлять предметы, изменять их свойства и управлять ими.

## Шаги выполнения

### Шаг 1. Создание базового класса InventoryItem
Создайте класс `InventoryItem`, который будет представлять любой предмет в инвентаре.

**Поля класса:**
- `name` – название предмета.
- `weight` – вес предмета.
- `rarity` – редкость предмета (common, uncommon, rare, legendary).

**Методы:**
- `getInfo()` – возвращает строку с информацией о предмете.
- `setWeight(newWeight)` – изменяет вес предмета.

### Шаг 2. Создание класса Item
Создайте класс `Item`, который будет представлять обычный предмет и наследоваться от `InventoryItem`.

### Шаг 3. Создание класса Weapon
Создайте класс `Weapon`, который наследуется от `InventoryItem` и добавляет дополнительные характеристики:

**Дополнительные поля:**
- `damage` – урон оружия.
- `durability` – прочность (от 0 до 100).

**Методы:**
- `use()` – уменьшает `durability` на 10 (если прочность больше 0).
- `repair()` – восстанавливает `durability` до 100.

### Шаг 4. Тестирование
Создайте несколько объектов классов `Item` и `Weapon`. Вызовите их методы, чтобы убедиться в правильности работы.

**Пример использования:**
```javascript
const sword = new Item("Steel Sword", 3.5, "rare");
console.log(sword.getInfo()); // Вывод: Item: Steel Sword, Weight: 3.5kg, Rarity: rare
sword.setWeight(4.0);
console.log(sword.getInfo()); // Вывод: Item: Steel Sword, Weight: 4.0kg, Rarity: rare

const bow = new Weapon("Longbow", 2.0, "uncommon", 15, 100);
console.log(bow.getInfo());
bow.use();
console.log(bow.durability); // должно уменьшиться
bow.repair();
```

## Контрольные вопросы

### 1. Какое значение имеет `this` в методах класса?
В методах класса `this` ссылается на экземпляр класса, внутри которого вызывается метод.

### 2. Как работает модификатор доступа `#` в JavaScript?
Модификатор `#` делает поле или метод приватными, т.е. недоступными за пределами класса. Например:
```javascript
class Example {
    #privateField = 42;
    getPrivateField() {
        return this.#privateField;
    }
}
const obj = new Example();
console.log(obj.getPrivateField()); // 42
console.log(obj.#privateField); // Ошибка
```

### 3. В чем разница между классами и функциями-конструкторами?
- Классы (`class`) являются более современным и удобочитаемым способом создания объектов.
- Функции-конструкторы (`function`) использовались до появления классов и требуют явного использования `prototype` для добавления методов.
- Классы инкапсулируют наследование и позволяют использовать `super` для вызова методов родителя.

**Пример на функции-конструкторе:**
```javascript
function Item(name, weight, rarity) {
    this.name = name;
    this.weight = weight;
    this.rarity = rarity;
}
Item.prototype.getInfo = function() {
    return `Item: ${this.name}, Weight: ${this.weight}kg, Rarity: ${this.rarity}`;
};
```
В современных приложениях предпочтительнее использовать `class` из-за большей читаемости и удобства работы.

---
Если есть вопросы или предложения по улучшению кода, дайте знать! 🚀

