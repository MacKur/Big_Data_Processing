# Big_Data_Processing
Project concerning data analysis of data containing information about differentiation of the altitude of the terrain (Europe) and data grouping (designate 6 groups) based on increase in altitude measured on the basis of atleast 10 points. The main purpose of the project was to compare performance between single local stations and clusters during big data processing.

### [ENG]
##### Project goals
The purpose of the task was to find areas in Europe with the greatest growth based on
minimum 10 measuring points. The results achieved were to be visualized.

##### Technologies used
Python 3.7 - a high-level programming language with an extensive library package. Thanks to its
transparent syntax it allows you to create advanced, but most of all readable source codes.

PODPAC - a Python library based on the SciPy ecosystem (Python, Numpy, SciPy, Matplotlib),
intended for simple and reproducible geospatial analytics that work locally or in the cloud.

Amazon EC2 - a web service that provides scalable computing power on demand in the AWS cloud.
It allows you to select instances with the desired parameters and perform calculations that require them,
which would be much more time consuming using the user's local power computing.

We decided to use such combination, due to the best knowledge of the programming language,
which is Python and the possibilities that comes with its extensive libraries. One of them is
precisely the PODPAC library, which we used for two most important reasons. First, it simplifies
the process of downloading geographic data from the AWS cloud to a minimum, which allows us to focus mainly
on the processing of received data. Secondly, it is an integral part of the already used in this project
language, which allowed us to stay 100% Python. During the implementation of the project, we wondered
on the possibility of using the Lambda PODPAC function in the AWS cloud, although we finally decided on
the use of Amazon EC2. This decision was made largely on the basis of the range of possibilities offered
through this service (freedom in choosing the computing power on demand, ease of configuration and just like the name itself
indicates the flexibility of this solution).

##### Implementation

The project implementation was based on the following steps:
1. Visualization the map of Europe.
2. Calculation of groups of areas consisting of 100 measurement points [10x10].
3. Count the average height height of each group.
4. Visualization of the height difference of groups of areas lying in Europe in the form of * .svg graphics.
5. Converting the obtained area data to a * .csv file.

Effects of limiting the Terrain Tiles dataset from Mapzen, containing the map of the whole world, to Europe
are shown in the figure below. Everything was made in Python and for the continent's visualization the PODPAC 
library was used due to its support for the used dataset and hence the ease of obtaining the tested data.

![](EUROPA.png)

After pre-processing the data containing information about the height of the terrain and selecting proper areas,
it was time to determine  with NumPy the average height in each group. The speed of task execution in the local
environment was compared with using the resources of Amazon Web Services. Naturally, with the use of AWS, 
the program worked a lotfaster, thanks to much more computing power available with EC2. Additionally,
the data needed for performing calculations (in the case of using EC2) did not even leave the cloud, so the code made in
the cloud only returned the effects. 

The measured time of the data processing are shown in the table below.

|  Local environment  |  Use of AWS   |
| -------------------- | -------------------- |
| ~50 min with zoom = 8 |  ~3 min with zoom = 8 |
|     i5 processor      |        8 vCPU        |



As we can see, the difference is impressive, and it is worth mentioning that it was achieved using an instance only about 
the size of m5.2xlarge (you can also choose instances much more powerful such as m5.24xlarge with 96 CPUs).

![](EC2_spec.png)

M5 instances feature either the 1st or 2nd generation Intel Xeon Platinum 8000 series processor (Skylake-SP or Cascade Lake) with a sustained all core Turbo CPU clock speed of up to 3.1 GHz.

##### Amazon Web Services
The AWS Elastic Computing service was used to launch the program. Access to EC2 is provided via PUTTY program. The use of 
cloud computing has significantly accelerated the data processing process, as can be seen from the previous table.

##### Results achieved
The final result of the program is a * .csv file, which contains the height data with division on measurement groups. 
A * .svg file is also saved, containing a map visualization taking into account the height increase in various areas of Europe.

![](result.svg)

### [PL]
### Raport z zadania projektowego nr 1

##### Cele projektu

Celem zadania by??o znalezienie grup obszar??w w Europie o najwi??kszym wzro??cie na podstawie 
minimum 10 punkt??w pomiarowych. Osi??gni??te wyniki mia??y zosta?? zwizualizowane.

##### Wykorzystane technologie 
Python 3.7 - j??zyk programowania wysokiego poziomu o rozbudowanym pakiecie bibliotek. Dzi??ki swojej
przejrzystej sk??adni umo??liwia tworzenie zaawansowanych, ale przede wszystkim czytelnych kod??w ??r??d??owych.

PODPAC - to biblioteka Pythona, opieraj??ca si?? na ekosystemie SciPy (Python, Numpy, SciPy, Matplotlib), 
aby umo??liwi?? proste oraz odtwarzalne analizy geoprzestrzenne, kt??re dzia??aj?? lokalnie lub w chmurze.

Amazon EC2 - to us??uga internetowa zapewniaj??ca skalowaln?? moc obliczeniow?? na ????danie w chmurze AWS.
Pozwala na wyb??r instancji o po????danych przez nas parametrach i wykonywanie na nich wymagaj??cych oblicze??,
kt??re by??yby o wiele bardziej czasoch??onne z wykorzystaniem posiadanej przez u??ytkownika lokalnie mocy 
obliczeniowej.

