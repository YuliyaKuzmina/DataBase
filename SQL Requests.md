## Создание SQL-запросов
### Customers

1. Выведем все значения из таблицы со страной Аргентина.  
```
SELECT * FROM [Customers]
WHERE Country = "Argentina";
```

<img src="https://drive.google.com/uc?export=download&id=11Fc2X4ZmNciEoqNV01l541fWIACD7yYt">

2. Выведем все значения из таблицы, id которых больше или равен 87.
```
SELECT * FROM [Customers]
WHERE CustomerID >= 87;
```

<img src="https://drive.google.com/uc?export=download&id=10jr2emxJ24p0V2dKnL-iimQACxC3YfiO">

3. Выведем значения первых четырех столбцов из таблицы, id которых в диапазоне от 3 до 15, отсортирован в обратном порядке. Столбцы CustomerName и CustomerName поменяны местами. 
```
SELECT CustomerID, ContactName, CustomerName, Address FROM [Customers]
WHERE CustomerID BETWEEN 3 and 15
ORDER BY CustomerID DESC;
```

<img src="https://drive.google.com/uc?export=download&id=17ugZImwWTOALSywGww1yXiCMDTRs4MQp">

### Categories

1. Выведем все данные, в которых CategoryName равно любому из значений, перечисленных в скобках.
```
SELECT * FROM [Categories]
WHERE CategoryName IN ("Condiments", "Meat/Poultry", "Seafood")
```

<img src="https://drive.google.com/uc?export=download&id=1F8j-kZmBPE3wPOSD5WRtAqbCPO2Q5t9Z">

2. Выведем первые 5 записей. 
```
SELECT * FROM [Categories]
LIMIT 5
```

<img src="https://drive.google.com/uc?export=download&id=1U5qiQXvYMULpZsajUuUb436EoVOYBlqn">

3. Поменяем местами столбцы, в столбце CategoryID выберем значения 2, 3, 5, 6, 8, сортируем столбец CategoryID в убывабщем порядке, выведем первые 3 записи. 
```
SELECT CategoryName, Description, CategoryID FROM [Categories]
WHERE CategoryID IN ("2", "3", "5", "6", "8")
ORDER BY CategoryID DESC
LIMIT 3;
```

<img src="https://drive.google.com/uc?export=download&id=10dFBrQ4UCwuik04NO-qZR7PRiPUzmZYB">

### Employees

1. Выведем все значения столбца FirstName, начинающиеся на букву "М"
```
SELECT * FROM [Employees]
WHERE FirstName LIKE 'M%'
```
<img src="https://drive.google.com/uc?export=download&id=1a9AudJ55HbJqAl9lgAQuTpCb-zaXRvLQ">

2. Выведем список сотрудников, поменяем местами колонки "LastName" и "FirstName". Выберем сотрудников с датой рождения после 1958.01.01 до 1999.12.31 и отсортируем их по дате рождения
```
SELECT EmployeeID, FirstName, LastName, BirthDate FROM [Employees]
where BirthDate between '1958-01-01' and '1999-12-31'
ORDER BY BirthDate
```
<img src="https://drive.google.com/uc?export=download&id=1rGPIrwJoTj1BrZeW5Vd49EJYTgmf64p9">

3. Выведем список сотрудников, закончивщих/обучающихся в университете и отсортируем список по фамилии.

```
SELECT * FROM [Employees]
WHERE Notes LIKE '%University%'
ORDER BY LastName
```
<img src="https://drive.google.com/uc?export=download&id=1dS5JzhIkVaL0ZdJV1g-llWpXpKiwiQE6">


### Orders

1. Найдем количество заказов  сотрудника ID=1
```
SELECT COUNT(*) FROM [Orders]
WHERE EmployeeID=1
```
<img src="https://drive.google.com/uc?export=download&id=1RhTEzgJx7d_0CJLMaECZfjb5QnvD-zAk">

2. Сгруппируем список сотрудников  по количеству заказов, по ID. Посчитаем все заказы на каждого сотрудника. Переименуем колонку "COUNT(OrderID)" в "CountOrder"

```
SELECT EmployeeID, COUNT(OrderID) AS CountOrder FROM [Orders]
GROUP BY EmployeeID
```
<img src="https://drive.google.com/uc?export=download&id=1A3Kmr-EIXHiivYHoZ-vM1TiIv320l4Bx">

3. Объединим таблицы Orders, Employees и Customers по значению "EmploeeID" и "CustomerID". Переименуем колонку "LastName" в "EmployeeLastName". Отсортируем по дате заказа и выведем 10 первых строк.
```
SELECT CustomerName, OrderID, o.CustomerID,	o.EmployeeID, OrderDate,	ShipperID,	LastName AS "EmployeeLastName",	FirstName FROM [Orders] o JOIN [Employees] e
on o.EmployeeID=e.EmployeeID
JOIN  [Customers] C
ON C.CustomerID=o.CustomerID
ORDER BY OrderDate
LIMIT 10
```
<img src="https://drive.google.com/uc?export=download&id=1Kb11ynAM9_heDLiOrK0NlbcuBxhvBEvy">

### OrderDetails

1. Переименуем столбец OrderDetailID на ID.

```
SELECT OrderDetailID AS ID, OrderID, ProductID, Quantity FROM [OrderDetails]
```

