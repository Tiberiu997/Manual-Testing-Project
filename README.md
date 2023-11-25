# Manual-Testing-Project

The scope of the final project for ITF Manual Testing Course is to use all gained knowledge throught the course and apply them in practice, using a store database.

Database under test named Kaufland.

Tools used: MySQL Workbench.

**Functional specifications**

____

**SQL section**

In this section will be describe how SQL testing was performed.

* Database creation
```sql
create database Kaufland;
use Kaufland;
);
```
* Create table 
``` sql
create table Angajati (
    AngajatID int primary key,
    Nume varchar(255),
    Salariu decimal(10, 2),
    BonusPerformanta decimal(10, 2)
);
```
* Create table 
``` sql
create table Clienti (
    ClientID int primary key,
    Nume varchar(255),
    Email varchar(255)
    );
```
* Create table 
``` sql
create table Produse (
    ProdusID int primary key,
    NumeProdus varchar(255),
    Pret decimal(10, 2)
);
```
* Create table 
``` sql
create table Comenzi (
    ComandaID int primary key,
    ClientID int,
    ProdusID int,
    Cantitate int,
    DataComenzii date,
    foreign key (ClientID) references Clienti(ClientID),
    foreign key (ProdusID) references Produse(ProdusID)
);
```


