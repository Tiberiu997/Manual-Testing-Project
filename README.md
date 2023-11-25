# Manual-Testing-Project

The scope of the final project for ITF Manual Testing Course is to use all gained knowledge throught the course and apply them in practice, using a store database.

Database under test named Kaufland.

Tools used: MySQL Workbench.

**Functional specifications**

____

**SQL section**

In this section will be describe how SQL testing was performed.

**DDL instructions**
* Database creation
```sql
create database Kaufland;
use Kaufland;
);
```
* Create table Angajati
``` sql
create table Angajati(
	AngajatID int primary key,
	NumeAngajat varchar(255),
	Salariu decimal(10,2),
	BonusPerformanta decimal (10,2)
);
```
* Create table Clienti
``` sql
create table Clienti(
	ClientID int primary key,
	NumeClient varchar(255),
	Email varchar(255)
);
```
* Create table Produse
``` sql
create table Produse (
    ProdusID int auto_increment primary key,
    NumeProdus varchar(255),
    Pret decimal(10, 2),
    Bucati int
);
```
* Create table Comenzi
``` sql
create table Comenzi(
	ComandaID int primary key,
	ClientID int,
	ProdusID int,
	Cantitate int,
	DataComenzii date,
	foreign key (ClientID) references Clienti(ClientID),
	foreign key (ProdusID) references Produse(ProdusID)
);
```
* Create table Facturi
``` sql
create table Facturi(
	FacturaID int primary key,
	ComandaID int,
	DataFactura date,
	ClientID int,
	foreign key (ComandaID) references Comenzi(ComandaID),
	foreign key (ClientID) references Clienti(ClientID)
);
```

**DML instructions**

* Insert 15 Angajati
``` sql
insert into Angajati(AngajatID,NumeAngajat,Salariu,BonusPerformanta) values
	(101,"Beniasu Andrei",1000,100.00),
	(102,"Paraschiv Ioan",1000,350.00),
	(103,"Soare Mihai",1000,50.00),
	(104,"Serban Maria",3000,350.00),
	(105,"Balan Madalina",3000,150.00),
	(106,"Andreea Marin",4300,100.00),
	(107,"Tudor Octavian",2500,0.00),
	(108,"Covil Marin",3500,100.00),
	(109,"Ciobanasu Catalina",2000,0.00),
	(110,"Hapciu Elena",2800,50.00),
	(111,"Botea Luminita",1500,0.00),
	(112,"Marius Ionel",4500,400.00),
	(113,"Iozefini Laura",1000,100.00),
	(114,"Chiriac Corina",2000,100.00),
	(115,"Andrei Iosif",3000,200.00);
  ```