Zdecydowali??my si?? na w??a??nie takie po????czenie, z racji na najwi??ksz?? styczno???? z j??zykiem programowania,
jakim jest Python oraz mo??liwo??ci kt??re nios?? za sob?? jego rozbudowane biblioteki. Jedn?? z nich jest
w??a??nie biblioteka PODPAC, z kt??rej skorzystali??my z dw??ch najistotniejszych powod??w. Po pierwsze upraszcza
do minimum proces pobierania danych geograficznych z chmury AWS co pozwala nam skupi?? si?? w g????wnej mierze 
na przetwarzaniu otrzymanych danych. Po drugie jest integraln?? cz????ci?? wykorzystywanego przez nas w projekcie 
j??zyka, co umo??liwi??o nam pozostanie w 100% przy Pythonie. W trakcie realizacji projektu zastanawiali??my si?? 
nad mo??liwo??ci?? wykorzystania funkcji Lambda PODPAC w chmurze AWS, aczkolwiek finalnie zdecydowali??my si?? na
wykorzystanie Amazon EC2. Decyzja ta zapad??a w g????wnej mierze bior??c pod uwag?? szereg mo??liwo??ci oferowanych
przez t?? us??ug?? (dowolno???? w wyborze mocy obliczeniowej na ????danie, ??atwo???? konfiguracji oraz jak sama nazwa
wskazuje elastyczno???? tego rozwi??zania)

##### Realizacja

Wykonanie projektu opiera??o si?? o nast??puj??ce kroki:
1. Wizualizacja obszaru Europy.
2. Wyznaczenie grup obszar??w sk??adaj??cych si?? ze 100 punkt??w pomiarowych [10x10].
3. Policzenie ??redniego wzrostu wysoko??ci ka??dej grupy.
4. Wizualizacja r????nicy wysoko??ci grup obszar??w le????cych w Europie w postaci grafiki *.svg.
5. Konwersja uzyskanych danych o obszarach do pliku *.csv.

Efekty ograniczenia obszaru datasetu Terrain Tiles od Mapzen, zawieraj??cego map?? ca??ego ??wiata, do Europy
przedstawione zosta??y na rysunku poni??ej. Ca??o???? wykonana zosta??a w j??zyku Python, a do zwizualizowania 
rozwa??anego kontynentu wykorzystano bibliotek?? PODPAC ze wzgl??du na jej wsparcie dla u??ywanego datasetu, 
a co za tym idzie ??atwo???? pozyskiwania badanych danych.

![](EUROPA.png)


Po wst??pnym przetworzeniu danych zawieraj??cych informacje o wysoko??ci terenu na rozwa??anym kontynencie 
i wydzieleniu odpowiednich grup obszar??w przyst??piono do wyznaczenia w ka??dej grupie ??redniego wzrostu 
wysoko??ci za pomoc?? biblioteki NumPy. Dokonano por??wnania szybko??ci realizacji zadania w lokalnym ??rodowisku
oraz przy wykorzystaniu zasob??w Amazon Web Services. Naturalnie przy pomocy AWS program dzia??a?? znacznie 
szybciej, za spraw?? du??o wi??kszej mocy obliczeniowej dost??pnej dzi??ki EC2. Dodatkowo, dane potrzebne do 
wykonania oblicze?? (w przypadku wykorzystania EC2) nawet nie opuszcza??y chmury, wi??c kod wykonany w 
chmurze zwraca?? nam tylko i wy????cznie efekty.

Zmierzone czasy przetwarzania danych przedstawione s?? w poni??szej tabeli.

|  Lokalne ??rodowisko  |  Wykorzystanie AWS   |
| -------------------- | -------------------- |
| ~50 min dla zoom = 8 |  ~3 min dla zoom = 8 |
|     Procesor i5      |        8 vCPU        |

Jak wida?? r????nica robi wra??enie, a warto nadmieni??, i?? osi??gni??ta zosta??a przy wykorzystaniu instancji 
zaledwie o rozmiarze m5.2xlarge, (mo??liwe do wyboru by??y r??wnie?? instancje kilka-kilkana??cie razy mocniejsze
takie jak m5.24xlarge posiadaj??ce 96 procesor??w).

![](EC2_spec.png)

Instancje M5 wyposa??one s?? w procesory Intel Xeon Platinum 8000 pierwszej lub drugiej generacji (Skylake-SP 
lub Cascade Lake) ze sta???? szybko??ci?? taktowania wszystkich rdzeni Turbo CPU do 3,1 GHz.

##### Amazon Web Services
Do uruchomienia programu pos??u??ono si?? serwisem AWS Elastic Computing. Dost??p do EC2 realizowany jest poprzez 
program PUTTY. Wykorzystanie chmury obliczeniowej znacznie przyspieszy??o proces przetwarzania danych, co wida?? 
z poprzedniej tabeli.

##### Osi??gniete wyniki

Efektem ko??cowym dzia??ania programu jest plik *.csv, w kt??rym znajduj?? si?? dane dotycz??ce wysoko??ci z podzia??em 
na grupy pomiarowe. Zapisywany jest r??wnie?? plik *.svg zawieraj??cy wizualizacj?? mapy uwzgl??dniaj??cej wzrost wysoko??ci 
w r????nych obszarach Europy.

![](result.svg)

