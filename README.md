# java-rdbms

* SQL
* RDBMS
* PostgreSQL

## Introduction

The Northwind database was original developed by Microsoft to show case the abilities of MS Access. The database has grown and been adapted to where now it is the defacto database used to introduce SQL and database management systems.

![Northwind Database Layout](assets/EntityRelation.png)

## Instructions

Import the Northwind database into PostgreSQL using pgAdmin

### clone https://github.com/pthom/northwind_psql.git

* The northwind.sql script is taken from this GitHub repository
* The EntityRelation.png (seen above) is taken from this GitHub repository

### pgAdmin

* Right Click Databases
  * Create
    * type in northwind

* Tools -> Query Tool
  * Open file northwind.sql (from cloned repo)
  * Execute

* Look under
  * northwind -> Schemas -> public -> tables

* Clear query windows

### SQL Syntax Overview

Query

```SQL
SELECT <fields>  
FROM <TABLES>  
WHERE <criteria>
GROUP BY <fields>
HAVING <aggregate criteria>
ORDER BY <order>
LIMIT <number>
```

Create Data

```SQL
INSERT <table> (<fields>)  
VALUES (<data>)  
```

Modify Data

```SQL
UPDATE <table>  
SET <field> = <data>  
WHERE <criteria>  
```

Remove Data

```SQL
DELETE <table>  
WHERE <criteria>  
```

#### SQL Select

Get all the information from the customers table

```SQL
SELECT *  
FROM customers  
```

<details><summary>results</summary>

91 rows affected  

|customer_id|company_name                        |contact_name           |contact_title                 |address                                       |city           |region       |postal_code|country    |phone            |fax              |
|-----------|------------------------------------|-----------------------|------------------------------|----------------------------------------------|---------------|-------------|-----------|-----------|-----------------|-----------------|
|ALFKI      |Alfreds Futterkiste                 |Maria Anders           |Sales Representative          |Obere Str. 57                                 |Berlin         |NULL         |12209      |Germany    |030-0074321      |030-0076545      |
|ANATR      |Ana Trujillo Emparedados y helados  |Ana Trujillo           |Owner                         |Avda. de la Constitución 2222                 |México D.F.    |NULL         |05021      |Mexico     |(5) 555-4729     |(5) 555-3745     |
|ANTON      |Antonio Moreno Taquería             |Antonio Moreno         |Owner                         |Mataderos  2312                               |México D.F.    |NULL         |05023      |Mexico     |(5) 555-3932     |NULL             |
|AROUT      |Around the Horn                     |Thomas Hardy           |Sales Representative          |120 Hanover Sq.                               |London         |NULL         |WA1 1DP    |UK         |(171) 555-7788   |(171) 555-6750   |
|BERGS      |Berglunds snabbköp                  |Christina Berglund     |Order Administrator           |Berguvsvägen  8                               |Luleå          |NULL         |S-958 22   |Sweden     |0921-12 34 65    |0921-12 34 67    |
|BLAUS      |Blauer See Delikatessen             |Hanna Moos             |Sales Representative          |Forsterstr. 57                                |Mannheim       |NULL         |68306      |Germany    |0621-08460       |0621-08924       |
|BLONP      |Blondesddsl père et fils            |Frédérique Citeaux     |Marketing Manager             |24, place Kléber                              |Strasbourg     |NULL         |67000      |France     |88.60.15.31      |88.60.15.32      |
|BOLID      |Bólido Comidas preparadas           |Martín Sommer          |Owner                         |C/ Araquil, 67                                |Madrid         |NULL         |28023      |Spain      |(91) 555 22 82   |(91) 555 91 99   |
|BONAP      |Bon app'                            |Laurence Lebihan       |Owner                         |12, rue des Bouchers                          |Marseille      |NULL         |13008      |France     |91.24.45.40      |91.24.45.41      |
|BOTTM      |Bottom-Dollar Markets               |Elizabeth Lincoln      |Accounting Manager            |23 Tsawassen Blvd.                            |Tsawassen      |BC           |T2F 8M4    |Canada     |(604) 555-4729   |(604) 555-3745   |
|BSBEV      |B's Beverages                       |Victoria Ashworth      |Sales Representative          |Fauntleroy Circus                             |London         |NULL         |EC2 5NT    |UK         |(171) 555-1212   |NULL             |
|CACTU      |Cactus Comidas para llevar          |Patricio Simpson       |Sales Agent                   |Cerrito 333                                   |Buenos Aires   |NULL         |1010       |Argentina  |(1) 135-5555     |(1) 135-4892     |
|CENTC      |Centro comercial Moctezuma          |Francisco Chang        |Marketing Manager             |Sierras de Granada 9993                       |México D.F.    |NULL         |05022      |Mexico     |(5) 555-3392     |(5) 555-7293     |
|CHOPS      |Chop-suey Chinese                   |Yang Wang              |Owner                         |Hauptstr. 29                                  |Bern           |NULL         |3012       |Switzerland|0452-076545      |NULL             |
|COMMI      |Comércio Mineiro                    |Pedro Afonso           |Sales Associate               |Av. dos Lusíadas, 23                          |Sao Paulo      |SP           |05432-043  |Brazil     |(11) 555-7647    |NULL             |
|CONSH      |Consolidated Holdings               |Elizabeth Brown        |Sales Representative          |Berkeley Gardens 12  Brewery                  |London         |NULL         |WX1 6LT    |UK         |(171) 555-2282   |(171) 555-9199   |
|DRACD      |Drachenblut Delikatessen            |Sven Ottlieb           |Order Administrator           |Walserweg 21                                  |Aachen         |NULL         |52066      |Germany    |0241-039123      |0241-059428      |
|DUMON      |Du monde entier                     |Janine Labrune         |Owner                         |67, rue des Cinquante Otages                  |Nantes         |NULL         |44000      |France     |40.67.88.88      |40.67.89.89      |
|EASTC      |Eastern Connection                  |Ann Devon              |Sales Agent                   |35 King George                                |London         |NULL         |WX3 6FW    |UK         |(171) 555-0297   |(171) 555-3373   |
|ERNSH      |Ernst Handel                        |Roland Mendel          |Sales Manager                 |Kirchgasse 6                                  |Graz           |NULL         |8010       |Austria    |7675-3425        |7675-3426        |
|FAMIA      |Familia Arquibaldo                  |Aria Cruz              |Marketing Assistant           |Rua Orós, 92                                  |Sao Paulo      |SP           |05442-030  |Brazil     |(11) 555-9857    |NULL             |
|FISSA      |FISSA Fabrica Inter. Salchichas S.A.|Diego Roel             |Accounting Manager            |C/ Moralzarzal, 86                            |Madrid         |NULL         |28034      |Spain      |(91) 555 94 44   |(91) 555 55 93   |
|FOLIG      |Folies gourmandes                   |Martine Rancé          |Assistant Sales Agent         |184, chaussée de Tournai                      |Lille          |NULL         |59000      |France     |20.16.10.16      |20.16.10.17      |
|FOLKO      |Folk och fä HB                      |Maria Larsson          |Owner                         |Åkergatan 24                                  |Bräcke         |NULL         |S-844 67   |Sweden     |0695-34 67 21    |NULL             |
|FRANK      |Frankenversand                      |Peter Franken          |Marketing Manager             |Berliner Platz 43                             |München        |NULL         |80805      |Germany    |089-0877310      |089-0877451      |
|FRANR      |France restauration                 |Carine Schmitt         |Marketing Manager             |54, rue Royale                                |Nantes         |NULL         |44000      |France     |40.32.21.21      |40.32.21.20      |
|FRANS      |Franchi S.p.A.                      |Paolo Accorti          |Sales Representative          |Via Monte Bianco 34                           |Torino         |NULL         |10100      |Italy      |011-4988260      |011-4988261      |
|FURIB      |Furia Bacalhau e Frutos do Mar      |Lino Rodriguez         |Sales Manager                 |Jardim das rosas n. 32                        |Lisboa         |NULL         |1675       |Portugal   |(1) 354-2534     |(1) 354-2535     |
|GALED      |Galería del gastrónomo              |Eduardo Saavedra       |Marketing Manager             |Rambla de Cataluña, 23                        |Barcelona      |NULL         |08022      |Spain      |(93) 203 4560    |(93) 203 4561    |
|GODOS      |Godos Cocina Típica                 |José Pedro Freyre      |Sales Manager                 |C/ Romero, 33                                 |Sevilla        |NULL         |41101      |Spain      |(95) 555 82 82   |NULL             |
|GOURL      |Gourmet Lanchonetes                 |André Fonseca          |Sales Associate               |Av. Brasil, 442                               |Campinas       |SP           |04876-786  |Brazil     |(11) 555-9482    |NULL             |
|GREAL      |Great Lakes Food Market             |Howard Snyder          |Marketing Manager             |2732 Baker Blvd.                              |Eugene         |OR           |97403      |USA        |(503) 555-7555   |NULL             |
|GROSR      |GROSELLA-Restaurante                |Manuel Pereira         |Owner                         |5ª Ave. Los Palos Grandes                     |Caracas        |DF           |1081       |Venezuela  |(2) 283-2951     |(2) 283-3397     |
|HANAR      |Hanari Carnes                       |Mario Pontes           |Accounting Manager            |Rua do Paço, 67                               |Rio de Janeiro |RJ           |05454-876  |Brazil     |(21) 555-0091    |(21) 555-8765    |
|HILAA      |HILARION-Abastos                    |Carlos Hernández       |Sales Representative          |Carrera 22 con Ave. Carlos Soublette #8-35    |San Cristóbal  |Táchira      |5022       |Venezuela  |(5) 555-1340     |(5) 555-1948     |
|HUNGC      |Hungry Coyote Import Store          |Yoshi Latimer          |Sales Representative          |City Center Plaza 516 Main St.                |Elgin          |OR           |97827      |USA        |(503) 555-6874   |(503) 555-2376   |
|HUNGO      |Hungry Owl All-Night Grocers        |Patricia McKenna       |Sales Associate               |8 Johnstown Road                              |Cork           |Co. Cork     |NULL       |Ireland    |2967 542         |2967 3333        |
|ISLAT      |Island Trading                      |Helen Bennett          |Marketing Manager             |Garden House Crowther Way                     |Cowes          |Isle of Wight|PO31 7PJ   |UK         |(198) 555-8888   |NULL             |
|KOENE      |Königlich Essen                     |Philip Cramer          |Sales Associate               |Maubelstr. 90                                 |Brandenburg    |NULL         |14776      |Germany    |0555-09876       |NULL             |
|LACOR      |La corne d'abondance                |Daniel Tonini          |Sales Representative          |67, avenue de l'Europe                        |Versailles     |NULL         |78000      |France     |30.59.84.10      |30.59.85.11      |
|LAMAI      |La maison d'Asie                    |Annette Roulet         |Sales Manager                 |1 rue Alsace-Lorraine                         |Toulouse       |NULL         |31000      |France     |61.77.61.10      |61.77.61.11      |
|LAUGB      |Laughing Bacchus Wine Cellars       |Yoshi Tannamuri        |Marketing Assistant           |1900 Oak St.                                  |Vancouver      |BC           |V3F 2K1    |Canada     |(604) 555-3392   |(604) 555-7293   |
|LAZYK      |Lazy K Kountry Store                |John Steel             |Marketing Manager             |12 Orchestra Terrace                          |Walla Walla    |WA           |99362      |USA        |(509) 555-7969   |(509) 555-6221   |
|LEHMS      |Lehmanns Marktstand                 |Renate Messner         |Sales Representative          |Magazinweg 7                                  |Frankfurt a.M. |NULL         |60528      |Germany    |069-0245984      |069-0245874      |
|LETSS      |Let's Stop N Shop                   |Jaime Yorres           |Owner                         |87 Polk St. Suite 5                           |San Francisco  |CA           |94117      |USA        |(415) 555-5938   |NULL             |
|LILAS      |LILA-Supermercado                   |Carlos González        |Accounting Manager            |Carrera 52 con Ave. Bolívar #65-98 Llano Largo|Barquisimeto   |Lara         |3508       |Venezuela  |(9) 331-6954     |(9) 331-7256     |
|LINOD      |LINO-Delicateses                    |Felipe Izquierdo       |Owner                         |Ave. 5 de Mayo Porlamar                       |I. de Margarita|Nueva Esparta|4980       |Venezuela  |(8) 34-56-12     |(8) 34-93-93     |
|LONEP      |Lonesome Pine Restaurant            |Fran Wilson            |Sales Manager                 |89 Chiaroscuro Rd.                            |Portland       |OR           |97219      |USA        |(503) 555-9573   |(503) 555-9646   |
|MAGAA      |Magazzini Alimentari Riuniti        |Giovanni Rovelli       |Marketing Manager             |Via Ludovico il Moro 22                       |Bergamo        |NULL         |24100      |Italy      |035-640230       |035-640231       |
|MAISD      |Maison Dewey                        |Catherine Dewey        |Sales Agent                   |Rue Joseph-Bens 532                           |Bruxelles      |NULL         |B-1180     |Belgium    |(02) 201 24 67   |(02) 201 24 68   |
|MEREP      |Mère Paillarde                      |Jean Fresnière         |Marketing Assistant           |43 rue St. Laurent                            |Montréal       |Québec       |H1J 1C3    |Canada     |(514) 555-8054   |(514) 555-8055   |
|MORGK      |Morgenstern Gesundkost              |Alexander Feuer        |Marketing Assistant           |Heerstr. 22                                   |Leipzig        |NULL         |04179      |Germany    |0342-023176      |NULL             |
|NORTS      |North/South                         |Simon Crowther         |Sales Associate               |South House 300 Queensbridge                  |London         |NULL         |SW7 1RZ    |UK         |(171) 555-7733   |(171) 555-2530   |
|OCEAN      |Océano Atlántico Ltda.              |Yvonne Moncada         |Sales Agent                   |Ing. Gustavo Moncada 8585 Piso 20-A           |Buenos Aires   |NULL         |1010       |Argentina  |(1) 135-5333     |(1) 135-5535     |
|OLDWO      |Old World Delicatessen              |Rene Phillips          |Sales Representative          |2743 Bering St.                               |Anchorage      |AK           |99508      |USA        |(907) 555-7584   |(907) 555-2880   |
|OTTIK      |Ottilies Käseladen                  |Henriette Pfalzheim    |Owner                         |Mehrheimerstr. 369                            |Köln           |NULL         |50739      |Germany    |0221-0644327     |0221-0765721     |
|PARIS      |Paris spécialités                   |Marie Bertrand         |Owner                         |265, boulevard Charonne                       |Paris          |NULL         |75012      |France     |(1) 42.34.22.66  |(1) 42.34.22.77  |
|PERIC      |Pericles Comidas clásicas           |Guillermo Fernández    |Sales Representative          |Calle Dr. Jorge Cash 321                      |México D.F.    |NULL         |05033      |Mexico     |(5) 552-3745     |(5) 545-3745     |
|PICCO      |Piccolo und mehr                    |Georg Pipps            |Sales Manager                 |Geislweg 14                                   |Salzburg       |NULL         |5020       |Austria    |6562-9722        |6562-9723        |
|PRINI      |Princesa Isabel Vinhos              |Isabel de Castro       |Sales Representative          |Estrada da saúde n. 58                        |Lisboa         |NULL         |1756       |Portugal   |(1) 356-5634     |NULL             |
|QUEDE      |Que Delícia                         |Bernardo Batista       |Accounting Manager            |Rua da Panificadora, 12                       |Rio de Janeiro |RJ           |02389-673  |Brazil     |(21) 555-4252    |(21) 555-4545    |
|QUEEN      |Queen Cozinha                       |Lúcia Carvalho         |Marketing Assistant           |Alameda dos Canàrios, 891                     |Sao Paulo      |SP           |05487-020  |Brazil     |(11) 555-1189    |NULL             |
|QUICK      |QUICK-Stop                          |Horst Kloss            |Accounting Manager            |Taucherstraße 10                              |Cunewalde      |NULL         |01307      |Germany    |0372-035188      |NULL             |
|RANCH      |Rancho grande                       |Sergio Gutiérrez       |Sales Representative          |Av. del Libertador 900                        |Buenos Aires   |NULL         |1010       |Argentina  |(1) 123-5555     |(1) 123-5556     |
|RATTC      |Rattlesnake Canyon Grocery          |Paula Wilson           |Assistant Sales Representative|2817 Milton Dr.                               |Albuquerque    |NM           |87110      |USA        |(505) 555-5939   |(505) 555-3620   |
|REGGC      |Reggiani Caseifici                  |Maurizio Moroni        |Sales Associate               |Strada Provinciale 124                        |Reggio Emilia  |NULL         |42100      |Italy      |0522-556721      |0522-556722      |
|RICAR      |Ricardo Adocicados                  |Janete Limeira         |Assistant Sales Agent         |Av. Copacabana, 267                           |Rio de Janeiro |RJ           |02389-890  |Brazil     |(21) 555-3412    |NULL             |
|RICSU      |Richter Supermarkt                  |Michael Holz           |Sales Manager                 |Grenzacherweg 237                             |Genève         |NULL         |1203       |Switzerland|0897-034214      |NULL             |
|ROMEY      |Romero y tomillo                    |Alejandra Camino       |Accounting Manager            |Gran Vía, 1                                   |Madrid         |NULL         |28001      |Spain      |(91) 745 6200    |(91) 745 6210    |
|SANTG      |Santé Gourmet                       |Jonas Bergulfsen       |Owner                         |Erling Skakkes gate 78                        |Stavern        |NULL         |4110       |Norway     |07-98 92 35      |07-98 92 47      |
|SAVEA      |Save-a-lot Markets                  |Jose Pavarotti         |Sales Representative          |187 Suffolk Ln.                               |Boise          |ID           |83720      |USA        |(208) 555-8097   |NULL             |
|SEVES      |Seven Seas Imports                  |Hari Kumar             |Sales Manager                 |90 Wadhurst Rd.                               |London         |NULL         |OX15 4NB   |UK         |(171) 555-1717   |(171) 555-5646   |
|SIMOB      |Simons bistro                       |Jytte Petersen         |Owner                         |Vinbæltet 34                                  |Kobenhavn      |NULL         |1734       |Denmark    |31 12 34 56      |31 13 35 57      |
|SPECD      |Spécialités du monde                |Dominique Perrier      |Marketing Manager             |25, rue Lauriston                             |Paris          |NULL         |75016      |France     |(1) 47.55.60.10  |(1) 47.55.60.20  |
|SPLIR      |Split Rail Beer & Ale               |Art Braunschweiger     |Sales Manager                 |P.O. Box 555                                  |Lander         |WY           |82520      |USA        |(307) 555-4680   |(307) 555-6525   |
|SUPRD      |Suprêmes délices                    |Pascale Cartrain       |Accounting Manager            |Boulevard Tirou, 255                          |Charleroi      |NULL         |B-6000     |Belgium    |(071) 23 67 22 20|(071) 23 67 22 21|
|THEBI      |The Big Cheese                      |Liz Nixon              |Marketing Manager             |89 Jefferson Way Suite 2                      |Portland       |OR           |97201      |USA        |(503) 555-3612   |NULL             |
|THECR      |The Cracker Box                     |Liu Wong               |Marketing Assistant           |55 Grizzly Peak Rd.                           |Butte          |MT           |59801      |USA        |(406) 555-5834   |(406) 555-8083   |
|TOMSP      |Toms Spezialitäten                  |Karin Josephs          |Marketing Manager             |Luisenstr. 48                                 |Münster        |NULL         |44087      |Germany    |0251-031259      |0251-035695      |
|TORTU      |Tortuga Restaurante                 |Miguel Angel Paolino   |Owner                         |Avda. Azteca 123                              |México D.F.    |NULL         |05033      |Mexico     |(5) 555-2933     |NULL             |
|TRADH      |Tradição Hipermercados              |Anabela Domingues      |Sales Representative          |Av. Inês de Castro, 414                       |Sao Paulo      |SP           |05634-030  |Brazil     |(11) 555-2167    |(11) 555-2168    |
|TRAIH      |Trail's Head Gourmet Provisioners   |Helvetius Nagy         |Sales Associate               |722 DaVinci Blvd.                             |Kirkland       |WA           |98034      |USA        |(206) 555-8257   |(206) 555-2174   |
|VAFFE      |Vaffeljernet                        |Palle Ibsen            |Sales Manager                 |Smagsloget 45                                 |Århus          |NULL         |8200       |Denmark    |86 21 32 43      |86 22 33 44      |
|VICTE      |Victuailles en stock                |Mary Saveley           |Sales Agent                   |2, rue du Commerce                            |Lyon           |NULL         |69004      |France     |78.32.54.86      |78.32.54.87      |
|VINET      |Vins et alcools Chevalier           |Paul Henriot           |Accounting Manager            |59 rue de l'Abbaye                            |Reims          |NULL         |51100      |France     |26.47.15.10      |26.47.15.11      |
|WANDK      |Die Wandernde Kuh                   |Rita Müller            |Sales Representative          |Adenauerallee 900                             |Stuttgart      |NULL         |70563      |Germany    |0711-020361      |0711-035428      |
|WARTH      |Wartian Herkku                      |Pirkko Koskitalo       |Accounting Manager            |Torikatu 38                                   |Oulu           |NULL         |90110      |Finland    |981-443655       |981-443655       |
|WELLI      |Wellington Importadora              |Paula Parente          |Sales Manager                 |Rua do Mercado, 12                            |Resende        |SP           |08737-363  |Brazil     |(14) 555-8122    |NULL             |
|WHITC      |White Clover Markets                |Karl Jablonski         |Owner                         |305 - 14th Ave. S. Suite 3B                   |Seattle        |WA           |98128      |USA        |(206) 555-4112   |(206) 555-4115   |
|WILMK      |Wilman Kala                         |Matti Karttunen        |Owner/Marketing Assistant     |Keskuskatu 45                                 |Helsinki       |NULL         |21240      |Finland    |90-224 8858      |90-224 8858      |
|WOLZA      |Wolski  Zajazd                      |Zbyszek Piestrzeniewicz|Owner                         |ul. Filtrowa 68                               |Warszawa       |NULL         |01-012     |Poland     |(26) 642-7012    |(26) 642-7012    |
</details>