<img src="https://drive.google.com/uc?export=download&id=1HgwNwvqog6W05FgCILZmmlNVGf6lBIQ3">

2. Выполним сортировку по столбцу Quantity, выведем первые 14 записей.
```
SELECT * FROM [OrderDetails]
ORDER BY Quantity
LIMIT 14
```

<img src="https://drive.google.com/uc?export=download&id=1iq3G93QBWv2v9lpndto9FukidQ_Fo4Mg">

3. Выведем уникальные значения в столбце Количество, со значениями больше или равно 58, сделаем сортировку в обратном порядке, выведем первые 5 записей.
```
SELECT DISTINCT Quantity FROM OrderDetails
WHERE Quantity >= 58
ORDER BY Quantity DESC
LIMIT 5;
```
<img src="https://drive.google.com/uc?export=download&id=1AV_gHDTW4Q74JqSUyUSZFmNARf3ajhPJ">

### Products

1. Выведем все значения, где названия продуктов начинаются на Chef.
```
SELECT * FROM [Products]
WHERE ProductName LIKE 'Chef%'
```

<img src="https://drive.google.com/uc?export=download&id=1LjZBJizQ1dIWgYZlNUs3xw_zIsOd1D4-">

2. Выведем значения, где цена находится в диапазоне от 3 до 50 и названия продуктов начинаются на букву "Т".
```
SELECT * FROM [Products]
WHERE Price BETWEEN 3 and 50 And ProductName LIKE 'T%'
```

<img src="https://drive.google.com/uc?export=download&id=1NRWu1Grq5MsluBACAYiLKcxHZVsz568V">

3. Переименуем столбец ProductID на ID, выведем значения,при которых названия продуктов начинаются с буквы "S" или буквы "Т", выполним группировку данных по Поставщикам, отсортируем названия продуктов в алфавитном порядке. 
```
SELECT ProductID AS ID, ProductName, SupplierID, CategoryID, Unit, Price FROM [Products]
WHERE ProductName LIKE 'S%' OR ProductName LIKE 'T%'
GROUP BY SupplierID
ORDER BY ProductName;
```
<img src="https://drive.google.com/uc?export=download&id=1g_DCOWaFB6ITheqNkvPPdfSMeET2Ofn3">

### Shippers

1. Объединим таблицы "Shippers" и "Orders". Отсортируем список по грузоотправителю "United Package" и по дате заказа, начиная от последнего. Выведем 10 значений.  

```
SELECT * FROM [Shippers] JOIN [Orders]
WHERE ShipperName = "United Package"
ORDER BY OrderDate DESC
LIMIT 10
```
![скрин](https://drive.google.com/uc?export=download&id=11ge4XKzVx-C2gZDT53q4Yr9egeu4ggBu)

2. Объединим таблицы "Shippers" и "Orders". Выведем только столбцы "ShipperID", "ShipperName", "Phone", "OrderID". Отсортируем список по ID грузоперевозчика и выведем 7 последних заказов.
```
SELECT Shippers.ShipperID, ShipperName, Phone, OrderID FROM [Shippers] JOIN [Orders]
WHERE Shippers.ShipperID = '3'
LIMIT 7
```

![screen](https://drive.google.com/uc?export=download&id=1ZFmci6Zy1P6bEDp9ELCYuH2K6QDTouTr)

3. Объединим таблицы "Shippers" и "Products". Выведем только столбцы "ShipperID", "ShipperName", "ProductName" и "Price". Отсортируем список по грузоперевозчику Speedy Express и посчитаем общую сумму доставленных товаров, имеющих наименование на букву "С". Переименуем столбец "ProductName" в "ProductNameC" 

```
SELECT ShipperID, ShipperName, ProductName AS ProductNameC, SUM(Price) FROM [Shippers] JOIN Products
WHERE ShipperName = "Speedy Express" AND ProductName LIKE 'C%'
```
![screen](https://drive.google.com/uc?export=download&id=1If0hTiP1BhPluFfXitRgdtNb6isAzD8I)

### Suppliers

1. Сгруппируем список по количеству поставщиков в каждую страну.

```
SELECT COUNT(SupplierID), Country FROM [Suppliers]
group by country;
```
![screen](https://drive.google.com/uc?export=download&id=1vLs-UDVlhuUbJrO28SQUowspGY2yw55l)

2. Объединим таблицы "Suppliers" и "Products" по SupplierID. Выведем список поставщиков в Австралию, Испанию и Японию, и отсортируем по стране
```
SELECT s.SupplierID, SupplierName, ProductName, Country FROM [Suppliers] s JOIN Products p	
on s.SupplierID=p.SupplierID
WHERE Country IN ("Japan", "Australia", "Spain")
Order BY Country
```
![screen](https://drive.google.com/uc?export=download&id=1obr-iGQM2nQe1DlPY_Qrcv0e44uQyctm)

3. Объединим таблицы "Suppliers" и "Products". Посчитаем, сколько ID товаров у каждого поставщика. Выведем список поставщиков от 4 товаров.

```
SELECT s.SupplierID, SupplierName, COUNT(ProductID) FROM [Suppliers] s JOIN Products p
ON s.SupplierID=p.SupplierID
Group By s.SupplierID, SupplierName
HAVING COUNT(ProductID) >=4
```
![screen](https://drive.google.com/uc?export=download&id=1gHI-mBv6G2uu4BPu_WlzH8XLaTDRq718)
