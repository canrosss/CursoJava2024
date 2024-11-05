SELECT * FROM Customers

SELECT CustomerName FROM Customers where CustomerName like "On%";
 
UPDATE Customers
SET CustomerName = "Bon app\'"
WHERE CustomerName = (SELECT CustomerName FROM Customers where CustomerName like "On%");


SELECT City FROM Customers
SELECT DISTINCT Country FROM Customers

SELECT * FROM Customers
WHERE City = "Berlin";

SELECT * FROM Customers
WHERE CustomerID = 32

SELECT * FROM Customers
ORDER BY City;

SELECT * FROM Customers
ORDER BY City DESC

SELECT * FROM Customers
ORDER BY Country ASC, City ASC;


-- Select all records where the City column has the value 'Berlin' and the PostalCode column has the value '12209'.

SELECT City FROM Customers WHERE City = "Berlin" AND PostalCode = 12209;

-- https://www.w3schools.com/sql/exercise.asp?filename=exercise_or1




```sql
INSERT INTO Customers 
VALUES
	(null, "Alfreds Futterkiste", "Maria Anders", "Obere Str. 57", "Berlin", "12209", "Germany"),
	(null, "Ana Trujillo Emparedados y helados", "Ana Trujillo", "Avda. de la Constitución 2222", "México D.F.", "05021", "Mexico"),
   	(null, "Antonio Moreno Taquería", "Antonio Moreno", "Mataderos 2312", "México D.F.", "05023", "Mexico"),
   	(null, "Around the Horn", "Thomas Hardy", "120 Hanover Sq.", "London", "WA1 1DP", "UK"),
   	(null, "Berglunds snabbköp", "Christina Berglund", "Berguvsvägen 8", "Luleå", "S-958 22", "Sweden"),
   	(null, "Blauer See Delikatessen", "Hanna Moos", "Forsterstr. 57", "Mannheim", "68306", "Germany"),
   	(null, "Blondel père et fils", "Frédérique Citeaux", "24, place Kléber", "Strasbourg", "67000", "France"),
   	(null, "Bólido Comidas preparadas", "Martín Sommer", "C/ Araquil, 67", "Madrid", "28023", "Spain"),
   	(null, "On app'", "Laurence Lebihans", "12, rue des Bouchers", "Marseille", "13008", "France"),
   	(null, "Bottom-Dollar Markets", "Elizabeth Lincoln", "23 Tsawassen Blvd.", "Tsawassen", "T2F 8M4", "Canada"),
   	(null, "B's Beverages", "Victoria Ashworth", "Fauntleroy Circus", "London", "EC2 5NT", "UK"),
   	(null, "Cactus Comidas para llevar", "Patricio Simpson", "Cerrito 333", "Buenos Aires", "1010", "Argentina"),
   	(null, "Centro comercial Moctezuma", "Francisco Chang", "Sierras de Granada 9993", "México D.F.", "05022", "Mexico"),
   	(null, "Chop-suey Chinese", "Yang Wang", "Hauptstr. 29", "Bern", "3012", "Switzerland"),
   	(null, "Comércio Mineiro", "Pedro Afonso", "Av. dos Lusíadas, 23", "São Paulo", "05432-043", "Brazil"),
   	(null, "Consolidated Holdings", "Elizabeth Brown", "Berkeley Gardens 12 Brewery", "London", "WX1 6LT", "UK"),
   	(null, "Drachenblut Delikatessen", "Sven Ottlieb", "Walserweg 21", "Aachen", "52066", "Germany"),
   	(null, "Du monde entier", "Janine Labrune", "67, rue des Cinquante Otages", "Nantes", "44000", "France"),
   	(null, "Eastern Connection", "Ann Devon", "35 King George", "London", "WX3 6FW", "UK"),
   	(null, "Ernst Handel", "Roland Mendel", "Kirchgasse 6", "Graz", "8010", "Austria"),
   	(null, "Familia Arquibaldo", "Aria Cruz", "Rua Orós, 92", "São Paulo", "05442-030", "Brazil"),
   	(null, "FISSA Fabrica Inter. Salchichas S.A.", "Diego Roel", "C/ Moralzarzal, 86", "Madrid", "28034", "Spain"),
   	(null, "Folies gourmandes", "Martine Rancé", "184, chaussée de Tournai", "Lille", "59000", "France"),
   	(null, "Folk och fä HB", "Maria Larsson", "Åkergatan 24", "Bräcke", "S-844 67", "Sweden"),
   	(null, "Frankenversand", "Peter Franken", "Berliner Platz 43", "München", "80805", "Germany"),
   	(null, "France restauration", "Carine Schmitt", "54, rue Royale", "Nantes", "44000", "France"),
   	(null, "Franchi S.p.A.", "Paolo Accorti", "Via Monte Bianco 34", "Torino", "10100", "Italy"),
   	(null, "Furia Bacalhau e Frutos do Mar", "Lino Rodriguez", "Jardim das rosas n. 32", "Lisboa", "1675", "Portugal"),
   	(null, "Galería del gastrónomo", "Eduardo Saavedra", "Rambla de Cataluña, 23", "Barcelona", "08022", "Spain"),
   	(null, "Godos Cocina Típica", "José Pedro Freyre", "C/ Romero, 33", "Sevilla", "41101", "Spain"),
   	(null, "Gourmet Lanchonetes", "André Fonseca", "Av. Brasil, 442", "Campinas", "04876-786", "Brazil"),
   	(null, "Great Lakes Food Market", "Howard Snyder", "2732 Baker Blvd.", "Eugene", "97403", "USA"),
   	(null, "GROSELLA-Restaurante", "Manuel Pereira", "5ª Ave. Los Palos Grandes", "Caracas", "1081", "Venezuela"),
   	(null, "Hanari Carnes", "Mario Pontes", "Rua do Paço, 67", "Rio de Janeiro", "05454-876", "Brazil"),
   	(null, "HILARIÓN-Abastos", "Carlos Hernández", "Carrera 22 con Ave. Carlos Soublette #8-35", "San Cristóbal", "5022", "Venezuela"),
   	(null, "Hungry Coyote Import Store", "Yoshi Latimer", "City Center Plaza 516 Main St.", "Elgin", "97827", "USA"),
   	(null, "Hungry Owl All-Night Grocers", "Patricia McKenna", "8 Johnstown Road", "Cork", "", "Ireland"),
   	(null, "Island Trading", "Helen Bennett", "Garden House Crowther Way", "Cowes", "PO31 7PJ", "UK"),
   	(null, "Königlich Essen", "Philip Cramer", "Maubelstr. 90", "Brandenburg", "14776", "Germany"),
   	(null, "La corne d'abondance", "Daniel Tonini", "67, avenue de l'Europe", "Versailles", "78000", "France"),
   	(null, "La maison d'Asie", "Annette Roulet", "1 rue Alsace-Lorraine", "Toulouse", "31000", "France"),
   	(null, "Laughing Bacchus Wine Cellars", "Yoshi Tannamuri", "1900 Oak St.", "Vancouver", "V3F 2K1", "Canada"),
   	(null, "Lazy K Kountry Store", "John Steel", "12 Orchestra Terrace", "Walla Walla", "99362", "USA"),
   	(null, "Lehmanns Marktstand", "Renate Messner", "Magazinweg 7", "Frankfurt a.M.", "60528", "Germany"),
   	(null, "Let's Stop N Shop", "Jaime Yorres", "87 Polk St. Suite 5", "San Francisco", "94117", "USA"),
   	(null, "LILA-Supermercado", "Carlos González", "Carrera 52 con Ave. Bolívar #65-98 Llano Largo", "Barquisimeto", "3508", "Venezuela"),
   	(null, "LINO-Delicateses", "Felipe Izquierdo", "Ave. 5 de Mayo Porlamar", "I. de Margarita", "4980", "Venezuela"),
   	(null, "Lonesome Pine Restaurant", "Fran Wilson", "89 Chiaroscuro Rd.", "Portland", "97219", "USA"),
   	(null, "Magazzini Alimentari Riuniti", "Giovanni Rovelli", "Via Ludovico il Moro 22", "Bergamo", "24100", "Italy"),
   	(null, "Maison Dewey", "Catherine Dewey", "Rue Joseph-Bens 532", "Bruxelles", "B-1180", "Belgium"),
```