Select all records from the customers table reporting only the columns company_name, contact_name, and contact_title

```SQL
SELECT company_name, contact_name, contact_title  
FROM customers  
```

<details><summary>results</summary>

91 rows affected  

|company_name                        |contact_name           |contact_title                 |
|------------------------------------|-----------------------|------------------------------|
|Alfreds Futterkiste                 |Maria Anders           |Sales Representative          |
|Ana Trujillo Emparedados y helados  |Ana Trujillo           |Owner                         |
|Antonio Moreno Taquería             |Antonio Moreno         |Owner                         |
|Around the Horn                     |Thomas Hardy           |Sales Representative          |
|Berglunds snabbköp                  |Christina Berglund     |Order Administrator           |
|Blauer See Delikatessen             |Hanna Moos             |Sales Representative          |
|Blondesddsl père et fils            |Frédérique Citeaux     |Marketing Manager             |
|Bólido Comidas preparadas           |Martín Sommer          |Owner                         |
|Bon app'                            |Laurence Lebihan       |Owner                         |
|Bottom-Dollar Markets               |Elizabeth Lincoln      |Accounting Manager            |
|B's Beverages                       |Victoria Ashworth      |Sales Representative          |
|Cactus Comidas para llevar          |Patricio Simpson       |Sales Agent                   |
|Centro comercial Moctezuma          |Francisco Chang        |Marketing Manager             |
|Chop-suey Chinese                   |Yang Wang              |Owner                         |
|Comércio Mineiro                    |Pedro Afonso           |Sales Associate               |
|Consolidated Holdings               |Elizabeth Brown        |Sales Representative          |
|Drachenblut Delikatessen            |Sven Ottlieb           |Order Administrator           |
|Du monde entier                     |Janine Labrune         |Owner                         |
|Eastern Connection                  |Ann Devon              |Sales Agent                   |
|Ernst Handel                        |Roland Mendel          |Sales Manager                 |
|Familia Arquibaldo                  |Aria Cruz              |Marketing Assistant           |
|FISSA Fabrica Inter. Salchichas S.A.|Diego Roel             |Accounting Manager            |
|Folies gourmandes                   |Martine Rancé          |Assistant Sales Agent         |
|Folk och fä HB                      |Maria Larsson          |Owner                         |
|Frankenversand                      |Peter Franken          |Marketing Manager             |
|France restauration                 |Carine Schmitt         |Marketing Manager             |
|Franchi S.p.A.                      |Paolo Accorti          |Sales Representative          |
|Furia Bacalhau e Frutos do Mar      |Lino Rodriguez         |Sales Manager                 |
|Galería del gastrónomo              |Eduardo Saavedra       |Marketing Manager             |
|Godos Cocina Típica                 |José Pedro Freyre      |Sales Manager                 |
|Gourmet Lanchonetes                 |André Fonseca          |Sales Associate               |
|Great Lakes Food Market             |Howard Snyder          |Marketing Manager             |
|GROSELLA-Restaurante                |Manuel Pereira         |Owner                         |
|Hanari Carnes                       |Mario Pontes           |Accounting Manager            |
|HILARION-Abastos                    |Carlos Hernández       |Sales Representative          |
|Hungry Coyote Import Store          |Yoshi Latimer          |Sales Representative          |
|Hungry Owl All-Night Grocers        |Patricia McKenna       |Sales Associate               |
|Island Trading                      |Helen Bennett          |Marketing Manager             |
|Königlich Essen                     |Philip Cramer          |Sales Associate               |
|La corne d'abondance                |Daniel Tonini          |Sales Representative          |
|La maison d'Asie                    |Annette Roulet         |Sales Manager                 |
|Laughing Bacchus Wine Cellars       |Yoshi Tannamuri        |Marketing Assistant           |
|Lazy K Kountry Store                |John Steel             |Marketing Manager             |
|Lehmanns Marktstand                 |Renate Messner         |Sales Representative          |
|Let's Stop N Shop                   |Jaime Yorres           |Owner                         |
|LILA-Supermercado                   |Carlos González        |Accounting Manager            |
|LINO-Delicateses                    |Felipe Izquierdo       |Owner                         |
|Lonesome Pine Restaurant            |Fran Wilson            |Sales Manager                 |
|Magazzini Alimentari Riuniti        |Giovanni Rovelli       |Marketing Manager             |
|Maison Dewey                        |Catherine Dewey        |Sales Agent                   |
|Mère Paillarde                      |Jean Fresnière         |Marketing Assistant           |
|Morgenstern Gesundkost              |Alexander Feuer        |Marketing Assistant           |
|North/South                         |Simon Crowther         |Sales Associate               |
|Océano Atlántico Ltda.              |Yvonne Moncada         |Sales Agent                   |
|Old World Delicatessen              |Rene Phillips          |Sales Representative          |
|Ottilies Käseladen                  |Henriette Pfalzheim    |Owner                         |
|Paris spécialités                   |Marie Bertrand         |Owner                         |
|Pericles Comidas clásicas           |Guillermo Fernández    |Sales Representative          |
|Piccolo und mehr                    |Georg Pipps            |Sales Manager                 |
|Princesa Isabel Vinhos              |Isabel de Castro       |Sales Representative          |
|Que Delícia                         |Bernardo Batista       |Accounting Manager            |
|Queen Cozinha                       |Lúcia Carvalho         |Marketing Assistant           |
|QUICK-Stop                          |Horst Kloss            |Accounting Manager            |
|Rancho grande                       |Sergio Gutiérrez       |Sales Representative          |
|Rattlesnake Canyon Grocery          |Paula Wilson           |Assistant Sales Representative|
|Reggiani Caseifici                  |Maurizio Moroni        |Sales Associate               |
|Ricardo Adocicados                  |Janete Limeira         |Assistant Sales Agent         |
|Richter Supermarkt                  |Michael Holz           |Sales Manager                 |
|Romero y tomillo                    |Alejandra Camino       |Accounting Manager            |
|Santé Gourmet                       |Jonas Bergulfsen       |Owner                         |
|Save-a-lot Markets                  |Jose Pavarotti         |Sales Representative          |
|Seven Seas Imports                  |Hari Kumar             |Sales Manager                 |
|Simons bistro                       |Jytte Petersen         |Owner                         |
|Spécialités du monde                |Dominique Perrier      |Marketing Manager             |
|Split Rail Beer & Ale               |Art Braunschweiger     |Sales Manager                 |
|Suprêmes délices                    |Pascale Cartrain       |Accounting Manager            |
|The Big Cheese                      |Liz Nixon              |Marketing Manager             |
|The Cracker Box                     |Liu Wong               |Marketing Assistant           |
|Toms Spezialitäten                  |Karin Josephs          |Marketing Manager             |
|Tortuga Restaurante                 |Miguel Angel Paolino   |Owner                         |
|Tradição Hipermercados              |Anabela Domingues      |Sales Representative          |
|Trail's Head Gourmet Provisioners   |Helvetius Nagy         |Sales Associate               |
|Vaffeljernet                        |Palle Ibsen            |Sales Manager                 |
|Victuailles en stock                |Mary Saveley           |Sales Agent                   |
|Vins et alcools Chevalier           |Paul Henriot           |Accounting Manager            |
|Die Wandernde Kuh                   |Rita Müller            |Sales Representative          |
|Wartian Herkku                      |Pirkko Koskitalo       |Accounting Manager            |
|Wellington Importadora              |Paula Parente          |Sales Manager                 |
|White Clover Markets                |Karl Jablonski         |Owner                         |
|Wilman Kala                         |Matti Karttunen        |Owner/Marketing Assistant     |
|Wolski  Zajazd                      |Zbyszek Piestrzeniewicz|Owner                         |
</details>