* I used alter table to add a new column.
``` sql
alter table Clienti add column Oras varchar(50);
```
* Insert Clienti
``` sql
insert into Clienti(ClientID,NumeClient,Email,Oras) values
	(2101,"Avram Tiberiu","tiby_godric@yahoo.com","Ploiesti"),
	(2102,"Ionescu Maria","ionesccu_maria@yahoo.com","Suceava"),
	(2103,"Cristian Marin","cristian.marin@yahoo.com","Iasi"),
	(2104,"Mihai Stan","mihai.stan@yahoo.com","Bucuresti"),
	(2105,"Gabriela Stan","gabriela.stan@yahoo.com","Bucuresti"),
	(2106,"Chiran Ionut","chiran.ionut@yahoo.com","Bucuresti"),
	(2107,"Florea Iuliana","florea.iuliana@yahoo.com","Ploiesti"),
	(2108,"Marcu Daniel","marcu.daniel@yahoo.com","Iasi"),
	(2109,"Sarbu Andreea","sarbu.andreea@yahoo.com","Timisoara"),
	(2110,"Crivat Elena","crivat.elena@yahoo.com","Ploiesti"),
	(2111,"Jurcan Bianca","jurcan.bianca@yahoo.com","Ploiesti"),
	(2112,"Niculescu Robert","niculescu.robert@yahoo.com","Bucuresti"),
	(2113,"Moscovici Alexandru","moscovici.alexandru@yahoo.com","Ploiesti"),
	(2114,"Dumitrescu Adriana","dumitrescu.adriana@yahoo.com","Bucuresti"),
	(2115,"Paul Andrei","paul.andrei@yahoo.com","Bucuresti"),
	(2116,"Octavian Neamtu","octavian.neamtu@yahoo.com","Bucuresti"),
	(2117,"Silviu Ispas","silviu.ispas@yahoo.com","Ploiesti"),
	(2118,"Puiu Stefan","puiu.stefan@yahoo.com","Iasi"),	
	(2119,"Anamaria Ciupu","anamaria.ciupu@yahoo.com","Ploiesti"),
	(2120,"Pascu Daniel","pascu.daniel@yahoo.com","Iasi"),
	(2121,"Ioda Bogdan","ioda.bogdan@yahoo.com","Ploiesti"),
	(2122,"Ivan Alexandru","ivan.alexandru@yahoo.com","Bucuresti"),
	(2123,"Ioana Maria","ioana.maria@yahoo.com","Bucuresti"),
	(2124,"Dumitru Mara","mara.dumitru@yahoo.com","Ploiesti"),
	(2125,"Andronic Andreea","andronic.andreea@yahoo.com","Oradea"),
	(2126,"Covaci Natalia ","covaci.natalia@yahoo.com","Ploiesti"),
	(2127,"Nicolae Mihai","nicolae.mihai@yahoo.com","Ploiesti"),
	(2128,"Zlavog Bogdan","zlavog.bogdan@yahoo.com","Bucuresti"),
	(2129,"Ivan Maria","ivan.maria@yahoo.com","Ploiesti"),
	(2130,"Pana Valentin","pana.valentin@yahoo.com","Ploiesti");
```
*Insert Produse
``` sql
insert into Produse(ProdusID,NumeProdus,Pret,Bucati) values
	(510,"Servetele umede",9.00,25),
	(511,"Servetele de masa",20.00,9),
	(512,"Lapte Light",18.70,30),
	(513,"Sunca de pui premium",45.00,8),
	(514,"Carne tocata porc 1kg",15.30,5),
	(515,"Paine feliata",7.20,15),
	(516,"Oua",900.00,25),
	(517,"Lapte condensat",11.00,7),
	(518,"Baton ciocolata proteine",10.00,25),
	(519,"Jeleuri",9.00,4),
	(520,"Unt",9.50,12),
	(521,"Punga legume salata",20.10,11),
	(522,"Fructe congelate",20.00,15),
	(523,"Biscuiti",6.00,20),
	(524,"Orez bob rotund",12.00,23),
	(525,"Ciocolata",9.50,32),
	(526,"Inghetata",3.50,14),
	(527,"Bauturi carbogazoase",10.00,25),
	(528,"Apa plata",5.00,25),
	(529,"Apa minerala",5.50,20),
	(530,"Suc de portocale",10.80,6),
	(531,"Suc de mere",10.80,2),
	(532,"Cartofi 1kg",10.10,4),
	(533,"Pepene galben felie",15.00,3),
	(534,"Solutie de curatat",25.40,8),
	(535,"Sampon ",30.00,2);
```
* Insert Comenzi
``` sql
insert into Comenzi(ComandaID,ClientID,ProdusID,Cantitate,DataComenzii) values
	(801,2110,516,2,'2023-09-25'),
	(802,2108,512,3,'2023-09-09'),
	(803,2109,510,2,'2023-09-09'),
	(804,2120,532,5,'2023-10-01'),
	(805,2125,516,2,'2023-10-05'),
	(806,2120,527,1,'2023-09-20'),
	(807,2107,520,2,'2023-10-15'),
	(808,2108,522,1,'2023-11-02'),
	(809,2111,528,2,'2023-11-05'),
	(810,2112,526,2,'2023-11-11');
```
* Insert Facturi
``` sql
insert into Facturi(FacturaID,ComandaID,DataFactura,ClientID) values
	(901,801,'2023-09-26',2110),
	(902,802,'2023-09-10',2108),
	(903,803,'2023-09-10',2109),
	(904,804,'2023-10-02',2120),
	(905,805,'2023-10-06',2125),
	(906,806,'2023-09-21',2120),
	(907,807,'2023-10-16',2107),
	(908,808,'2023-11-03',2108),
	(909,809,'2023-11-06',2111),
	(910,810,'2023-11-12',2112);
```
* Update Angajati - Updating the performance bonus for a specific employee
    ``` sql
    update Angajati set BonusPerformanta = 300.0 where AngajatID = 1;
    ```

* Delete Produse - Deleting a product
    ``` sql
    delete from Produse where ProdusId = 4;
    ```
 **DQL instructions**
* Check if products were added successfully
    ``` sql
    select ProdusID, NumeProdus, Pret from Produse;
    ```
* Selecting employees who have a bonus greater than $100.
    ``` sql
    select * from Angajati where BonusPerformanta > 100.0;
    ```
*
    ``` sql
    select * from Produse where NumeProdus like '%Laptop%' ;
    ```
*
    ``` sql
    select *
    from Angajati
    where (BonusPerformanta > 100.0 and Salariu < 700)
       or (BonusPerformanta < 150.0 and Salariu > 800);
    ```
* Calculation of the average salary of employees
    ``` sql
    select avg(Salariu) from Angajati;
    ```
* Selection of the first 10 employees ordered by decreasing salary.
    ``` sql
    select * from Angajati order by Salariu desc limit 4;
    ```
 

  
