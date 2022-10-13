# SQL - patika.dev - Soru ve Cevapları
>**[patika.dev](https://app.patika.dev/courses/sql) platformu SQL öğrenme amaçlı soruların cevaplanması projesidir.** \
> **Profil için tıklayınız: [app.patika.dev/nmelihkutlu](https://app.patika.dev/nmelihkutlu)**


![](https://raw.githubusercontent.com/nmelihkutlu/patikasql/main/PatikaSQLproje.png)



[Ödev1](#ödev-1) - [Ödev2](#ödev-2) - [Ödev3](#ödev-3) - [Ödev4](#ödev-4) - [Ödev5](#ödev-5) - [Ödev6](#ödev-6) - [Ödev7](#ödev-7) - [Ödev8](#ödev-8) - [Ödev9](#ödev-9) - [Ödev10](#ödev-10) - [Ödev11](#ödev-11)


## Ödev 1
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
    > SELECT title, description FROM film 


2. film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
    > SELECT * FROM film WHERE length > 60 AND length < 75


3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
    > SELECT * FROM film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99

4. customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
    > SELECT last_name FROM customer WHERE first_name = 'Mary'
    
    > Smith

5. film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
    > SELECT * FROM film WHERE NOT (length > 50) AND NOT (rental_rate = 2.99 OR rental_rate = 4.99)


## Ödev 2
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
    > SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99

2. actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
    > SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope', 'Nick', 'Ed')

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
    > SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99)

## Ödev 3
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
    > SELECT country FROM country WHERE country LIKE 'A%a' 

2. country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
    > SELECT country FROM country WHERE country LIKE '_____%n' 

3. film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
    > SELECT title FROM film WHERE title ILIKE '%t%t%t%t%' 

4. film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
    > SELECT * FROM film WHERE title LIKE 'C%' AND length>90 AND rental_rate = 2.99

## Ödev 4
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
    >SELECT DISTINCT replacement_cost FROM film

2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
    > SELECT COUNT (DISTINCT replacement_cost) FROM film

    > 21
3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
    > SELECT COUNT (*) FROM film WHERE title LIKE 'T%' AND rating ='G';

    > 9
4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
    > SELECT COUNT (*) FROM country WHERE country LIKE '_____';

5. city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
    > SELECT COUNT (*) FROM city WHERE city ILIKE '%r';

## Ödev 5
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
    > SELECT title FROM film where title LIKE '%n' ORDER BY length DESC LIMIT 5;

2. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
    > SELECT title FROM film where title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;

3. customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
    > SELECT * FROM customer where store_id = 1 ORDER BY last_name DESC LIMIT 4;


## Ödev 6
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
    > SELECT AVG(rental_rate) FROM film;

2. film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
    > SELECT COUNT(*) FROM film WHERE title LIKE 'C%';

3. film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
    > SELECT MAX(length) FROM film WHERE rental_rate=0.99;

    > 189

4. film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
    > SELECT COUNT(DISTINCT(replacement_cost)) FROM film WHERE length > 150;

    > 21


## Ödev 7
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
    > SELECT rating FROM film GROUP BY rating;


2. film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
    > SELECT replacement_cost, COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(replacement_cost) > 50;

3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
    > SELECT store_id, COUNT(*) FROM customer GROUP BY store_id;

4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
    > SELECT country_id, COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(country_id) DESC LIMIT 1;

    > 44 60


## Ödev 8
1. test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
    > CREATE TABLE employee(id INT, name VARCHAR(50),  birthday DATE,  email VARCHAR(100));

2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
    > insert into employee  (id, name, birthday, email) values (1, 'Rawley', '2021-12-11', 'rponceford0@time.com');
insert into employee  (id, name, birthday, email) values (2, 'Betti', '2022-09-06', 'bclimson1@imdb.com');
insert into employee  (id, name, birthday, email) values (3, 'Darleen', '2022-02-02', 'dvedikhov2@reddit.com');
insert into employee  (id, name, birthday, email) values (4, 'Maximilian', '2022-05-16', 'mchaves3@shareasale.com');
insert into employee  (id, name, birthday, email) values (5, 'Shelby', '2022-09-14', 'sbrittles4@icio.us');
insert into employee  (id, name, birthday, email) values (6, 'Jackelyn', '2022-07-07', 'jlillyman5@nps.gov');
insert into employee  (id, name, birthday, email) values (7, 'Dexter', '2022-02-13', 'dpenkman6@bizjournals.com');
insert into employee  (id, name, birthday, email) values (8, 'Bartolomeo', '2022-05-06', 'blefriec7@symantec.com');
insert into employee  (id, name, birthday, email) values (9, 'Laurella', '2022-10-11', 'lmeijer8@xinhuanet.com');
insert into employee  (id, name, birthday, email) values (10, 'Jeniece', '2022-09-12', 'jshilvock9@bloglines.com');
insert into employee  (id, name, birthday, email) values (11, 'Bink', '2022-01-04', 'bcoshama@ocn.ne.jp');
insert into employee  (id, name, birthday, email) values (12, 'Nicholle', '2022-06-09', 'nkettlestringb@disqus.com');
insert into employee  (id, name, birthday, email) values (13, 'Juliet', '2021-11-15', 'jmckintyc@bbb.org');
insert into employee  (id, name, birthday, email) values (14, 'Legra', '2021-12-27', 'lorigand@hud.gov');
insert into employee  (id, name, birthday, email) values (15, 'Consolata', '2022-03-29', 'cloisie@theatlantic.com');
insert into employee  (id, name, birthday, email) values (16, 'Claudia', '2021-10-22', 'calvyf@theatlantic.com');
insert into employee  (id, name, birthday, email) values (17, 'Paloma', '2022-06-29', 'pharkusg@ovh.net');
insert into employee  (id, name, birthday, email) values (18, 'Web', '2022-03-02', 'wlattosh@hostgator.com');
insert into employee  (id, name, birthday, email) values (19, 'Clifford', '2022-01-09', 'ctapendeni@google.ru');
insert into employee  (id, name, birthday, email) values (20, 'Euphemia', '2022-02-12', 'eenderlej@ask.com');
insert into employee  (id, name, birthday, email) values (21, 'Briney', '2021-12-22', 'bcretneyk@acquirethisname.com');
insert into employee  (id, name, birthday, email) values (22, 'Danice', '2022-04-18', 'ddunfordl@vkontakte.ru');
insert into employee  (id, name, birthday, email) values (23, 'Trenna', '2022-03-03', 'tjakesm@answers.com');
insert into employee  (id, name, birthday, email) values (24, 'Arlina', '2022-03-03', 'astegern@hugedomains.com');
insert into employee  (id, name, birthday, email) values (25, 'Myrvyn', '2022-05-28', 'maeryo@jalbum.net');
insert into employee  (id, name, birthday, email) values (26, 'Daffi', '2022-01-29', 'dnathonp@hud.gov');
insert into employee  (id, name, birthday, email) values (27, 'Roseann', '2022-03-12', 'rjewissq@woothemes.com');
insert into employee  (id, name, birthday, email) values (28, 'Hettie', '2022-04-30', 'hpicklessr@jimdo.com');
insert into employee  (id, name, birthday, email) values (29, 'Sax', '2022-02-07', 'sfaustins@intel.com');
insert into employee  (id, name, birthday, email) values (30, 'Jeremias', '2022-07-20', 'jadcockst@reuters.com');
insert into employee  (id, name, birthday, email) values (31, 'Jessalyn', '2022-07-08', 'jrarityu@who.int');
insert into employee  (id, name, birthday, email) values (32, 'Cris', '2022-02-12', 'cgillaspyv@nyu.edu');
insert into employee  (id, name, birthday, email) values (33, 'Evangelina', '2022-09-26', 'edudsonw@reddit.com');
insert into employee  (id, name, birthday, email) values (34, 'Alva', '2021-11-02', 'aroothamx@foxnews.com');
insert into employee  (id, name, birthday, email) values (35, 'Vidovik', '2022-07-19', 'vtatteshally@is.gd');
insert into employee  (id, name, birthday, email) values (36, 'Jock', '2021-12-16', 'jpetrelliz@nymag.com');
insert into employee  (id, name, birthday, email) values (37, 'Kristy', '2022-05-17', 'koglassane10@rakuten.co.jp');
insert into employee  (id, name, birthday, email) values (38, 'Callie', '2022-02-16', 'cbyer11@zimbio.com');
insert into employee  (id, name, birthday, email) values (39, 'Natale', '2022-09-25', 'nbarosch12@123-reg.co.uk');
insert into employee  (id, name, birthday, email) values (40, 'Niven', '2022-04-13', 'nreignolds13@yellowbook.com');
insert into employee  (id, name, birthday, email) values (41, 'Nils', '2022-02-19', 'ndonlon14@usda.gov');
insert into employee  (id, name, birthday, email) values (42, 'Kirk', '2022-10-02', 'kcroisier15@freewebs.com');
insert into employee  (id, name, birthday, email) values (43, 'Kane', '2022-08-25', 'kdebenham16@tiny.cc');
insert into employee  (id, name, birthday, email) values (44, 'Kati', '2022-06-10', 'kjancso17@tiny.cc');
insert into employee  (id, name, birthday, email) values (45, 'Iosep', '2022-05-26', 'isains18@theglobeandmail.com');
insert into employee  (id, name, birthday, email) values (46, 'Veda', '2021-11-22', 'vorman19@list-manage.com');
insert into employee  (id, name, birthday, email) values (47, 'Cherilyn', '2022-03-12', 'cdalligan1a@jiathis.com');
insert into employee  (id, name, birthday, email) values (48, 'Gradey', '2022-07-05', 'godlin1b@sohu.com');
insert into employee  (id, name, birthday, email) values (49, 'Lenna', '2022-04-06', 'llesek1c@npr.org');
insert into employee  (id, name, birthday, email) values (50, 'Myrtie', '2022-01-13', 'mpetruskevich1d@apache.org');

3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
    > UPDATE employee SET name = 'değiştirildi' WHERE id IN (5,6,7,8,9,10)

4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
    > DELETE FROM employee WHERE id IN (5,6,7,8,9,10)

## Ödev 9
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
    > SELECT city.city, country.country FROM city INNER JOIN country ON country.country_id = city.city_id

2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
    > SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer INNER JOIN payment ON payment.customer_id = customer.customer_id

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
    > SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer INNER JOIN rental ON rental.customer_id = customer.customer_id

## Ödev 10
1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
    > SELECT city.city, country.country FROM city LEFT JOIN country ON country.country_id = city.city_id


2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
    > SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer RIGHT JOIN payment ON payment.customer_id = customer.customer_id


3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
    > SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer RIGHT JOIN rental ON rental.customer_id = customer.customer_id

## Ödev 11
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
    > SELECT first_name FROM actor UNION SELECT first_name FROM customer

2. actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
    > SELECT first_name FROM actor INTERSECT SELECT first_name FROM customer

3. actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
    > SELECT first_name FROM actor EXCEPT SELECT first_name FROM customer


4. İlk 3 sorguyu tekrar eden veriler için de yapalım.
    > SELECT first_name FROM actor UNION ALL SELECT first_name FROM customer

    > SELECT first_name FROM actor INTERSECT ALL SELECT first_name FROM customer

    > SELECT first_name FROM actor EXCEPT ALL SELECT first_name FROM customer