#### SQL Where

Select from the customers table records where the country is equal to Sweden reporting only the columns company_name, contact_name, and country

```SQL
SELECT company_name, contact_name, country  
FROM customers  
WHERE country = 'Sweden'
```

<details><summary>results</summary>

2 rows affected  

|company_name      |contact_name      |country|
|------------------|------------------|-------|
|Berglunds snabbköp|Christina Berglund|Sweden |
|Folk och fä HB    |Maria Larsson     |Sweden |

</details>

Select from the products table where units_in_stock is less than 10 reporting only the columns product_name and units_in_stock

```SQL
SELECT product_name, units_in_stock  
FROM products  
WHERE units_in_stock < 10  
```

<details><summary>results</summary>

12 rows affected  

|product_name              |units_in_stock|
|--------------------------|--------------|
|Chef Anton's Gumbo Mix    |0             |
|Northwoods Cranberry Sauce|6             |
|Alice Mutton              |0             |
|Sir Rodney's Scones       |3             |
|Thüringer Rostbratwurst   |0             |
|Gorgonzola Telino         |0             |
|Mascarpone Fabioli        |9             |
|Rogede sild               |5             |
|Perth Pasties             |0             |
|Louisiana Hot Spiced Okra |4             |
|Scottish Longbreads       |6             |
|Longlife Tofu             |4             |

</details>

#### SELECT order by

Select all records from the customers table reporting only columns company_name, contact_name, city, and country. Sort the results by company_name descending, ie reverse alphabetical order.

```SQL
SELECT company_name, contact_name, city, country  
FROM customers  
ORDER BY company_name DESC  
```

<details><summary>results</summary>

91 rows affected

|company_name                        |contact_name           |city           |country    |
|------------------------------------|-----------------------|---------------|-----------|
|Wolski  Zajazd                      |Zbyszek Piestrzeniewicz|Warszawa       |Poland     |
|Wilman Kala                         |Matti Karttunen        |Helsinki       |Finland    |
|White Clover Markets                |Karl Jablonski         |Seattle        |USA        |
|Wellington Importadora              |Paula Parente          |Resende        |Brazil     |
|Wartian Herkku                      |Pirkko Koskitalo       |Oulu           |Finland    |
|Vins et alcools Chevalier           |Paul Henriot           |Reims          |France     |
|Victuailles en stock                |Mary Saveley           |Lyon           |France     |
|Vaffeljernet                        |Palle Ibsen            |Århus          |Denmark    |
|Trail's Head Gourmet Provisioners   |Helvetius Nagy         |Kirkland       |USA        |
|Tradição Hipermercados              |Anabela Domingues      |Sao Paulo      |Brazil     |
|Tortuga Restaurante                 |Miguel Angel Paolino   |México D.F.    |Mexico     |
|Toms Spezialitäten                  |Karin Josephs          |Münster        |Germany    |
|The Cracker Box                     |Liu Wong               |Butte          |USA        |
|The Big Cheese                      |Liz Nixon              |Portland       |USA        |
|Suprêmes délices                    |Pascale Cartrain       |Charleroi      |Belgium    |
|Spécialités du monde                |Dominique Perrier      |Paris          |France     |
|Split Rail Beer & Ale               |Art Braunschweiger     |Lander         |USA        |
|Simons bistro                       |Jytte Petersen         |Kobenhavn      |Denmark    |
|Seven Seas Imports                  |Hari Kumar             |London         |UK         |
|Save-a-lot Markets                  |Jose Pavarotti         |Boise          |USA        |
|Santé Gourmet                       |Jonas Bergulfsen       |Stavern        |Norway     |
|Romero y tomillo                    |Alejandra Camino       |Madrid         |Spain      |
|Richter Supermarkt                  |Michael Holz           |Genève         |Switzerland|
|Ricardo Adocicados                  |Janete Limeira         |Rio de Janeiro |Brazil     |
|Reggiani Caseifici                  |Maurizio Moroni        |Reggio Emilia  |Italy      |
|Rattlesnake Canyon Grocery          |Paula Wilson           |Albuquerque    |USA        |
|Rancho grande                       |Sergio Gutiérrez       |Buenos Aires   |Argentina  |
|Queen Cozinha                       |Lúcia Carvalho         |Sao Paulo      |Brazil     |
|Que Delícia                         |Bernardo Batista       |Rio de Janeiro |Brazil     |
|QUICK-Stop                          |Horst Kloss            |Cunewalde      |Germany    |
|Princesa Isabel Vinhos              |Isabel de Castro       |Lisboa         |Portugal   |
|Piccolo und mehr                    |Georg Pipps            |Salzburg       |Austria    |
|Pericles Comidas clásicas           |Guillermo Fernández    |México D.F.    |Mexico     |
|Paris spécialités                   |Marie Bertrand         |Paris          |France     |
|Ottilies Käseladen                  |Henriette Pfalzheim    |Köln           |Germany    |
|Old World Delicatessen              |Rene Phillips          |Anchorage      |USA        |
|Océano Atlántico Ltda.              |Yvonne Moncada         |Buenos Aires   |Argentina  |
|North/South                         |Simon Crowther         |London         |UK         |
|Mère Paillarde                      |Jean Fresnière         |Montréal       |Canada     |
|Morgenstern Gesundkost              |Alexander Feuer        |Leipzig        |Germany    |
|Maison Dewey                        |Catherine Dewey        |Bruxelles      |Belgium    |
|Magazzini Alimentari Riuniti        |Giovanni Rovelli       |Bergamo        |Italy      |
|Lonesome Pine Restaurant            |Fran Wilson            |Portland       |USA        |
|Let's Stop N Shop                   |Jaime Yorres           |San Francisco  |USA        |
|Lehmanns Marktstand                 |Renate Messner         |Frankfurt a.M. |Germany    |
|Lazy K Kountry Store                |John Steel             |Walla Walla    |USA        |
|Laughing Bacchus Wine Cellars       |Yoshi Tannamuri        |Vancouver      |Canada     |
|La maison d'Asie                    |Annette Roulet         |Toulouse       |France     |
|La corne d'abondance                |Daniel Tonini          |Versailles     |France     |
|LINO-Delicateses                    |Felipe Izquierdo       |I. de Margarita|Venezuela  |
|LILA-Supermercado                   |Carlos González        |Barquisimeto   |Venezuela  |
|Königlich Essen                     |Philip Cramer          |Brandenburg    |Germany    |
|Island Trading                      |Helen Bennett          |Cowes          |UK         |
|Hungry Owl All-Night Grocers        |Patricia McKenna       |Cork           |Ireland    |
|Hungry Coyote Import Store          |Yoshi Latimer          |Elgin          |USA        |
|Hanari Carnes                       |Mario Pontes           |Rio de Janeiro |Brazil     |
|HILARION-Abastos                    |Carlos Hernández       |San Cristóbal  |Venezuela  |
|Great Lakes Food Market             |Howard Snyder          |Eugene         |USA        |
|Gourmet Lanchonetes                 |André Fonseca          |Campinas       |Brazil     |
|Godos Cocina Típica                 |José Pedro Freyre      |Sevilla        |Spain      |
|Galería del gastrónomo              |Eduardo Saavedra       |Barcelona      |Spain      |
|GROSELLA-Restaurante                |Manuel Pereira         |Caracas        |Venezuela  |
|Furia Bacalhau e Frutos do Mar      |Lino Rodriguez         |Lisboa         |Portugal   |
|Frankenversand                      |Peter Franken          |München        |Germany    |
|Franchi S.p.A.                      |Paolo Accorti          |Torino         |Italy      |
|France restauration                 |Carine Schmitt         |Nantes         |France     |
|Folk och fä HB                      |Maria Larsson          |Bräcke         |Sweden     |
|Folies gourmandes                   |Martine Rancé          |Lille          |France     |
|Familia Arquibaldo                  |Aria Cruz              |Sao Paulo      |Brazil     |
|FISSA Fabrica Inter. Salchichas S.A.|Diego Roel             |Madrid         |Spain      |
|Ernst Handel                        |Roland Mendel          |Graz           |Austria    |
|Eastern Connection                  |Ann Devon              |London         |UK         |
|Du monde entier                     |Janine Labrune         |Nantes         |France     |
|Drachenblut Delikatessen            |Sven Ottlieb           |Aachen         |Germany    |
|Die Wandernde Kuh                   |Rita Müller            |Stuttgart      |Germany    |
|Consolidated Holdings               |Elizabeth Brown        |London         |UK         |
|Comércio Mineiro                    |Pedro Afonso           |Sao Paulo      |Brazil     |
|Chop-suey Chinese                   |Yang Wang              |Bern           |Switzerland|
|Centro comercial Moctezuma          |Francisco Chang        |México D.F.    |Mexico     |
|Cactus Comidas para llevar          |Patricio Simpson       |Buenos Aires   |Argentina  |
|Bólido Comidas preparadas           |Martín Sommer          |Madrid         |Spain      |
|Bottom-Dollar Markets               |Elizabeth Lincoln      |Tsawassen      |Canada     |
|Bon app'                            |Laurence Lebihan       |Marseille      |France     |
|Blondesddsl père et fils            |Frédérique Citeaux     |Strasbourg     |France     |
|Blauer See Delikatessen             |Hanna Moos             |Mannheim       |Germany    |
|Berglunds snabbköp                  |Christina Berglund     |Luleå          |Sweden     |
|B's Beverages                       |Victoria Ashworth      |London         |UK         |
|Around the Horn                     |Thomas Hardy           |London         |UK         |
|Antonio Moreno Taquería             |Antonio Moreno         |México D.F.    |Mexico     |
|Ana Trujillo Emparedados y helados  |Ana Trujillo           |México D.F.    |Mexico     |
|Alfreds Futterkiste                 |Maria Anders           |Berlin         |Germany    |

