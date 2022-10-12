
## 기본 출력(SELECT)
```
select * from Customers;
select CustomerID, CustomerName from Customers;
```


## 수 제한(LIMIT)
```
select * from Customers LIMIT 5;
```


## 정렬(ORDER BY)
```
select * from Customers ORDER BY CustomerID DESC; // 내림차순
select * from Customers ORDER BY CustomerID ASC; // 오름차순 default
```


## 중복 제거(DISTINCT)
```
SELECT DISTINCT country FROM Customers;
```


- - - 
## 조건(WHERE)
```
SELECT * FROM Products WHERE SupplierID = 1;
```

##### 논리연산자(=, !=, >=, <=, <, >)
```
SELECT ProductID, ProductName FROM Products WHERE Price >= 15;
```

##### 목록 포함 여부(IN, NOT IN) **
```
SELECT ProductName, SupplierID FROM Products WHERE SupplierID IN ('1', '2');
SELECT ProductName, SupplierID FROM Products WHERE SupplierID NOT IN ('1', '2');
```

##### 문자열 포함 여부(LIKE)
- 문자열 앞뒤로 % 붙여서 큰 범위로 검색 가능
```
SELECT ProductID, Unit FROM Products WHERE Unit LIKE '%boxes%';
```

##### AND / OR
- 여러 조건 검색 할 때
```
SELECT ProductID, Unit FROM Products WHERE Unit LIKE '%boxes%' AND Price <= 15;
```


## 묶기 (GROUP BY)
```
SELECT Country, COUNT(CustomerID) FROM Customers GROUP BY Country;
```

###### COUNT()
- 각 컬럼의 개수 세어서 출력

###### Having()
- 계산된 결과 값을 다시 조건으로 걸 때
```
SELECT Country, COUNT(CustomerID) FROM Customers GROUP BY Country HAVING COUNT(CustomerID) >= 5;
```


## 엮기 (JOIN)
### INNER JOIN
- 교집합
- 같은 컬럼을 갖고 있는 테이블에서 교집합을 가져오기
```
SELECT Customers.CustomerID FROM Customers
INNER JOIN Orders
ON Orders.CustomerID = Customers.CustomerID;
```

- AS 문법으로 짧게 처리할 수도 있음
```
SELECT C.CustomerID, C.CustomerName FROM Customers AS C
INNER JOIN Orders AS O
ON O.CustomerID = C.CustomerID;
```

- 이 외에도 다양한 조인 방법이 있음 
- ![[Pasted image 20221012180744.png]]


## 서브쿼리
- 쿼리 안에 쿼리가 있는 형태.....?
- 이건 필요할 때 배울래.. 어려버