</details>

Select records from the customers table where the country is either USA, Japan, or Germany making the filter case insensitive (convert the data to all upper case before comparing) reporting only the columns company_name, contact_name, city, and country. Sort the results by country descending, reverse alphabetical order, and within each country sort the results alphabetically by city.

```SQL
SELECT company_name, contact_name, city, country  
FROM customers  
WHERE country in ('USA', 'Japan', 'Germany')  
ORDER BY country DESC, city  
```

<details><summary>results</summary>

24 rows affected  

|company_name                     |contact_name       |city          |country|
|---------------------------------|-------------------|--------------|-------|
|Rattlesnake Canyon Grocery       |Paula Wilson       |Albuquerque   |USA    |
|Old World Delicatessen           |Rene Phillips      |Anchorage     |USA    |
|Save-a-lot Markets               |Jose Pavarotti     |Boise         |USA    |
|The Cracker Box                  |Liu Wong           |Butte         |USA    |
|Hungry Coyote Import Store       |Yoshi Latimer      |Elgin         |USA    |
|Great Lakes Food Market          |Howard Snyder      |Eugene        |USA    |
|Trail's Head Gourmet Provisioners|Helvetius Nagy     |Kirkland      |USA    |
|Split Rail Beer & Ale            |Art Braunschweiger |Lander        |USA    |
|The Big Cheese                   |Liz Nixon          |Portland      |USA    |
|Lonesome Pine Restaurant         |Fran Wilson        |Portland      |USA    |
|Let's Stop N Shop                |Jaime Yorres       |San Francisco |USA    |
|White Clover Markets             |Karl Jablonski     |Seattle       |USA    |
|Lazy K Kountry Store             |John Steel         |Walla Walla   |USA    |
|Drachenblut Delikatessen         |Sven Ottlieb       |Aachen        |Germany|
|Alfreds Futterkiste              |Maria Anders       |Berlin        |Germany|
|Königlich Essen                  |Philip Cramer      |Brandenburg   |Germany|
|QUICK-Stop                       |Horst Kloss        |Cunewalde     |Germany|
|Lehmanns Marktstand              |Renate Messner     |Frankfurt a.M.|Germany|
|Ottilies Käseladen               |Henriette Pfalzheim|Köln          |Germany|
|Morgenstern Gesundkost           |Alexander Feuer    |Leipzig       |Germany|
|Blauer See Delikatessen          |Hanna Moos         |Mannheim      |Germany|
|Frankenversand                   |Peter Franken      |München       |Germany|
|Toms Spezialitäten               |Karin Josephs      |Münster       |Germany|
|Die Wandernde Kuh                |Rita Müller        |Stuttgart     |Germany|

</details>

#### SQL Select Limit

From the products table, report only the columns product_id, product_name, and unit_price, order the results by unit_price, but only report the first 5 rows of data.

```SQL
SELECT product_id, product_name, unit_price  
FROM products  
ORDER BY unit_price  
LIMIT 5  
```

<details><summary>results</summary>
<p>

5 rows affected.

|product_id|product_name      |unit_price|
|----------|------------------|----------|
|33        |Geitost           |2.5       |
|24        |Guaraná Fantástica|4.5       |
|13        |Konbu             |6         |
|52        |Filo Mix          |7         |
|54        |Tourtière         |7.45      |

</p>
</details>

#### SQL Select Distinct

Select a list of unique, distinct, countries from the customers table ordered by those countries.

```SQL
SELECT DISTINCT country  
FROM customers  
ORDER BY country  
```

<details><summary>results</summary>
<p>

21 rows affected

|country|
|-------|
|Argentina|
|Austria|
|Belgium|
|Brazil |
|Canada |
|Denmark|
|Finland|
|France |
|Germany|
|Ireland|
|Italy  |
|Mexico |
|Norway |
|Poland |
|Portugal|
|Spain  |
|Sweden |
|Switzerland|
|UK     |
|USA    |
|Venezuela|

</p>
</details>

#### SQL Min, Max

Select the minimum unit_price from the products table

```SQL
SELECT MIN(unit_price)  
FROM products  
```

<details><summary>results</summary>
<p>

1 rows affected

|min|
|---|
|2.5|

</p>
</details>

Select all rows and all columns from the products table where the product has the same unit_price as the maximum unit_price in the products table.

```SQL
SELECT *  
FROM products  
WHERE unit_price =  
 (SELECT MAX(unit_price)  
  FROM products)  
```

<details><summary>results</summary>
<p>

1 rows affected

|product_id|product_name |supplier_id|category_id|quantity_per_unit |unit_price|units_in_stock|units_on_order|reorder_level|discontinued|
|----------|-------------|-----------|-----------|------------------|----------|--------------|--------------|-------------|------------|
|38        |Côte de Blaye|18         |1          |12 - 75 cl bottles|263.5     |17            |0             |15           |0           |

</p>
</details>

#### SQL Count, Sum, Avg

Determine how many rows are in the products table.

```SQL
SELECT count(*)  
FROM products  
```

<details><summary>results</summary>
<p>

1 rows affected

|count|
|-----|
|77   |

</p>
</details>

Determine how many distinct unit_price are in the products table. In other words determine how complicated our pricing strategy is - the more unit_prices the more complicated the pricing strategy.

```SQL
SELECT count(DISTINCT unit_price)  
FROM products  
```

<details><summary>results</summary>
<p>

1 rows affected

|count|
|-----|
|61   |

</p>
</details>

From the products table, get a list of unique quantity_per_unit and report how many products have each quantity_per_unit value. Notice the addition of the GROUP BY statement.

```SQL
SELECT quantity_per_unit, count(*)  
FROM products  
GROUP BY quantity_per_unit  
```

<details><summary>results</summary>
<p>

70 rows affected

|quantity_per_unit|count|
|-----------------|-----|
|16 - 2 kg boxes  |1    |
|10 kg pkg.       |1    |
|48 pieces        |1    |
|18 - 500 g pkgs. |1    |
|10 boxes x 12 pieces|1    |
|12 - 200 ml jars |1    |
|15 - 625 g jars  |1    |
|24 pkgs. x 4 pieces|1    |
|16 kg pkg.       |1    |
|10 boxes x 30 bags|1    |
|10 - 200 g glasses|1    |
|12 - 100 g bars  |1    |
|20 - 450 g glasses|1    |
|24 - 500 ml bottles|1    |
|24 - 250 g pkgs. |2    |
|500 ml           |1    |
|1 kg pkg.        |1    |
|36 boxes         |1    |
|24 - 250 g  jars |1    |
|40 - 100 g pkgs. |1    |
|20 - 2 kg bags   |1    |
|12 - 500 g pkgs. |1    |
|15 - 300 g rounds|1    |
|24 - 4 oz tins   |1    |
|24 - 200 g pkgs. |2    |
|24 boxes x 2 pies|1    |
|50 bags x 30 sausgs.|1    |
|12 - 75 cl bottles|1    |
|100 - 250 g bags |1    |
|30 gift boxes    |1    |
|24 - 500 g pkgs. |1    |
|50 - 300 g pkgs. |1    |
|24 - 8 oz jars   |1    |
|1k pkg.          |1    |
|32 - 8 oz bottles|1    |
|24 - 150 g jars  |1    |
|10 - 4 oz boxes  |1    |
|20 bags x 4 pieces|1    |
|24 - 12 oz bottles|4    |
|24 - 250 ml bottles|1    |
|32 - 1 kg pkgs.  |1    |
|12 boxes         |1    |
|16 - 500 g tins  |1    |
|750 cc per bottle|1    |
|10 - 500 g pkgs. |2    |
|12 - 1 lb pkgs.  |1    |
|24 pieces        |1    |
|12 - 550 ml bottles|1    |
|24 - 0.5 l bottles|1    |
|12 - 12 oz jars  |1    |
|10 boxes x 8 pieces|1    |
|5 kg pkg.        |2    |
|12 - 355 ml cans |1    |
|48 pies          |1    |
|32 - 500 g boxes |1    |
|16 pies          |1    |
|12 - 12 oz cans  |1    |
|4 - 450 g glasses|1    |
|20 - 1 kg tins   |1    |
|24 - 355 ml bottles|1    |
|500 g            |1    |
|24 - 50 g pkgs.  |1    |
|10 pkgs.         |1    |
|100 - 100 g pieces|1    |
|2 kg box         |1    |
|25 - 825 g cans  |1    |
|12 - 250 g pkgs. |1    |
|12 - 8 oz jars   |1    |
|12 - 100 g pkgs  |1    |
|48 - 6 oz jars   |1    |

</p>
</details>

#### SQL And, Or, Not

Select all rows and all columns from the employees table where is first_name is Anne AND the last name is Dodsworth.

```SQL
SELECT *  
FROM employees  
WHERE first_name = 'Anne' AND last_name = 'Dodsworth'  
```

<details><summary>results</summary>
<p>

1 rows affected

|employee_id|last_name|first_name|title               |title_of_courtesy|birth_date|hire_date |address          |city  |region|postal_code|country|home_phone   |extension|photo      |notes                                                                                          |reports_to|photo_path                          |
|-----------|---------|----------|--------------------|-----------------|----------|----------|-----------------|------|------|-----------|-------|-------------|---------|-----------|-----------------------------------------------------------------------------------------------|----------|------------------------------------|
|9          |Dodsworth|Anne      |Sales Representative|Ms.              |1966-01-27|1994-11-15|7 Houndstooth Rd.|London|NULL  |WG2 7LT    |UK     |(71) 555-4444|452      |binary data|Anne has a BA degree in English from St. Lawrence College.  She is fluent in French and German.|5         |http://accweb/emmployees/davolio.bmp|

</p>
</details>

From the customers table select all rows where the country is not USA, so all countries that are not labeled as USA, reporting only columns company_name, city, and country

```SQL
SELECT company_name, city, country  
FROM customers  
WHERE NOT country = 'USA'  
```

<details><summary>results</summary>
<p>

78 rows affected

|company_name|city|country|
|------------|----|-------|
|Alfreds Futterkiste|Berlin|Germany|
|Ana Trujillo Emparedados y helados|México D.F.|Mexico |
|Antonio Moreno Taquería|México D.F.|Mexico |
|Around the Horn|London|UK     |
|Berglunds snabbköp|Luleå|Sweden |
|Blauer See Delikatessen|Mannheim|Germany|
|Blondesddsl père et fils|Strasbourg|France |
|Bólido Comidas preparadas|Madrid|Spain  |
|Bon app'    |Marseille|France |
|Bottom-Dollar Markets|Tsawassen|Canada |
|B's Beverages|London|UK     |
|Cactus Comidas para llevar|Buenos Aires|Argentina|
|Centro comercial Moctezuma|México D.F.|Mexico |
|Chop-suey Chinese|Bern|Switzerland|
|Comércio Mineiro|Sao Paulo|Brazil |
|Consolidated Holdings|London|UK     |
|Drachenblut Delikatessen|Aachen|Germany|
|Du monde entier|Nantes|France |
|Eastern Connection|London|UK     |
|Ernst Handel|Graz|Austria|
|Familia Arquibaldo|Sao Paulo|Brazil |
|FISSA Fabrica Inter. Salchichas S.A.|Madrid|Spain  |
|Folies gourmandes|Lille|France |
|Folk och fä HB|Bräcke|Sweden |
|Frankenversand|München|Germany|
|France restauration|Nantes|France |
|Franchi S.p.A.|Torino|Italy  |
|Furia Bacalhau e Frutos do Mar|Lisboa|Portugal|
|Galería del gastrónomo|Barcelona|Spain  |
|Godos Cocina Típica|Sevilla|Spain  |
|Gourmet Lanchonetes|Campinas|Brazil |
|GROSELLA-Restaurante|Caracas|Venezuela|
|Hanari Carnes|Rio de Janeiro|Brazil |
|HILARION-Abastos|San Cristóbal|Venezuela|
|Hungry Owl All-Night Grocers|Cork|Ireland|
|Island Trading|Cowes|UK     |
|Königlich Essen|Brandenburg|Germany|
|La corne d'abondance|Versailles|France |
|La maison d'Asie|Toulouse|France |
|Laughing Bacchus Wine Cellars|Vancouver|Canada |
|Lehmanns Marktstand|Frankfurt a.M.|Germany|
|LILA-Supermercado|Barquisimeto|Venezuela|
|LINO-Delicateses|I. de Margarita|Venezuela|
|Magazzini Alimentari Riuniti|Bergamo|Italy  |
|Maison Dewey|Bruxelles|Belgium|
|Mère Paillarde|Montréal|Canada |
|Morgenstern Gesundkost|Leipzig|Germany|
|North/South |London|UK     |
|Océano Atlántico Ltda.|Buenos Aires|Argentina|
|Ottilies Käseladen|Köln|Germany|
|Paris spécialités|Paris|France |
|Pericles Comidas clásicas|México D.F.|Mexico |
|Piccolo und mehr|Salzburg|Austria|
|Princesa Isabel Vinhos|Lisboa|Portugal|
|Que Delícia |Rio de Janeiro|Brazil |
|Queen Cozinha|Sao Paulo|Brazil |
|QUICK-Stop  |Cunewalde|Germany|
|Rancho grande|Buenos Aires|Argentina|
|Reggiani Caseifici|Reggio Emilia|Italy  |
|Ricardo Adocicados|Rio de Janeiro|Brazil |
|Richter Supermarkt|Genève|Switzerland|
|Romero y tomillo|Madrid|Spain  |
|Santé Gourmet|Stavern|Norway |
|Seven Seas Imports|London|UK     |
|Simons bistro|Kobenhavn|Denmark|
|Spécialités du monde|Paris|France |
|Suprêmes délices|Charleroi|Belgium|
|Toms Spezialitäten|Münster|Germany|
|Tortuga Restaurante|México D.F.|Mexico |
|Tradição Hipermercados|Sao Paulo|Brazil |
|Vaffeljernet|Århus|Denmark|
|Victuailles en stock|Lyon|France |
|Vins et alcools Chevalier|Reims|France |
|Die Wandernde Kuh|Stuttgart|Germany|
|Wartian Herkku|Oulu|Finland|
|Wellington Importadora|Resende|Brazil |
|Wilman Kala |Helsinki|Finland|
|Wolski  Zajazd|Warszawa|Poland |

</p>
</details>

#### SQL Between

Select the columns product_id, product_name, and unit_price from the products table where unit_price is between 10 and 20

```SQL
SELECT product_id, product_name, unit_price  
FROM products  
WHERE unit_price between 10 and 20  
```

<details><summary>results</summary>
<p>

29 rows affected

|product_id|product_name|unit_price|
|----------|------------|----------|
|1         |Chai        |18        |
|2         |Chang       |19        |
|3         |Aniseed Syrup|10        |
|15        |Genen Shouyu|13        |
|16        |Pavlova     |17.45     |
|21        |Sir Rodney's Scones|10        |
|25        |NuNuCa Nuß-Nougat-Creme|14        |
|31        |Gorgonzola Telino|12.5      |
|34        |Sasquatch Ale|14        |
|35        |Steeleye Stout|18        |
|36        |Inlagd Sill |19        |
|39        |Chartreuse verte|18        |
|40        |Boston Crab Meat|18.4      |
|42        |Singaporean Hokkien Fried Mee|14        |
|44        |Gula Malacca|19.45     |
|46        |Spegesild   |12        |
|48        |Chocolade   |12.75     |
|49        |Maxilaku    |20        |
|50        |Valkoinen suklaa|16.25     |
|57        |Ravioli Angelo|19.5      |
|58        |Escargots de Bourgogne|13.25     |
|66        |Louisiana Hot Spiced Okra|17        |
|67        |Laughing Lumberjack Lager|14        |
|68        |Scottish Longbreads|12.5      |
|70        |Outback Lager|15        |
|73        |Röd Kaviar  |15        |
|74        |Longlife Tofu|10        |
|76        |Lakkalikööri|18        |
|77        |Original Frankfurter grüne Soße|13        |

</p>
</details>

#### SQL In

Select the columns company_name, contact_name, city, and country from the table suppliers where the countries are in the list USA, Canada, and Mexico making sure the comparisons are case insensitive

```SQL
SELECT company_name, contact_name, city, country  
FROM suppliers  
WHERE upper(country) in ('USA', 'CANADA', 'MEXICO')  
```

<details><summary>results</summary>
<p>

6 rows affected

|company_name|contact_name|city|country|
|------------|------------|----|-------|
|New Orleans Cajun Delights|Shelley Burke|New Orleans|USA    |
|Grandma Kelly's Homestead|Regina Murphy|Ann Arbor|USA    |
|Bigfoot Breweries|Cheryl Saylor|Bend|USA    |
|New England Seafood Cannery|Robb Merchant|Boston|USA    |
|Ma Maison   |Jean-Guy Lauzon|Montréal|Canada |
|Forêts d'érables|Chantal Goulet|Ste-Hyacinthe|Canada |

</p>
</details>

Find all the customers from the customers tables who are in countries where there are suppliers from the suppliers tables. Report only the columns company_name, contact_name, city, and country

```SQL
SELECT company_name, contact_name, city, country  
FROM customers  
WHERE country IN  
    (SELECT country  
     FROM suppliers)  
```

<details><summary>results</summary>
<p>

69 rows affected

|company_name|contact_name|city|country|
|------------|------------|----|-------|
|Alfreds Futterkiste|Maria Anders|Berlin|Germany|
|Around the Horn|Thomas Hardy|London|UK     |
|Berglunds snabbköp|Christina Berglund|Luleå|Sweden |
|Blauer See Delikatessen|Hanna Moos  |Mannheim|Germany|
|Blondesddsl père et fils|Frédérique Citeaux|Strasbourg|France |
|Bólido Comidas preparadas|Martín Sommer|Madrid|Spain  |
|Bon app'    |Laurence Lebihan|Marseille|France |
|Bottom-Dollar Markets|Elizabeth Lincoln|Tsawassen|Canada |
|B's Beverages|Victoria Ashworth|London|UK     |
|Comércio Mineiro|Pedro Afonso|Sao Paulo|Brazil |
|Consolidated Holdings|Elizabeth Brown|London|UK     |
|Drachenblut Delikatessen|Sven Ottlieb|Aachen|Germany|
|Du monde entier|Janine Labrune|Nantes|France |
|Eastern Connection|Ann Devon   |London|UK     |
|Familia Arquibaldo|Aria Cruz   |Sao Paulo|Brazil |
|FISSA Fabrica Inter. Salchichas S.A.|Diego Roel  |Madrid|Spain  |
|Folies gourmandes|Martine Rancé|Lille|France |
|Folk och fä HB|Maria Larsson|Bräcke|Sweden |
|Frankenversand|Peter Franken|München|Germany|
|France restauration|Carine Schmitt|Nantes|France |
|Franchi S.p.A.|Paolo Accorti|Torino|Italy  |
|Galería del gastrónomo|Eduardo Saavedra|Barcelona|Spain  |
|Godos Cocina Típica|José Pedro Freyre|Sevilla|Spain  |
|Gourmet Lanchonetes|André Fonseca|Campinas|Brazil |
|Great Lakes Food Market|Howard Snyder|Eugene|USA    |
|Hanari Carnes|Mario Pontes|Rio de Janeiro|Brazil |
|Hungry Coyote Import Store|Yoshi Latimer|Elgin|USA    |
|Island Trading|Helen Bennett|Cowes|UK     |
|Königlich Essen|Philip Cramer|Brandenburg|Germany|
|La corne d'abondance|Daniel Tonini|Versailles|France |
|La maison d'Asie|Annette Roulet|Toulouse|France |
|Laughing Bacchus Wine Cellars|Yoshi Tannamuri|Vancouver|Canada |
|Lazy K Kountry Store|John Steel  |Walla Walla|USA    |
|Lehmanns Marktstand|Renate Messner|Frankfurt a.M.|Germany|
|Let's Stop N Shop|Jaime Yorres|San Francisco|USA    |
|Lonesome Pine Restaurant|Fran Wilson |Portland|USA    |
|Magazzini Alimentari Riuniti|Giovanni Rovelli|Bergamo|Italy  |
|Mère Paillarde|Jean Fresnière|Montréal|Canada |
|Morgenstern Gesundkost|Alexander Feuer|Leipzig|Germany|
|North/South |Simon Crowther|London|UK     |
|Old World Delicatessen|Rene Phillips|Anchorage|USA    |
|Ottilies Käseladen|Henriette Pfalzheim|Köln|Germany|
|Paris spécialités|Marie Bertrand|Paris|France |
|Que Delícia |Bernardo Batista|Rio de Janeiro|Brazil |
|Queen Cozinha|Lúcia Carvalho|Sao Paulo|Brazil |
|QUICK-Stop  |Horst Kloss |Cunewalde|Germany|
|Rattlesnake Canyon Grocery|Paula Wilson|Albuquerque|USA    |
|Reggiani Caseifici|Maurizio Moroni|Reggio Emilia|Italy  |
|Ricardo Adocicados|Janete Limeira|Rio de Janeiro|Brazil |
|Romero y tomillo|Alejandra Camino|Madrid|Spain  |
|Santé Gourmet|Jonas Bergulfsen|Stavern|Norway |
|Save-a-lot Markets|Jose Pavarotti|Boise|USA    |
|Seven Seas Imports|Hari Kumar  |London|UK     |
|Simons bistro|Jytte Petersen|Kobenhavn|Denmark|
|Spécialités du monde|Dominique Perrier|Paris|France |
|Split Rail Beer & Ale|Art Braunschweiger|Lander|USA    |
|The Big Cheese|Liz Nixon   |Portland|USA    |
|The Cracker Box|Liu Wong    |Butte|USA    |
|Toms Spezialitäten|Karin Josephs|Münster|Germany|
|Tradição Hipermercados|Anabela Domingues|Sao Paulo|Brazil |
|Trail's Head Gourmet Provisioners|Helvetius Nagy|Kirkland|USA    |
|Vaffeljernet|Palle Ibsen |Århus|Denmark|
|Victuailles en stock|Mary Saveley|Lyon|France |
|Vins et alcools Chevalier|Paul Henriot|Reims|France |
|Die Wandernde Kuh|Rita Müller |Stuttgart|Germany|
|Wartian Herkku|Pirkko Koskitalo|Oulu|Finland|
|Wellington Importadora|Paula Parente|Resende|Brazil |
|White Clover Markets|Karl Jablonski|Seattle|USA    |
|Wilman Kala |Matti Karttunen|Helsinki|Finland|

</p>
</details>

#### SQL Like

From the products table, report all of the product_name where they start with C

```SQL
SELECT product_name  
FROM products  
WHERE product_name LIKE 'C%'  
```

<details><summary>results</summary>
<p>

9 rows affected

|product_name|
|------------|
|Chai        |
|Chang       |
|Chef Anton's Cajun Seasoning|
|Chef Anton's Gumbo Mix|
|Carnarvon Tigers|
|Côte de Blaye|
|Chartreuse verte|
|Chocolade   |
|Camembert Pierrot|

</p>
</details>

#### SQL is Null

From the suppliers table, list the company_name, contact_name, and homepage where the homepage is empty, null.

```SQL
SELECT company_name, contact_name, homepage  
FROM suppliers  
WHERE homepage is NULL  
```

<details><summary>results</summary>
<p>

24 rows affected

|company_name|contact_name              |homepage|
|------------|--------------------------|--------|
|Exotic Liquids|Charlotte Cooper          |NULL    |
|Grandma Kelly's Homestead|Regina Murphy             |NULL    |
|Tokyo Traders|Yoshi Nagase              |NULL    |
|Cooperativa de Quesos 'Las Cabras'|Antonio del Valle Saavedra|NULL    |
|Pavlova, Ltd.|Ian Devling               |NULL    |
|Specialty Biscuits, Ltd.|Peter Wilson              |NULL    |
|PB Knäckebröd AB|Lars Peterson             |NULL    |
|Refrescos Americanas LTDA|Carlos Diaz               |NULL    |
|Heli Süßwaren GmbH & Co. KG|Petra Winkler             |NULL    |
|Nord-Ost-Fisch Handelsgesellschaft mbH|Sven Petersen             |NULL    |
|Norske Meierier|Beate Vileid              |NULL    |
|Bigfoot Breweries|Cheryl Saylor             |NULL    |
|Svensk Sjöföda AB|Michael Björn             |NULL    |
|Aux joyeux ecclésiastiques|Guylène Nodier            |NULL    |
|New England Seafood Cannery|Robb Merchant             |NULL    |
|Leka Trading|Chandra Leka              |NULL    |
|Lyngbysild  |Niels Petersen            |NULL    |
|Zaanse Snoepfabriek|Dirk Luchte               |NULL    |
|Karkki Oy   |Anne Heikkonen            |NULL    |
|Ma Maison   |Jean-Guy Lauzon           |NULL    |
|Pasta Buttini s.r.l.|Giovanni Giudici          |NULL    |
|Escargots Nouveaux|Marie Delamare            |NULL    |
|Gai pâturage|Eliane Noz                |NULL    |
|Forêts d'érables|Chantal Goulet            |NULL    |

</p>
</details>

From the suppliers table, list the company_name, contact_name, and homepage for suppliers who have a homepage list. Notice the only difference is the addition of the word NOT in the filter.

```SQL
SELECT company_name, contact_name, homepage  
FROM suppliers  
WHERE homepage is NOT NULL  
```

<details><summary>results</summary>
<p>

5 rows affected

|company_name|contact_name              |homepage|
|------------|--------------------------|--------|
|New Orleans Cajun Delights|Shelley Burke             |#CAJUN.HTM#|
|Mayumi's    |Mayumi Ohno               |Mayumi's (on the World Wide Web)#http://www.microsoft.com/accessdev/sampleapps/mayumi.htm#|
|Plutzer Lebensmittelgroßmärkte AG|Martin Bein               |Plutzer (on the World Wide Web)#http://www.microsoft.com/accessdev/sampleapps/plutzer.htm#|
|Formaggi Fortini s.r.l.|Elio Rossi                |#FORMAGGI.HTM#|
|G'day, Mate |Wendy Mackenzie           |G'day Mate (on the World Wide Web)#http://www.microsoft.com/accessdev/sampleapps/gdaymate.htm#|

</p>
</details>

#### SQL Having

List all countries and the number of customers in those countries where the number of customers is greater than 10

```SQL
SELECT count(customer_id), country  
FROM customers  
GROUP BY country  
HAVING count(customer_id) > 10  
```

<details><summary>results</summary>
<p>

3 rows affected

|count|country                   |
|-----|--------------------------|
|13   |USA                       |
|11   |France                    |
|11   |Germany                   |

</p>
</details>

#### SQL Alias

List all countries and the number of customers in those countries ordered by the number of customers in the countries. Label the column for the number of customers in the country as TotalCustomers and the country as Nation

```SQL
SELECT COUNT(c.customer_id) as TotalCustomers, c.country as Nation  
FROM customers c  
GROUP BY c.country  
ORDER by TotalCustomers  
```

<details><summary>results</summary>
<p>

21 rows affected

|totalcustomers|nation                    |
|--------------|--------------------------|
|1             |Poland                    |
|1             |Norway                    |
|1             |Ireland                   |
|2             |Portugal                  |
|2             |Finland                   |
|2             |Belgium                   |
|2             |Denmark                   |
|2             |Sweden                    |
|2             |Austria                   |
|2             |Switzerland               |
|3             |Argentina                 |
|3             |Italy                     |
|3             |Canada                    |
|4             |Venezuela                 |
|5             |Spain                     |
|5             |Mexico                    |
|7             |UK                        |
|9             |Brazil                    |
|11            |Germany                   |
|11            |France                    |
|13            |USA                       |

</p>
</details>

#### SQL Join

inner join - select records that match in BOTH tables  
includes those customers with orders and  
only those orders with customers  

List all customers who have placed orders along with their orders. Report order_date, company_name, and contact_name.

```SQL
SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM orders o JOIN customers c  
on o.Customer_ID = c.Customer_ID  
```

<details><summary>results</summary>
<p>

830 rows affected

|order_date|company_name              |contact_name           |
|----------|--------------------------|-----------------------|
|1996-07-04|Vins et alcools Chevalier |Paul Henriot           |
|1996-07-05|Toms Spezialitäten        |Karin Josephs          |
|1996-07-08|Hanari Carnes             |Mario Pontes           |
|1996-07-08|Victuailles en stock      |Mary Saveley           |
|1996-07-09|Suprêmes délices          |Pascale Cartrain       |
|...       |                          |                       |
|1998-05-06|Bon app'                  |Laurence Lebihan       |
|1998-05-06|Rattlesnake Canyon Grocery|Paula Wilson           |

</p>
</details>

#### SQL Left Join

Left join - select all records from the left table (closest to the FROM keyword)  
getting the data from the right table (closest to the JOIN keyword) where available  
Thus, includes all customers and if available their order data  
This would be the most normal query for this setup of data  

List all customers including those who have never placed an order. If the customer has placed an order, report back the information from that order. Otherwise leave the order information null. Report order_date, company_name, and contact_name ordered by order_date

```SQL
SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM customers c LEFT JOIN orders o  
ON o.Customer_ID = c.Customer_ID  
ORDER BY o.Order_Date  
```

<details><summary>results</summary>
<p>

830 rows affected

|order_date|company_name              |contact_name           |
|----------|--------------------------|-----------------------|
|1996-07-04|Vins et alcools Chevalier |Paul Henriot           |
|1996-07-05|Toms Spezialitäten        |Karin Josephs          |
|1996-07-08|Hanari Carnes             |Mario Pontes           |
|1996-07-08|Victuailles en stock      |Mary Saveley           |
|1996-07-09|Suprêmes délices          |Pascale Cartrain       |
|...       |                          |                       |
|1998-05-06|Bon app'                  |Laurence Lebihan       |
|1998-05-06|Rattlesnake Canyon Grocery|Paula Wilson           |

</p>
</details>

#### SQL Right Join

Right join - select all records from the right table (closest to the JOIN keyword)  
getting the data from the left table (closest to the FROM keyword) where available  
Thus, include all orders even if a customer is not associated with the order and the order's associated customer data if available  

List all orders including those who do not have an associated customer. If the order has a customer, report back the information from that customer. Otherwise leave the customer information null. Report order_date, company_name, and contact_name ordered by order_date

```SQL
SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM customers c RIGHT JOIN orders o  
ON o.Customer_ID = c.Customer_ID  
ORDER BY o.Order_Date  
```

<details><summary>results</summary>
<p>

832 rows affected

|order_date|company_name              |contact_name           |
|----------|--------------------------|-----------------------|
|1996-07-04|Vins et alcools Chevalier |Paul Henriot           |
|1996-07-05|Toms Spezialitäten        |Karin Josephs          |
|1996-07-08|Hanari Carnes             |Mario Pontes           |
|1996-07-08|Victuailles en stock      |Mary Saveley           |
|1996-07-09|Suprêmes délices          |Pascale Cartrain       |
|...       |                          |                       |
|1998-05-06|Bon app'                  |Laurence Lebihan       |
|1998-05-06|Rattlesnake Canyon Grocery|Paula Wilson           |
|NULL      |Paris spécialités         |Marie Bertrand         |
|NULL      |FISSA Fabrica Inter. Salchichas S.A.|Diego Roel             |

</p>
</details>

#### SQL Full Join

Full join - select all records from both tables joining the data as appropriate  

List all orders and all customers. If the orders and customers have the same customer_id, report their data on the same row. Report order_date, company_name, and contact_name ordered by order_date

```SQL
SELECT o.Order_Date, c.Company_Name, c.Contact_Name
FROM customers c FULL JOIN orders o
ON o.Customer_ID = c.Customer_ID
ORDER BY o.Order_Date
```

<details><summary>results</summary>
<p>

832 rows affected

|order_date|company_name              |contact_name           |
|----------|--------------------------|-----------------------|
|1996-07-04|Vins et alcools Chevalier |Paul Henriot           |
|1996-07-05|Toms Spezialitäten        |Karin Josephs          |
|1996-07-08|Hanari Carnes             |Mario Pontes           |
|1996-07-08|Victuailles en stock      |Mary Saveley           |
|1996-07-09|Suprêmes délices          |Pascale Cartrain       |
|...       |                          |                       |
|1998-05-06|Bon app'                  |Laurence Lebihan       |
|1998-05-06|Rattlesnake Canyon Grocery|Paula Wilson           |
|NULL      |Paris spécialités         |Marie Bertrand         |
|NULL      |FISSA Fabrica Inter. Salchichas S.A.|Diego Roel             |

</p>
</details>

#### SQL Union

***EXTRA*** In a single report, list all customers and employees ordered by company_name. Report only company_name, contact_name, and phone.

```SQL
SELECT company_name, contact_name, phone  
FROM customers  
UNION
SELECT 'Northwind', CONCAT(first_name, ' ', last_name), home_phone  
FROM employees  
ORDER BY company_name
```

<details><summary>results</summary>
<p>

100 rows affected

|company_name|contact_name              |phone                  |
|------------|--------------------------|-----------------------|
|Alfreds Futterkiste|Maria Anders              |030-0074321            |
|Ana Trujillo Emparedados y helados|Ana Trujillo              |(5) 555-4729           |
|Antonio Moreno Taquería|Antonio Moreno            |(5) 555-3932           |
|Around the Horn|Thomas Hardy              |(171) 555-7788         |
|B's Beverages|Victoria Ashworth         |(171) 555-1212         |
|Berglunds snabbköp|Christina Berglund        |0921-12 34 65          |
|Blauer See Delikatessen|Hanna Moos                |0621-08460             |
|Blondesddsl père et fils|Frédérique Citeaux        |88.60.15.31            |
|Bon app'    |Laurence Lebihan          |91.24.45.40            |
|Bottom-Dollar Markets|Elizabeth Lincoln         |(604) 555-4729         |
|Bólido Comidas preparadas|Martín Sommer             |(91) 555 22 82         |
|Cactus Comidas para llevar|Patricio Simpson          |(1) 135-5555           |
|Centro comercial Moctezuma|Francisco Chang           |(5) 555-3392           |
|Chop-suey Chinese|Yang Wang                 |0452-076545            |
|Comércio Mineiro|Pedro Afonso              |(11) 555-7647          |
|Consolidated Holdings|Elizabeth Brown           |(171) 555-2282         |
|Die Wandernde Kuh|Rita Müller               |0711-020361            |
|Drachenblut Delikatessen|Sven Ottlieb              |0241-039123            |
|Du monde entier|Janine Labrune            |40.67.88.88            |
|Eastern Connection|Ann Devon                 |(171) 555-0297         |
|Ernst Handel|Roland Mendel             |7675-3425              |
|FISSA Fabrica Inter. Salchichas S.A.|Diego Roel                |(91) 555 94 44         |
|Familia Arquibaldo|Aria Cruz                 |(11) 555-9857          |
|Folies gourmandes|Martine Rancé             |20.16.10.16            |
|Folk och fä HB|Maria Larsson             |0695-34 67 21          |
|France restauration|Carine Schmitt            |40.32.21.21            |
|Franchi S.p.A.|Paolo Accorti             |011-4988260            |
|Frankenversand|Peter Franken             |089-0877310            |
|Furia Bacalhau e Frutos do Mar|Lino Rodriguez            |(1) 354-2534           |
|GROSELLA-Restaurante|Manuel Pereira            |(2) 283-2951           |
|Galería del gastrónomo|Eduardo Saavedra          |(93) 203 4560          |
|Godos Cocina Típica|José Pedro Freyre         |(95) 555 82 82         |
|Gourmet Lanchonetes|André Fonseca             |(11) 555-9482          |
|Great Lakes Food Market|Howard Snyder             |(503) 555-7555         |
|HILARION-Abastos|Carlos Hernández          |(5) 555-1340           |
|Hanari Carnes|Mario Pontes              |(21) 555-0091          |
|Hungry Coyote Import Store|Yoshi Latimer             |(503) 555-6874         |
|Hungry Owl All-Night Grocers|Patricia McKenna          |2967 542               |
|Island Trading|Helen Bennett             |(198) 555-8888         |
|Königlich Essen|Philip Cramer             |0555-09876             |
|LILA-Supermercado|Carlos González           |(9) 331-6954           |
|LINO-Delicateses|Felipe Izquierdo          |(8) 34-56-12           |
|La corne d'abondance|Daniel Tonini             |30.59.84.10            |
|La maison d'Asie|Annette Roulet            |61.77.61.10            |
|Laughing Bacchus Wine Cellars|Yoshi Tannamuri           |(604) 555-3392         |
|Lazy K Kountry Store|John Steel                |(509) 555-7969         |
|Lehmanns Marktstand|Renate Messner            |069-0245984            |
|Let's Stop N Shop|Jaime Yorres              |(415) 555-5938         |
|Lonesome Pine Restaurant|Fran Wilson               |(503) 555-9573         |
|Magazzini Alimentari Riuniti|Giovanni Rovelli          |035-640230             |
|Maison Dewey|Catherine Dewey           |(02) 201 24 67         |
|Morgenstern Gesundkost|Alexander Feuer           |0342-023176            |
|Mère Paillarde|Jean Fresnière            |(514) 555-8054         |
|North/South |Simon Crowther            |(171) 555-7733         |
|Northwind   |Nancy Davolio             |(206) 555-9857         |
|Northwind   |Steven Buchanan           |(71) 555-4848          |
|Northwind   |Andrew Fuller             |(206) 555-9482         |
|Northwind   |Michael Suyama            |(71) 555-7773          |
|Northwind   |Margaret Peacock          |(206) 555-8122         |
|Northwind   |Anne Dodsworth            |(71) 555-4444          |
|Northwind   |Laura Callahan            |(206) 555-1189         |
|Northwind   |Robert King               |(71) 555-5598          |
|Northwind   |Janet Leverling           |(206) 555-3412         |
|Océano Atlántico Ltda.|Yvonne Moncada            |(1) 135-5333           |
|Old World Delicatessen|Rene Phillips             |(907) 555-7584         |
|Ottilies Käseladen|Henriette Pfalzheim       |0221-0644327           |
|Paris spécialités|Marie Bertrand            |(1) 42.34.22.66        |
|Pericles Comidas clásicas|Guillermo Fernández       |(5) 552-3745           |
|Piccolo und mehr|Georg Pipps               |6562-9722              |
|Princesa Isabel Vinhos|Isabel de Castro          |(1) 356-5634           |
|QUICK-Stop  |Horst Kloss               |0372-035188            |
|Que Delícia |Bernardo Batista          |(21) 555-4252          |
|Queen Cozinha|Lúcia Carvalho            |(11) 555-1189          |
|Rancho grande|Sergio Gutiérrez          |(1) 123-5555           |
|Rattlesnake Canyon Grocery|Paula Wilson              |(505) 555-5939         |
|Reggiani Caseifici|Maurizio Moroni           |0522-556721            |
|Ricardo Adocicados|Janete Limeira            |(21) 555-3412          |
|Richter Supermarkt|Michael Holz              |0897-034214            |
|Romero y tomillo|Alejandra Camino          |(91) 745 6200          |
|Santé Gourmet|Jonas Bergulfsen          |07-98 92 35            |
|Save-a-lot Markets|Jose Pavarotti            |(208) 555-8097         |
|Seven Seas Imports|Hari Kumar                |(171) 555-1717         |
|Simons bistro|Jytte Petersen            |31 12 34 56            |
|Split Rail Beer & Ale|Art Braunschweiger        |(307) 555-4680         |
|Spécialités du monde|Dominique Perrier         |(1) 47.55.60.10        |
|Suprêmes délices|Pascale Cartrain          |(071) 23 67 22 20      |
|The Big Cheese|Liz Nixon                 |(503) 555-3612         |
|The Cracker Box|Liu Wong                  |(406) 555-5834         |
|Toms Spezialitäten|Karin Josephs             |0251-031259            |
|Tortuga Restaurante|Miguel Angel Paolino      |(5) 555-2933           |
|Tradição Hipermercados|Anabela Domingues         |(11) 555-2167          |
|Trail's Head Gourmet Provisioners|Helvetius Nagy            |(206) 555-8257         |
|Vaffeljernet|Palle Ibsen               |86 21 32 43            |
|Victuailles en stock|Mary Saveley              |78.32.54.86            |
|Vins et alcools Chevalier|Paul Henriot              |26.47.15.10            |
|Wartian Herkku|Pirkko Koskitalo          |981-443655             |
|Wellington Importadora|Paula Parente             |(14) 555-8122          |
|White Clover Markets|Karl Jablonski            |(206) 555-4112         |
|Wilman Kala |Matti Karttunen           |90-224 8858            |
|Wolski  Zajazd|Zbyszek Piestrzeniewicz   |(26) 642-7012          |

</p>
</details>

#### SQL Subquery

***EXTRA*** Repeated from above to highlight that the following query is called a subquery

```SQL
    (SELECT country  
     FROM suppliers)  
```

Find all the customers from the customers tables who are in countries where there are suppliers from the suppliers tables. Report only the columns company_name, contact_name, city, and country

```SQL
SELECT company_name, contact_name, city, country  
FROM customers  
WHERE country IN  
    (SELECT country  
     FROM suppliers)  
```

<details><summary>results</summary>
<p>

69 rows affected

|company_name|contact_name|city|country|
|------------|------------|----|-------|
|Alfreds Futterkiste|Maria Anders|Berlin|Germany|
|Around the Horn|Thomas Hardy|London|UK     |
|Berglunds snabbköp|Christina Berglund|Luleå|Sweden |
|Blauer See Delikatessen|Hanna Moos  |Mannheim|Germany|
|Blondesddsl père et fils|Frédérique Citeaux|Strasbourg|France |
|Bólido Comidas preparadas|Martín Sommer|Madrid|Spain  |
|Bon app'    |Laurence Lebihan|Marseille|France |
|Bottom-Dollar Markets|Elizabeth Lincoln|Tsawassen|Canada |
|B's Beverages|Victoria Ashworth|London|UK     |
|Comércio Mineiro|Pedro Afonso|Sao Paulo|Brazil |
|Consolidated Holdings|Elizabeth Brown|London|UK     |
|Drachenblut Delikatessen|Sven Ottlieb|Aachen|Germany|
|Du monde entier|Janine Labrune|Nantes|France |
|Eastern Connection|Ann Devon   |London|UK     |
|Familia Arquibaldo|Aria Cruz   |Sao Paulo|Brazil |
|FISSA Fabrica Inter. Salchichas S.A.|Diego Roel  |Madrid|Spain  |
|Folies gourmandes|Martine Rancé|Lille|France |
|Folk och fä HB|Maria Larsson|Bräcke|Sweden |
|Frankenversand|Peter Franken|München|Germany|
|France restauration|Carine Schmitt|Nantes|France |
|Franchi S.p.A.|Paolo Accorti|Torino|Italy  |
|Galería del gastrónomo|Eduardo Saavedra|Barcelona|Spain  |
|Godos Cocina Típica|José Pedro Freyre|Sevilla|Spain  |
|Gourmet Lanchonetes|André Fonseca|Campinas|Brazil |
|Great Lakes Food Market|Howard Snyder|Eugene|USA    |
|Hanari Carnes|Mario Pontes|Rio de Janeiro|Brazil |
|Hungry Coyote Import Store|Yoshi Latimer|Elgin|USA    |
|Island Trading|Helen Bennett|Cowes|UK     |
|Königlich Essen|Philip Cramer|Brandenburg|Germany|
|La corne d'abondance|Daniel Tonini|Versailles|France |
|La maison d'Asie|Annette Roulet|Toulouse|France |
|Laughing Bacchus Wine Cellars|Yoshi Tannamuri|Vancouver|Canada |
|Lazy K Kountry Store|John Steel  |Walla Walla|USA    |
|Lehmanns Marktstand|Renate Messner|Frankfurt a.M.|Germany|
|Let's Stop N Shop|Jaime Yorres|San Francisco|USA    |
|Lonesome Pine Restaurant|Fran Wilson |Portland|USA    |
|Magazzini Alimentari Riuniti|Giovanni Rovelli|Bergamo|Italy  |
|Mère Paillarde|Jean Fresnière|Montréal|Canada |
|Morgenstern Gesundkost|Alexander Feuer|Leipzig|Germany|
|North/South |Simon Crowther|London|UK     |
|Old World Delicatessen|Rene Phillips|Anchorage|USA    |
|Ottilies Käseladen|Henriette Pfalzheim|Köln|Germany|
|Paris spécialités|Marie Bertrand|Paris|France |
|Que Delícia |Bernardo Batista|Rio de Janeiro|Brazil |
|Queen Cozinha|Lúcia Carvalho|Sao Paulo|Brazil |
|QUICK-Stop  |Horst Kloss |Cunewalde|Germany|
|Rattlesnake Canyon Grocery|Paula Wilson|Albuquerque|USA    |
|Reggiani Caseifici|Maurizio Moroni|Reggio Emilia|Italy  |
|Ricardo Adocicados|Janete Limeira|Rio de Janeiro|Brazil |
|Romero y tomillo|Alejandra Camino|Madrid|Spain  |
|Santé Gourmet|Jonas Bergulfsen|Stavern|Norway |
|Save-a-lot Markets|Jose Pavarotti|Boise|USA    |
|Seven Seas Imports|Hari Kumar  |London|UK     |
|Simons bistro|Jytte Petersen|Kobenhavn|Denmark|
|Spécialités du monde|Dominique Perrier|Paris|France |
|Split Rail Beer & Ale|Art Braunschweiger|Lander|USA    |
|The Big Cheese|Liz Nixon   |Portland|USA    |
|The Cracker Box|Liu Wong    |Butte|USA    |
|Toms Spezialitäten|Karin Josephs|Münster|Germany|
|Tradição Hipermercados|Anabela Domingues|Sao Paulo|Brazil |
|Trail's Head Gourmet Provisioners|Helvetius Nagy|Kirkland|USA    |
|Vaffeljernet|Palle Ibsen |Århus|Denmark|
|Victuailles en stock|Mary Saveley|Lyon|France |
|Vins et alcools Chevalier|Paul Henriot|Reims|France |
|Die Wandernde Kuh|Rita Müller |Stuttgart|Germany|
|Wartian Herkku|Pirkko Koskitalo|Oulu|Finland|
|Wellington Importadora|Paula Parente|Resende|Brazil |
|White Clover Markets|Karl Jablonski|Seattle|USA    |
|Wilman Kala |Matti Karttunen|Helsinki|Finland|

</p>
</details>

Subqueries can be used a columns as well

***EXTRA*** Report how many orders each customer has made. Report contact_name, phone, and number of orders ordering by number of orders

```SQL
SELECT contact_name, phone,
       (SELECT COUNT(o.order_id)
        FROM orders o
        WHERE o.customer_id = c.customer_id) as ordercount  
FROM customers c  
ORDER BY ordercount  
```

<details><summary>results</summary>
<p>

91 rows affected

|contact_name|phone                     |ordercount             |
|------------|--------------------------|-----------------------|
|Marie Bertrand|(1) 42.34.22.66           |0                      |
|Diego Roel  |(91) 555 94 44            |0                      |
|Francisco Chang|(5) 555-3392              |1                      |
|John Steel  |(509) 555-7969            |2                      |
|Manuel Pereira|(2) 283-2951              |2                      |
|Martín Sommer|(91) 555 22 82            |3                      |
|Liu Wong    |(406) 555-5834            |3                      |
|Carine Schmitt|40.32.21.21               |3                      |
|Elizabeth Brown|(171) 555-2282            |3                      |
|Simon Crowther|(171) 555-7733            |3                      |
|Yoshi Tannamuri|(604) 555-3392            |3                      |
|Helvetius Nagy|(206) 555-8257            |3                      |
|Jaime Yorres|(415) 555-5938            |4                      |
|Daniel Tonini|30.59.84.10               |4                      |
|Ana Trujillo|(5) 555-4729              |4                      |
|Liz Nixon   |(503) 555-3612            |4                      |
|Janine Labrune|40.67.88.88               |4                      |
|Dominique Perrier|(1) 47.55.60.10           |4                      |
|Alexander Feuer|0342-023176               |5                      |
|Martine Rancé|20.16.10.16               |5                      |
|Alejandra Camino|(91) 745 6200             |5                      |
|Sergio Gutiérrez|(1) 123-5555              |5                      |
|Isabel de Castro|(1) 356-5634              |5                      |
|Eduardo Saavedra|(93) 203 4560             |5                      |
|Yvonne Moncada|(1) 135-5333              |5                      |
|Paul Henriot|26.47.15.10               |5                      |
|Yoshi Latimer|(503) 555-6874            |5                      |
|Pedro Afonso|(11) 555-7647             |5                      |
|Jonas Bergulfsen|07-98 92 35               |6                      |
|Maria Anders|030-0074321               |6                      |
|Sven Ottlieb|0241-039123               |6                      |
|Anabela Domingues|(11) 555-2167             |6                      |
|Guillermo Fernández|(5) 552-3745              |6                      |
|Karin Josephs|0251-031259               |6                      |
|Patricio Simpson|(1) 135-5555              |6                      |
|Paolo Accorti|011-4988260               |6                      |
|Zbyszek Piestrzeniewicz|(26) 642-7012             |7                      |
|Antonio Moreno|(5) 555-3932              |7                      |
|Hanna Moos  |0621-08460                |7                      |
|Aria Cruz   |(11) 555-9857             |7                      |
|Catherine Dewey|(02) 201 24 67            |7                      |
|Jytte Petersen|31 12 34 56               |7                      |
|Matti Karttunen|90-224 8858               |7                      |
|Lino Rodriguez|(1) 354-2534              |8                      |
|Ann Devon   |(171) 555-0297            |8                      |
|Yang Wang   |0452-076545               |8                      |
|Fran Wilson |(503) 555-9573            |8                      |
|André Fonseca|(11) 555-9482             |9                      |
|Art Braunschweiger|(307) 555-4680            |9                      |
|Hari Kumar  |(171) 555-1717            |9                      |
|Bernardo Batista|(21) 555-4252             |9                      |
|Paula Parente|(14) 555-8122             |9                      |
|Georg Pipps |6562-9722                 |10                     |
|Giovanni Rovelli|035-640230                |10                     |
|Helen Bennett|(198) 555-8888            |10                     |
|Rene Phillips|(907) 555-7584            |10                     |
|Henriette Pfalzheim|0221-0644327              |10                     |
|José Pedro Freyre|(95) 555 82 82            |10                     |
|Rita Müller |0711-020361               |10                     |
|Mary Saveley|78.32.54.86               |10                     |
|Michael Holz|0897-034214               |10                     |
|Miguel Angel Paolino|(5) 555-2933              |10                     |
|Victoria Ashworth|(171) 555-1212            |10                     |
|Frédérique Citeaux|88.60.15.31               |11                     |
|Palle Ibsen |86 21 32 43               |11                     |
|Janete Limeira|(21) 555-3412             |11                     |
|Howard Snyder|(503) 555-7555            |11                     |
|Pascale Cartrain|(071) 23 67 22 20         |12                     |
|Felipe Izquierdo|(8) 34-56-12              |12                     |
|Maurizio Moroni|0522-556721               |12                     |
|Thomas Hardy|(171) 555-7788            |13                     |
|Jean Fresnière|(514) 555-8054            |13                     |
|Lúcia Carvalho|(11) 555-1189             |13                     |
|Elizabeth Lincoln|(604) 555-4729            |14                     |
|Carlos González|(9) 331-6954              |14                     |
|Karl Jablonski|(206) 555-4112            |14                     |
|Mario Pontes|(21) 555-0091             |14                     |
|Annette Roulet|61.77.61.10               |14                     |
|Philip Cramer|0555-09876                |14                     |
|Peter Franken|089-0877310               |15                     |
|Pirkko Koskitalo|981-443655                |15                     |
|Renate Messner|069-0245984               |15                     |
|Laurence Lebihan|91.24.45.40               |17                     |
|Carlos Hernández|(5) 555-1340              |18                     |
|Paula Wilson|(505) 555-5939            |18                     |
|Christina Berglund|0921-12 34 65             |18                     |
|Maria Larsson|0695-34 67 21             |19                     |
|Patricia McKenna|2967 542                  |19                     |
|Horst Kloss |0372-035188               |28                     |
|Roland Mendel|7675-3425                 |30                     |
|Jose Pavarotti|(208) 555-8097            |31                     |

</p>
</details>

#### SQL Insert

Create a single new customer

```SQL
INSERT INTO customers(customer_id, company_name, contact_name)  
VALUES (9191, 'Lambda School', 'John Mitchell')  
```

<details><summary>results</summary>
<p>

Query returned successfully

</p>
</details>

Create customers from suppliers who have a company_name starting with Big

```SQL
INSERT INTO customers(customer_id, company_name, contact_name)  
SELECT 9192, company_name, contact_name  
FROM suppliers  
WHERE company_name LIKE 'Big%'  
```

<details><summary>results</summary>
<p>

Query returned successfully

</p>
</details>

#### SQL Update

Discontinue all products with unit price less than 10.00  

```SQL
UPDATE products  
SET discontinued = 1  
WHERE unit_price < 10.00  
```

<details><summary>results</summary>
<p>

Query returned successfully

</p>
</details>

Update the city, phone, and fax of the supplier whose supplier id is 15

```SQL
UPDATE suppliers  
SET City = 'Oslo', Phone = '(0)1-953530', Fax = '(0)1-953555'  
WHERE supplier_id = 15  
```

<details><summary>results</summary>
<p>

Query returned successfully

</p>
</details>

#### SQL Delete

Delete all products with a unit_price less than 10. This may not be possible if an order refers to a product you are trying to delete

```SQL
DELETE
FROM products  
WHERE unit_price < 10.00  
```

<details><summary>results</summary>
<p>

ERROR:  update or delete on table "products" violates foreign key constraint "fk_order_details_products" on table "order_details"  
DETAIL:  Key (product_id)=(13) is still referenced from table "order_details".  
SQL state: 23503

</p>
</details>

Delete the customer with the customer_id of 15. This may not be possible if an order refers to the customer you are trying to delete

```SQL
DELETE
FROM customers  
WHERE customer_id = '15'  
```

<details><summary>results</summary>
<p>

Query returned successfully

</p>
</details>

### Data Normalization

<details><summary>Original Data</summary>
<p>

Data Table

| Customer Name | Customer Location | C Location 2   | Order Number | Order Total | Product | Product Unit Price | Quantity Ordered |
|---------------|-------------------|----------------|--------------|-------------|---------|--------------------|------------------|
| BarnBarn      | His Hutch         | Window Dresser | AAA          | 99.99       | Carrot  | 1.00               | 5                |
| BarnBarn      | His Hutch         | Window Dresser | AAA          | 99.99       | Apple   | 2.00               | 3                |
| BarnBarn      | Her Hutch         | Window Dresser | AAA          | 99.99       | Hay     | 3.00               | 7                |
| Cinnamon      | Her Hutch         | Closet Dresser | BBB          | 99.99       | Carrot  | 1.00               | 2                |
| Cinnamon      | Her Hutch         | Closet Dresser | BBB          | 99.99       | Apple   | 2.00               | 1                |
| Cinnamon      | Her Hutch         | Closet Dresser | BBB          | 99.99       | Dress   | 5.00               | 3                |
| Cinnamon      | Her Hutch         | Closet Dresser | BBB          | 99.99       | Dress   | 5.00               | 5                |
| Cinnamon      | Her Hutch         | Closet Dresser | BBB          | 99.99       | Chewy   | 4.00               | 4                |
| BarnBarn      | His Hutch         | Windows Dresser| CCC          | 99.99       | Chewy   | 4.00               | 8                |
| BarnBarn      | His Hutch         | Windows Dresser| CCC          | 99.99       | Apple   | 2.00               | 1                |
| Tiger         | Cat Tree          |                |              |             |         |                    |                  |

</p>
</details>

<details><summary>1NF - Separate Data into related fields, No repeated fields</summary>
<p>

Customer Table

| Customer Id | Name     |
|-------------|----------|
| 1           | BarnBarn |
| 2           | Cinnamon |
| 3           | Tiger    |

Order Table

| Order Entry Id | Customer Id   | Order Number | Order Total | Product | Product Unit Price | Quantity Ordered |
|----------------|---------------|--------------|-------------|---------|--------------------|------------------|
| 1              | 1             | AAA          | 99.99       | Carrot  | 1.00               | 5                |
| 2              | 1             | AAA          | 99.99       | Apple   | 2.00               | 3                |
| 3              | 1             | AAA          | 99.99       | Hay     | 3.00               | 7                |
| 4              | 2             | BBB          | 99.99       | Carrot  | 1.00               | 2                |
| 5              | 2             | BBB          | 99.99       | Apple   | 2.00               | 1                |
| 6              | 2             | BBB          | 99.99       | Dress   | 5.00               | 3                |
| 7              | 2             | BBB          | 99.99       | Dress   | 5.00               | 5                |
| 8              | 2             | BBB          | 99.99       | Chewy   | 4.00               | 4                |
| 9              | 1             | CCC          | 99.99       | Chewy   | 4.00               | 8                |
| 10             | 1             | CCC          | 99.99       | Apple   | 2.00               | 1                |

Location Table

| Location Id | Employee | Location       |
|-------------|----------|----------------|
| 1           | 1        | His Hutch      |
| 2           | 1        | Window Dresser |
| 3           | 2        | Her Hutch      |
| 4           | 2        | Closet Dress   |
| 5           | 3        | Cat Tree       |

</p>
</details>

<details><summary>2NF - Multiple Records Data Not Repeated</summary>
<p>

Customer Table

| Customer Id | Name     |
|-------------|----------|
| 1           | BarnBarn |
| 2           | Cinnamon |
| 3           | Tiger    |

Product Table

| Product Id | Product | Product Unit Price |
|------------|---------|--------------------|
| 1          | Carrot  | 1.00               |
| 2          | Apple   | 2.00               |
| 3          | Hay     | 3.00               |
| 4          | Dress   | 5.00               |
| 5          | Chewy   | 4.00               |

Order Table

| Order Id | Customer Id   | Order Number | Order Total |
|----------|---------------|--------------|-------------|
| 1        | 1             | AAA          | 99.99       |
| 2        | 2             | BBB          | 99.99       |
| 3        | 1             | CCC          | 99.99       |

Order Item Table

| Order Item Id | Order Id | Product Id | Quantity Ordered |
|---------------|----------|------------|------------------|
| 1             | 1        | 1          | 5                |
| 2             | 1        | 2          | 3                |
| 3             | 1        | 3          | 7                |
| 4             | 2        | 1          | 2                |
| 5             | 2        | 2          | 1                |
| 6             | 2        | 4          | 3                |
| 7             | 2        | 4          | 5                |
| 8             | 2        | 5          | 4                |
| 9             | 3        | 5          | 8                |
| 10            | 3        | 2          | 1                |

Location Table

| Location Id | Employee | Location       |
|-------------|----------|----------------|
| 1           | 1        | His Hutch      |
| 2           | 1        | Window Dresser |
| 3           | 2        | Her Hutch      |
| 4           | 2        | Closet Dress   |
| 5           | 3        | Cat Tree       |

</p>
</details>

<details><summary>3NF - Duplicated Data Removed, No Derived Data</summary>
<p>

Customer Table

| Customer Id | Name     |
|-------------|----------|
| 1           | BarnBarn |
| 2           | Cinnamon |
| 3           | Tiger    |

Product Table

| Product Id | Product | Product Unit Price |
|------------|---------|--------------------|
| 1          | Carrot  | 1.00               |
| 2          | Apple   | 2.00               |
| 3          | Hay     | 3.00               |
| 4          | Dress   | 5.00               |
| 5          | Chewy   | 4.00               |

Order Table

| Order Id | Customer Id   | Order Number |
|----------|---------------|--------------|
| 1        | 1             | AAA          |
| 2        | 2             | BBB          |
| 3        | 1             | CCC          |

Order Item Table

| Order Item Id | Order Id | Product Id | Quantity Ordered |
|---------------|----------|------------|------------------|
| 1             | 1        | 1          | 5                |
| 2             | 1        | 2          | 3                |
| 3             | 1        | 3          | 7                |
| 4             | 2        | 1          | 2                |
| 5             | 2        | 2          | 1                |
| 6             | 2        | 4          | 8                |
| 7             | 2        | 5          | 4                |
| 8             | 3        | 5          | 8                |
| 9             | 3        | 2          | 1                |

Notice that in order 2, DRESS was ordered twice. These items orders are combined here

Location Table

| Location Id | Employee | Location       |
|-------------|----------|----------------|
| 1           | 1        | His Hutch      |
| 2           | 1        | Window Dresser |
| 3           | 2        | Her Hutch      |
| 4           | 2        | Closet Dress   |
| 5           | 3        | Cat Tree       |

</p>
</details>
