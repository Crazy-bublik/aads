---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.15.2
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

<!-- #region -->
<h1> ОТЧЕТ ПО ПРОЕКТНОЙ РАБОТЕ </h1>
<h3> От города N в город M </h3>
<br>
<h4> Цель работы: </h4>
Создание проекта.
<br>
<h4> Задание: </h4>

1. Ознакомиться с теоретическим содержанием задачи(историей возникновения, существующими методами решения, практической значимостью и т.д.).
2. На основе данных какой-либо социальной сети, новостного сайта, онлайн-энциклопедии построить граф взаимосвязи городов (России, Мира), используя для хранения данных подходящую структуру данных.
3. Реализовать алгоритм нахождения оптимального пути между узлами графа.
4. Используя реализацию алгоритма из предыдущего пункта, написать приложение строящее маршрут между двумя произвольными городами.
5. Проанализировать насколько коррелируют параметры полученных таким образом "маршрутов" с реальными маршрутами между городами.
6. Провести анализ эффективности используемых структур данных и алгоритмов.
7. Подготовить отчет о проделанной работе.
<br>

<h4> Code Listing: </h4>

```python
city = { #список всех столиц мира
    ...
}

def way(graph, start, end) #функция для поиска оптимального пути
    ...

#Приложение
print(...)
while True:
    first = input(...)
    second = input(...)
    ...
    way(city, first, second)                 
```
<h4> Выводы </h4>
В ходе проектной работы был построен граф взаимосвязи столиц мира, реализован алгоритм нахождения оптимального пути между узлами графа на основе алгоритма Дэйкстры и написано приложение, строящее маршрут между двумя произвольными столицами мира.
<br>
<!-- #endregion -->

```python
city = {
	'Abu Dhabi': {'Riyadh': 703, 'Muscat': 425, 'Doha': 561, 'Manama': 515, 'Kuwait City': 882, 'Tehran': 1227, 'Baghdad': 1086, 'Amman': 1984, 'Damascus': 1379, 'Beirut': 1329, 'Sanaʻa': 1593, 'Valletta': 4006},
	'Abuja': {'Niamey': 746, 'NʻDjamena': 830, 'Yaounde': 1106, 'Porto-Novo': 1150},
	'Accra': {'Lome': 156, 'Ouagadougou': 381, 'Yamoussoukro': 202, 'Porto-Novo': 255},
	'Addis Ababa': {'Asmara': 976, 'Djibouti City': 930, 'Juba': 1347, 'Khartoum': 1773, 'Mogadishu': 1503, 'Nairobi': 1021},
	'Algiers': {'Bamako': 1354, 'Niamey': 1320, 'Nouakchott': 1561, 'Tripoli': 1008, 'Tunis': 257, 'Rabat': 1175},
	'Amman': {'Damascus': 176, 'Jerusalem': 105, 'Riyadh': 925, 'Baghdad': 545, 'Abu Dhabi': 1984, 'Cairo': 603},
	'Amsterdam': {'Brussels': 208, 'Berlin': 575, 'London': 358, 'Paris': 431, 'Luxembourg': 339, 'Copenhagen': 728, 'Oslo': 1038, 'Stockholm': 1060, 'Warsaw': 1140, 'Prague': 766},
	'Andorra la Vella': {'Paris': 850, 'Madrid': 626, 'Lisbon': 1047},
	'Ankara': {'Athens': 700, 'Sofia': 998, 'Tbilisi': 1760, 'Tehran': 2660, 'Baghdad': 1180, 'Damascus': 775, 'Baku': 1262, 'Bucharest': 748, 'Nicosia': 250, 'Sukhumi': 500, 'Tokyo': 8740, 'Yerevan': 993},
	'Antananarivo': {'Maputo': 1058, 'Moroni': 507, 'Port Louis': 981, 'Victoria': 1388},
	'Apia': {'Pago Pago': 38, 'Nukuʻalofa': 417, 'Suva': 1898, 'South Tarawa': 3303, 'Tskhinvali': 1663},
	'Ashgabat': {'Tehran': 1156, 'Tashkent': 1108, 'Kabul': 427, 'Astana': 1509},
	'Asmara': {'Khartoum': 1075, 'Addis Ababa': 976, 'Djibouti City': 301},
	'Astana': {'Moscow': 2274, 'Beijing': 4768, 'Bishkek': 949, 'Tashkent': 1300, 'Ashgabat': 1509},
	'Asuncion': {'Brasilia': 1386, 'Buenos Aires': 1137, 'La Paz': 895, 'Santiago': 1651},
	'Athens': {'Tirana': 501, 'Sofia': 578, 'Ankara': 700, 'Nicosia': 692, 'Skopje': 797, 'Bucharest': 996, 'Cairo': 1123, 'Valletta': 1034},
	'Baghdad': {'Tehran': 981, 'Amman': 545, 'Riyadh': 907, 'Damascus': 371, 'Ankara': 1180, 'Kuwait City': 533, 'Abu Dhabi': 1086},
	'Baku': {'Moscow': 2160, 'Tehran': 679, 'Ankara': 1262, 'Tbilisi': 379, 'Yerevan': 395},
	'Bamako': {'Nouakchott': 754, 'Algiers': 1354, 'Yamoussoukro': 949, 'Conakry': 671, 'Ouagadougou': 317, 'Dakar': 1058, 'Niamey': 900},
	'Bandar Seri Begawan': {'Kuala Lumpur': 1539, 'Jakarta': 1256},
	'Bangkok': {'Naypyidaw': 980, 'Phnom Penh': 576, 'Vientiane': 570, 'Kuala Lumpur': 1544},
	'Bangui': {'Yaounde': 924, 'NʻDjamena': 1552, 'Khartoum': 1254, 'Juba': 1232, 'Kinshasa': 1665, 'Brazzaville': 633},
	'Banjul': {'Dakar': 303, 'Conakry': 742, 'Bissau': 41, 'Praia': 1509},
	'Basseterre': {'St. Johnʻs': 53, 'St. Georgeʻs': 314, 'Roseau': 253},
	'Beijing': {'Ulaanbaatar': 1219, 'Moscow': 7489, 'Pyongyang': 1332, 'New Delhi': 3817, 'Islamabad': 3915, 'Bishkek': 3466, 'Dushanbe': 3195, 'Hanoi': 1474, 'Kathmandu': 2218, 'Naypyidaw': 1855, 'Astana': 4768, 'Seoul': 953, 'Taipei': 1760, 'Tashkent': 4400, 'Thimphu': 2500, 'Tokyo': 2106, 'Vientiane': 1773},
	'Beirut': {'Damascus': 53, 'Jerusalem': 235, 'Abu Dhabi': 1329},
	'Belgrade': {'Budapest': 316, 'Bucharest': 448, 'Sofia': 397, 'Zagreb': 367, 'Sarajevo': 245, 'Podgorica': 455, 'Skopje': 315, 'Chisinau': 800, 'Pristina': 385, 'Tirana': 398},
	'Belmopan': {'Guatemala City': 205, 'Mexico City': 2290, 'Tegucigalpa': 483, 'San Jose': 1406, 'San Salvador': 503},
	'Berlin': {'Warsaw': 516, 'Prague': 280, 'Vienna': 523, 'Bern': 651, 'Paris': 1050, 'Amsterdam': 575, 'Copenhagen': 355, 'Brussels': 650, 'Luxembourg': 764, 'Rabat': 2387, 'Vaduz': 770, 'Victoria': 10892, 'Vilnius': 818, 'Edinburgh': 1092},
	'Bern': {'Berlin': 651, 'Paris': 540, 'Rome': 970, 'Vienna': 810, 'Monaco': 549, 'Vaduz': 157, 'Vatican City': 861, 'Victoria': 9789},
	'Bishkek': {'Astana': 949, 'Tashkent': 520, 'Dushanbe': 550, 'Beijing': 3466},
	'Bissau': {'Dakar': 300, 'Conakry': 300, 'Banjul': 41, 'Praia': 1088},
	'Bogota': {'Caracas': 500, 'Brasilia': 1600, 'Lima': 1800, 'Quito': 700, 'Panama City': 625},
	'Brasilia': {'Buenos Aires': 1343, 'Sucre': 1645, 'Bogota': 1600, 'Lima': 1899, 'Asuncion': 1386, 'Montevideo': 2275, 'Caracas': 2296, 'Georgetown': 3284, 'La Paz': 3060, 'Paramaribo': 2535, 'Santiago': 3091, 'Quito': 3776},
	'Bratislava': {'Vienna': 55, 'Prague': 290, 'Budapest': 162, 'Warsaw': 532, 'Kiev': 1004},
	'Brazzaville': {'Libreville': 173, 'Yaounde': 277, 'Bangui': 633, 'Kinshasa': 713, 'Luanda': 684, 'Bujumbura': 1225},
	'Bridgetown': {'Castries': 282, 'Kingstown': 143, 'Roseau': 236, 'St. Georgeʻs': 140, 'San Juan': 3110},
	'Brussels': {'Amsterdam': 208, 'Berlin': 650, 'Luxembourg': 220, 'Paris': 264, 'London': 320, 'Victoria': 5529, 'Edinburgh': 740},
	'Bucharest': {'Budapest': 799, 'Belgrade': 448, 'Sofia': 307, 'Kiev': 1011, 'Chisinau': 290, 'Ankara': 748, 'Athens': 996},
	'Budapest': {'Vienna': 243, 'Bratislava': 162, 'Kiev': 885, 'Bucharest': 799, 'Belgrade': 316, 'Zagreb': 349, 'Ljubljana': 435, 'Chisinau': 850, 'Sarajevo': 362},
	'Buenos Aires': {'Montevideo': 206, 'Brasilia': 1343, 'Asuncion': 1137, 'La Paz': 1486, 'Santiago': 1408, 'Sucre': 1227},
	'Cairo': {'Jerusalem': 610, 'Khartoum': 1250, 'Tripoli': 1670, 'Amman': 603, 'Riyadh': 1641, 'Nicosia': 612, 'Athens': 1123, 'Sanaʻa': 1416},
	'Canberra': {'Wellington': 2143, 'Jakarta': 4948, 'Port Moresby': 2591, 'Dili': 3162, 'Honiara': 3382, 'Suva': 4169, 'Tskhinvali': 8945},
	'Caracas': {'Bogota': 500, 'Brasilia': 2296, 'Georgetown': 565, 'Castries': 1127, 'Port of Spain': 130, 'Quito': 2245},
	'Castries': {'Bridgetown': 282, 'Kingstown': 186, 'St. Georgeʻs': 375, 'Port of Spain': 487, 'Roseau': 217, 'Caracas': 1127, 'St. Johnʻs': 411, 'San Juan': 496},
	'Chisinau': {'Bucharest': 290, 'Sofia': 570, 'Budapest': 850, 'Belgrade': 800, 'Kiev': 363},
	'Colombo, Sri Jayawardenepura Kotte': {'New Delhi': 1300, 'Male': 700},
	'Conakry': {'Bissau': 300, 'Freetown': 500, 'Monrovia': 450, 'Yamoussoukro': 1100, 'Bamako': 671, 'Banjul': 742, 'Dakar': 706},
	'Copenhagen': {'Berlin': 355, 'Stockholm': 522, 'Oslo': 519, 'Amsterdam': 728, 'Reykjavik': 1840, 'Edinburgh': 870},
	'Dakar': {'Nouakchott': 485, 'Bamako': 1058, 'Conakry': 706, 'Banjul': 303, 'Bissau': 300, 'Praia': 1587},
	'Damascus': {'Beirut': 53, 'Amman': 176, 'Jerusalem': 239, 'Abu Dhabi': 1379, 'Ankara': 775, 'Baghdad': 371},
	'Dhaka': {'New Delhi': 1346, 'Naypyidaw': 739, 'Thimphu': 423, 'Male': 1159, 'Tokyo': 4370},
	'Dili': {'Jakarta': 1671, 'Canberra': 3162},
	'Djibouti City': {'Addis Ababa': 930, 'Asmara': 301, 'Mogadishu': 1033},
	'Dodoma': {'Nairobi': 741, 'Kampala': 859, 'Kigali': 991, 'Bujumbura': 1017, 'Lusaka': 1070, 'Lilongwe': 1151, 'Maputo': 1474, 'Gitega': 602, 'Kinshasa': 1696, 'Moroni': 945},
	'Doha': {'Riyadh': 405, 'Abu Dhabi': 561, 'Manama': 146, 'Kuwait City': 135, 'Muscat': 1168},
	'Dublin': {'London': 461, 'Belfast': 168, 'Reykjavik': 1461, 'Edinburgh': 512},
	'Dushanbe': {'Kabul': 394, 'Tashkent': 430, 'Bishkek': 550, 'Beijing': 3195},
	'Freetown': {'Conakry': 500, 'Monrovia': 387},
	'Funafuti': {'South Tarawa': 1286},
	'Gaborone': {'Pretoria, Cape Town, Bloemfontein': 351, 'Harare': 811, 'Lusaka': 1052, 'Windhoek': 1186},
	'Georgetown': {'Caracas': 565, 'Brasilia': 3284},
	'Gitega': {'Kigali': 97, 'Dodoma': 602, 'Kinshasa': 1608},
	'Guatemala City': {'Mexico City': 829, 'Belmopan': 205, 'San Salvador': 269, 'Tegucigalpa': 342, 'Managua': 271, 'San Jose': 1065},
	'Hanoi': {'Beijing': 1474, 'Vientiane': 421, 'Phnom Penh': 1010, 'Kuala Lumpur': 2433, 'Manila': 1559, 'Taipei': 1400, 'Tokyo': 3790},
	'Harare': {'Pretoria, Cape Town, Bloemfontein': 1409, 'Lusaka': 371, 'Maputo': 1086, 'Gaborone': 811, 'Lilongwe': 594},
	'Havana': {'Washington, D.C.': 1753, 'Mexico City': 1726, 'Kingston': 691, 'Port-au-Prince': 1608, 'Santo Domingo': 1635, 'Nassau': 282},
	'Helsinki': {'Moscow': 1106, 'Stockholm': 398, 'Oslo': 391, 'Tallinn': 81, 'Reykjavik': 2080, 'Riga': 395},
	'Honiara': {'Port Moresby': 834, 'Port Vila': 1059, 'Yaren': 2349, 'Canberra': 3382, 'Majuro': 2300},
	'Islamabad': {'New Delhi': 689, 'Beijing': 3915, 'Kabul': 368, 'Tehran': 2406, 'Kathmandu': 1348},
	'Jakarta': {'Kuala Lumpur': 1075, 'Dili': 1671, 'Canberra': 4948, 'Port Moresby': 2627, 'Bandar Seri Begawan': 1256, 'Male': 5337, 'Manila': 2540},
	'Jerusalem': {'Beirut': 235, 'Damascus': 239, 'Amman': 105, 'Cairo': 610},
	'Juba': {'Khartoum': 1387, 'Addis Ababa': 1347, 'Nairobi': 1313, 'Kampala': 760, 'Bangui': 1232, 'Kinshasa': 1741},
	'Kabul': {'Islamabad': 368, 'Dushanbe': 394, 'Ashgabat': 427, 'Tehran': 4337},
	'Kampala': {'Juba': 760, 'Nairobi': 414, 'Dodoma': 859, 'Kigali': 379, 'Kinshasa': 1678, 'Bujumbura': 456},
	'Kathmandu': {'New Delhi': 814, 'Beijing': 2218, 'Thimphu': 427, 'Islamabad': 1348},
	'Khartoum': {'Cairo': 1250, 'Juba': 1387, 'Asmara': 1075, 'Addis Ababa': 1773, 'Bangui': 1254, 'NʻDjamena': 1600, 'Sanaʻa': 1316},
	'Kigali': {'Kampala': 379, 'Dodoma': 991, 'Bujumbura': 55, 'Kinshasa': 650, 'Gitega': 97},
	'Kingston': {'Washington, D.C.': 2189, 'Havana': 691, 'Port-au-Prince': 356, 'Nassau': 189},
	'Kingstown': {'Bridgetown': 143, 'Castries': 186, 'St. Georgeʻs': 100, 'Roseau': 162, 'St. Johnʻs': 86},
	'Kinshasa': {'Brazzaville': 713, 'Luanda': 1299, 'Bangui': 1665, 'Juba': 1741, 'Kampala': 1678, 'Kigali': 650, 'Dodoma': 1696, 'Gitega': 1608, 'Lusaka': 1230},
	'Kuala Lumpur': {'Bangkok': 1544, 'Singapore': 297, 'Jakarta': 1075, 'Bandar Seri Begawan': 1539, 'Manila': 2671, 'Hanoi': 2433},
	'Kuwait City': {'Baghdad': 533, 'Riyadh': 374, 'Abu Dhabi': 882, 'Doha': 135, 'Manama': 60},
	'Kiev': {'Minsk': 484, 'Moscow': 755, 'Chisinau': 363, 'Bratislava': 1004, 'Budapest': 885, 'Warsaw': 590, 'Bucharest': 1011},
	'La Paz': {'Lima': 1131, 'Santiago': 1645, 'Buenos Aires': 1486, 'Brasilia': 3060, 'Asuncion': 895, 'Sucre': 302},
	'Libreville': {'Sao Tome': 245, 'Malabo': 287, 'Yaounde': 547, 'Brazzaville': 173},
	'Lilongwe': {'Dodoma': 1151, 'Maputo': 1457, 'Lusaka': 744, 'Harare': 594},
	'Lima': {'Quito': 917, 'Bogota': 1800, 'La Paz': 1131, 'Santiago': 2246, 'Brasilia': 1899, 'Sucre': 1195},
	'Lisbon': {'Madrid': 623, 'Andorra la Vella': 1047, 'Paris': 1733, 'Rabat': 741},
	'Ljubljana': {'Vienna': 276, 'Rome': 650, 'Zagreb': 140, 'Budapest': 435, 'Sarajevo': 418, 'Vatican City': 1120},
	'Lome': {'Accra': 156, 'Ouagadougou': 441, 'Porto-Novo': 174},
	'London': {'Paris': 343, 'Brussels': 320, 'Amsterdam': 358, 'Dublin': 461, 'Reykjavik': 1844, 'Belfast': 523, 'Edinburgh': 539},
	'Luanda': {'Kinshasa': 1299, 'Brazzaville': 684, 'Windhoek': 1120, 'Lusaka': 1300},
	'Lusaka': {'Kinshasa': 1230, 'Dodoma': 1070, 'Lilongwe': 744, 'Maputo': 1400, 'Harare': 371, 'Gaborone': 1052, 'Luanda': 1300},
	'Luxembourg': {'Brussels': 220, 'Berlin': 764, 'Paris': 300, 'Amsterdam': 339, 'Victoria': 7094, 'Edinburgh': 785},
	'Madrid': {'Lisbon': 623, 'Paris': 1050, 'Andorra la Vella': 626, 'Rabat': 1200},
	'Majuro': {'Palikir': 250, 'Yaren': 700, 'Port Moresby': 2600, 'Honiara': 2300, 'South Tarawa': 2690},
	'Malabo': {'Yaounde': 150, 'Libreville': 287},
	'Male': {'New Delhi': 1684, 'Colombo, Sri Jayawardenepura Kotte': 700, 'Dhaka': 1159, 'Jakarta': 5337},
	'Managua': {'Tegucigalpa': 314, 'San Jose': 285, 'San Salvador': 75, 'Guatemala City': 271},
	'Manama': {'Riyadh': 423, 'Doha': 146, 'Kuwait City': 60, 'Abu Dhabi': 515},
	'Manila': {'Taipei': 1094, 'Hanoi': 1559, 'Kuala Lumpur': 2671, 'Jakarta': 2540, 'Tokyo': 2985},
	'Maputo': {'Pretoria, Cape Town, Bloemfontein': 496, 'Mbabane': 315, 'Harare': 1086, 'Dodoma': 1474, 'Lilongwe': 1457, 'Antananarivo': 1058, 'Lusaka': 1400},
	'Maseru': {'Pretoria, Cape Town, Bloemfontein': 281},
	'Mbabane': {'Maputo': 315, 'Pretoria, Cape Town, Bloemfontein': 336},
	'Mexico City': {'Washington, D.C.': 2510, 'Guatemala City': 829, 'Belmopan': 2290, 'Havana': 1726, 'San Jose': 2829},
	'Minsk': {'Moscow': 690, 'Kiev': 484, 'Warsaw': 490, 'Vilnius': 160, 'Riga': 200, 'Tallinn': 600},
	'Mogadishu': {'Nairobi': 680, 'Addis Ababa': 1503, 'Djibouti City': 1033},
	'Monaco': {'Paris': 920, 'Rome': 541, 'Bern': 549, 'Vatican City': 982},
	'Monrovia': {'Freetown': 387, 'Conakry': 450, 'Yamoussoukro': 850},
	'Montevideo': {'Brasilia': 2275, 'Buenos Aires': 206, 'Santiago': 2068},
	'Moroni': {'Dodoma': 945, 'Antananarivo': 507},
	'Moscow': {'Minsk': 690, 'Kiev': 755, 'Tallinn': 870, 'Riga': 750, 'Vilnius': 791, 'Helsinki': 1106, 'Oslo': 1490, 'Astana': 2274, 'Tbilisi': 1647, 'Beijing': 7489, 'Baku': 2160, 'Pyongyang': 6357, 'Seoul': 6380, 'Sukhumi': 840, 'Tashkent': 3300, 'Tokyo': 7484, 'Ulaanbaatar': 4636, 'Warsaw': 1200},
	'Muscat': {'Abu Dhabi': 425, 'Riyadh': 1100, 'Sanaʻa': 1300, 'Doha': 1168},
	'Nairobi': {'Dodoma': 741, 'Kampala': 414, 'Juba': 1313, 'Addis Ababa': 1021, 'Mogadishu': 680},
	'Nassau': {'Washington, D.C.': 1732, 'Havana': 282, 'Port-au-Prince': 946, 'Kingston': 189},
	'Naypyidaw': {'Bangkok': 980, 'Beijing': 1855, 'New Delhi': 2579, 'Dhaka': 739, 'Vientiane': 375},
	'NʻDjamena': {'Yaounde': 900, 'Abuja': 830, 'Niamey': 1100, 'Khartoum': 1600, 'Bangui': 1552},
	'New Delhi': {'Islamabad': 689, 'Beijing': 3817, 'Kathmandu': 814, 'Thimphu': 1285, 'Dhaka': 1346, 'Naypyidaw': 2579, 'Colombo, Sri Jayawardenepura Kotte': 1300, 'Male': 1684},
	'Ngerulmud': {},
	'Niamey': {'Ouagadougou': 500, 'Porto-Novo': 600, 'Abuja': 746, 'Bamako': 900, 'Algiers': 1320, 'NʻDjamena': 1100},
	'Nicosia': {'Athens': 692, 'Ankara': 250, 'Cairo': 612, 'Valletta': 512},
	'Nouakchott': {'Rabat': 1240, 'Dakar': 485, 'Bamako': 754, 'Algiers': 1561},
	'Nukuʻalofa': {'Apia': 417, 'South Tarawa': 2144, 'Tskhinvali': 2931},
	'Oslo': {'Stockholm': 520, 'Helsinki': 391, 'Moscow': 1490, 'Amsterdam': 1038, 'Copenhagen': 519, 'Reykjavik': 1581, 'Riga': 789, 'Edinburgh': 1045},
	'Ottawa': {'Washington, D.C.': 725, 'Santo Domingo': 3194, 'Tokyo': 10410},
	'Ouagadougou': {'Accra': 381, 'Yamoussoukro': 500, 'Bamako': 317, 'Niamey': 500, 'Lome': 441},
	'Pago Pago': {'Apia': 38},
	'Palikir': {'Majuro': 250},
	'Panama City': {'San Jose': 320, 'Bogota': 625, 'Quito': 1788, 'San Salvador': 726},
	'Paramaribo': {'Paris': 7193, 'Brasilia': 2535},
	'Paris': {'Brussels': 264, 'Berlin': 1050, 'Madrid': 1050, 'Rome': 1106, 'Bern': 540, 'Amsterdam': 431, 'Andorra la Vella': 850, 'Lisbon': 1733, 'London': 343, 'Luxembourg': 300, 'Monaco': 920, 'Rabat': 2004, 'Vatican City': 1084, 'Paramaribo': 7193, 'Edinburgh': 874},
	'Phnom Penh': {'Hanoi': 1010, 'Bangkok': 576, 'Vientiane': 786},
	'Podgorica': {'Belgrade': 455, 'Zagreb': 455, 'Sarajevo': 190, 'Tirana': 153, 'Pristina': 120, 'Skopje': 405, 'Sofia': 543},
	'Port Louis': {'Antananarivo': 981, 'Victoria': 1200},
	'Port Moresby': {'Jakarta': 2627, 'Canberra': 2591, 'Honiara': 834, 'Majuro': 2600},
	'Port of Spain': {'Caracas': 130, 'Castries': 487, 'Roseau': 390, 'St. Georgeʻs': 338, 'St. Johnʻs': 420},
	'Port Vila': {'Honiara': 1059, 'Suva': 2356},
	'Port-au-Prince': {'Santo Domingo': 275, 'Havana': 1608, 'Kingston': 356, 'Roseau': 793, 'San Juan': 2630, 'Nassau': 946},
	'Porto-Novo': {'Abuja': 1150, 'Accra': 255, 'Lome': 174, 'Niamey': 600},
	'Prague': {'Berlin': 280, 'Vienna': 300, 'Warsaw': 500, 'Amsterdam': 766, 'Bratislava': 290},
	'Praia': {'Dakar': 1587, 'Banjul': 1509, 'Bissau': 1088},
	'Pretoria, Cape Town, Bloemfontein': {'Windhoek': 1300, 'Gaborone': 351, 'Harare': 1409, 'Maputo': 496, 'Maseru': 281, 'Mbabane': 336},
	'Pristina': {'Skopje': 78, 'Podgorica': 120, 'Tirana': 81, 'Belgrade': 385, 'Sarajevo': 271},
	'Pyongyang': {'Seoul': 181, 'Beijing': 1332, 'Moscow': 6357, 'Tokyo': 1353},
	'Quito': {'Bogota': 700, 'Lima': 917, 'Brasilia': 3776, 'Panama City': 1788, 'Caracas': 2245, 'Santiago': 4378},
	'Rabat': {'Madrid': 1200, 'Lisbon': 741, 'Algiers': 1175, 'Paris': 2004, 'Rome': 1608, 'Berlin': 2387, 'Nouakchott': 1240},
	'Reykjavik': {'Oslo': 1581, 'Stockholm': 1532, 'Helsinki': 2080, 'Copenhagen': 1840, 'London': 1844, 'Dublin': 1461, 'Edinburgh': 1645},
	'Riga': {'Tallinn': 279, 'Vilnius': 267, 'Stockholm': 389, 'Helsinki': 395, 'Oslo': 789, 'Warsaw': 561, 'Minsk': 200, 'Moscow': 750},
	'Riyadh': {'Manama': 423, 'Doha': 405, 'Abu Dhabi': 703, 'Kuwait City': 374, 'Amman': 925, 'Muscat': 1100, 'Sanaʻa': 1328, 'Baghdad': 907, 'Cairo': 1641},
	'Rome': {'Bern': 970, 'Vienna': 833, 'Ljubljana': 650, 'Monaco': 541, 'Vaduz': 784, 'Zagreb': 516, 'Tirana': 612, 'Paris': 1106, 'Rabat': 1608, 'Tunis': 1332, 'Valletta': 690, 'Vatican City': 281, 'Victoria': 17331},
	'Roseau': {'St. Georgeʻs': 36, 'Port of Spain': 390, 'Castries': 217, 'Bridgetown': 236, 'Basseterre': 253, 'Kingstown': 162, 'Port-au-Prince': 793, 'St. Johnʻs': 145},
	'St. Georgeʻs': {'St. Johnʻs': 145, 'Bridgetown': 140, 'Castries': 375, 'Port of Spain': 338, 'Roseau': 36, 'Kingstown': 100, 'Basseterre': 314},
	'St. Johnʻs': {'St. Georgeʻs': 145, 'Castries': 411, 'Port of Spain': 420, 'Basseterre': 53, 'Roseau': 145, 'Kingstown': 86},
	'San Jose': {'Managua': 285, 'San Salvador': 329, 'Panama City': 320, 'Tegucigalpa': 1063, 'Belmopan': 1406, 'Guatemala City': 1065, 'Mexico City': 2829},
	'San Marino': {'Vatican City': 366},
	'San Salvador': {'Guatemala City': 269, 'Belmopan': 503, 'Tegucigalpa': 422, 'Managua': 75, 'Santo Domingo': 1146, 'Panama City': 726, 'San Jose': 329},
	'Sanaʻa': {'Muscat': 1300, 'Riyadh': 1328, 'Abu Dhabi': 1593, 'Khartoum': 1316, 'Cairo': 1416},
	'Santiago': {'Buenos Aires': 1408, 'La Paz': 1645, 'Lima': 2246, 'Asuncion': 1651, 'Brasilia': 3091, 'Montevideo': 2068, 'Quito': 4378, 'Sucre': 2737},
	'Santo Domingo': {'Washington, D.C.': 2335, 'Port-au-Prince': 275, 'Ottawa': 3194, 'San Juan': 254, 'Havana': 1635, 'San Salvador': 1146},
	'Sao Tome': {'Libreville': 245},
	'Sarajevo': {'Podgorica': 190, 'Belgrade': 245, 'Zagreb': 392, 'Ljubljana': 418, 'Tirana': 449, 'Budapest': 362, 'Skopje': 348, 'Pristina': 271, 'Sofia': 376},
	'Seoul': {'Beijing': 953, 'Pyongyang': 181, 'Moscow': 6380, 'Ulaanbaatar': 1992, 'Tokyo': 1158, 'Taipei': 1123},
	'Singapore': {'Kuala Lumpur': 297},
	'Skopje': {'Sofia': 238, 'Tirana': 319, 'Belgrade': 315, 'Podgorica': 405, 'Pristina': 78, 'Athens': 797, 'Sarajevo': 348},
	'Sofia': {'Tirana': 339, 'Skopje': 238, 'Sarajevo': 376, 'Podgorica': 543, 'Belgrade': 397, 'Athens': 578, 'Ankara': 998, 'Bucharest': 307, 'Chisinau': 570},
	'South Tarawa': {'Funafuti': 1286, 'Majuro': 2690, 'Nukuʻalofa': 2144, 'Suva': 2564, 'Apia': 3303},
	'Stockholm': {'Helsinki': 398, 'Oslo': 520, 'Copenhagen': 522, 'Tallinn': 380, 'Riga': 389, 'Vilnius': 615, 'Amsterdam': 1060, 'Reykjavik': 1532},
	'Sucre': {'La Paz': 302, 'Lima': 1195, 'Brasilia': 1645, 'Buenos Aires': 1227, 'Santiago': 2737},
	'Sukhumi': {'Ankara': 500, 'Tbilisi': 370, 'Moscow': 840},
	'Suva': {'Apia': 1898, 'Canberra': 4169, 'Wellington': 2850, 'Port Vila': 2356, 'South Tarawa': 2564, 'Tskhinvali': 217},
	'Taipei': {'Beijing': 1760, 'Seoul': 1123, 'Tokyo': 2300, 'Manila': 1094, 'Hanoi': 1400},
	'Tallinn': {'Riga': 279, 'Helsinki': 81, 'Stockholm': 380, 'Minsk': 600, 'Moscow': 870},
	'Tashkent': {'Astana': 1300, 'Bishkek': 520, 'Dushanbe': 430, 'Ashgabat': 1108, 'Moscow': 3300, 'Beijing': 4400},
	'Tbilisi': {'Baku': 379, 'Ankara': 1760, 'Yerevan': 170, 'Moscow': 1647, 'Sukhumi': 370},
	'Tegucigalpa': {'Guatemala City': 342, 'San Salvador': 422, 'Managua': 314, 'Belmopan': 483, 'San Jose': 1063},
	'Tehran': {'Ankara': 2660, 'Baghdad': 981, 'Ashgabat': 1156, 'Baku': 679, 'Yerevan': 2077, 'Kabul': 4337, 'Islamabad': 2406, 'Abu Dhabi': 1227},
	'Thimphu': {'Kathmandu': 427, 'Dhaka': 423, 'Beijing': 2500, 'New Delhi': 1285},
	'Tirana': {'Podgorica': 153, 'Skopje': 319, 'Belgrade': 398, 'Sofia': 339, 'Athens': 501, 'Pristina': 81, 'Rome': 612, 'Sarajevo': 449},
	'Tokyo': {'Taipei': 2300, 'Beijing': 2106, 'Moscow': 7484, 'Seoul': 1158, 'Pyongyang': 1353, 'Manila': 2985, 'Hanoi': 3790, 'Ottawa': 10410, 'Ankara': 8740, 'Dhaka': 4370, 'Ulaanbaatar': 3012},
	'Tripoli': {'Algiers': 1008, 'Cairo': 1670, 'Tunis': 1363, 'Valletta': 360},
	'Tskhinvali': {'Apia': 1663, 'Canberra': 8945, 'Wellington': 5506, 'Nukuʻalofa': 2931, 'Suva': 217},
	'Tunis': {'Algiers': 257, 'Tripoli': 1363, 'Rome': 1332, 'Valletta': 400},
	'Ulaanbaatar': {'Beijing': 1219, 'Moscow': 4636, 'Seoul': 1992, 'Tokyo': 3012},
	'Vaduz': {'Berlin': 770, 'Bern': 157, 'Vienna': 525, 'Rome': 784, 'Vatican City': 785},
	'Valletta': {'Rome': 690, 'Tunis': 400, 'Abu Dhabi': 4006, 'Athens': 1034, 'Nicosia': 512, 'Tripoli': 360},
	'Vatican City': {'Rome': 281, 'San Marino': 366, 'Vaduz': 785, 'Bern': 861, 'Monaco': 982, 'Paris': 1084, 'Ljubljana': 1120, 'Vienna': 1139},
	'Victoria': {'Rome': 17331, 'Brussels': 5529, 'Bern': 9789, 'Berlin': 10892, 'Luxembourg': 7094, 'Vienna': 13810, 'Antananarivo': 1388, 'Port Louis': 1200},
	'Vienna': {'Bratislava': 55, 'Budapest': 243, 'Prague': 300, 'Berlin': 523, 'Bern': 810, 'Ljubljana': 276, 'Rome': 833, 'Vaduz': 525, 'Vatican City': 1139, 'Victoria': 13810},
	'Vientiane': {'Beijing': 1773, 'Hanoi': 421, 'Bangkok': 570, 'Phnom Penh': 786, 'Naypyidaw': 375},
	'Vilnius': {'Riga': 267, 'Minsk': 160, 'Warsaw': 340, 'Berlin': 818, 'Stockholm': 615, 'Moscow': 791},
	'Warsaw': {'Berlin': 516, 'Prague': 500, 'Bratislava': 532, 'Vilnius': 340, 'Kiev': 590, 'Minsk': 490, 'Moscow': 1200, 'Amsterdam': 1140, 'Riga': 561},
	'Washington, D.C.': {'Ottawa': 725, 'Mexico City': 2510, 'Havana': 1753, 'Kingston': 2189, 'Santo Domingo': 2335, 'San Juan': 2447, 'Nassau': 1732},
	'Wellington': {'Canberra': 2143, 'Suva': 2850, 'Tskhinvali': 5506},
	'Windhoek': {'Luanda': 1120, 'Gaborone': 1186, 'Pretoria, Cape Town, Bloemfontein': 1300},
	'Yamoussoukro': {'Accra': 202, 'Bamako': 949, 'Conakry': 1100, 'Monrovia': 850, 'Ouagadougou': 500},
	'Yaounde': {'Abuja': 1106, 'NʻDjamena': 900, 'Bangui': 924, 'Brazzaville': 277, 'Libreville': 547, 'Malabo': 150},
	'Yaren': {'Honiara': 2349, 'Majuro': 700},
	'Yerevan': {'Ankara': 993, 'Tbilisi': 170, 'Baku': 395, 'Tehran': 2077},
	'Zagreb': {'Ljubljana': 140, 'Budapest': 349, 'Belgrade': 367, 'Sarajevo': 392, 'Podgorica': 455, 'Rome': 516},
	'Bujumbura': {'Kigali': 55, 'Kampala': 456, 'Dodoma': 1017, 'Brazzaville': 1225},
	'Belfast': {'Dublin': 168, 'London': 523},
	'Edinburgh': {'Reykjavik': 1645, 'London': 539, 'Dublin': 512, 'Oslo': 1045, 'Copenhagen': 870, 'Brussels': 740, 'Paris': 874, 'Luxembourg': 785, 'Berlin': 1092},
	'San Juan': {'Santo Domingo': 254, 'Port-au-Prince': 2630, 'Washington, D.C.': 2447, 'Bridgetown': 3110, 'Castries': 496},
}
```

```python
for i in list(city.keys()):
    for j in list(city[i].keys()):
        if j not in list(city.keys()):
            city[j] = {}
            city[j][i] = city[i][j]
        else:
            city[j][i] = city[i][j]

print("city =", "{")
for i in city:
    print("\t", "\'", i, "\'", ": ", city[i], ",", sep = "")
print("}")
# print(h)
```

```python
import heapq
def way(graph, start, end):
    queue = [(0, start,[])]
    visited = set()
    t = 0
    while queue:
        cost, node, path = heapq.heappop(queue)
        if node not in visited:
            visited.add(node)
            path = path + [node]
            if node == end:
                t = 1
                print("Расстояние: ", cost, "\n", "      Путь: ", sep = "", end = "")
                for point in path:
                    if path[-1] == point:
                        print(point)
                    else:
                        print(point, "-> ", end = "")
            for neighbour, weight in graph.get(node, {}).items():
                if neighbour not in visited:
                    heapq.heappush(queue,(cost + weight, neighbour, path))
    if t == 0:
        print("Не удалось найти путь до конечного города.")

# way(city, 'Moscow', 'Tokyo')
# way(city, 'Belfast', 'Bujumbura')
# way(city, 'Abu Dhabi', 'Zagreb')
# way(city, 'Brussels', 'Bangkok')
# way(city, 'Sofia', 'Tirana')
# way(city, 'Tokyo', 'Copenhagen')
# way(city, 'Paris', 'London')
# way(city, 'Rome', 'Madrid')
# way(city, 'Berlin', 'Prague')
# way(city, 'Helsinki', 'Budapest')
# way(city, 'Vilnius', 'Luxembourg')
# way(city, 'Riga', 'Amsterdam')
# way(city, 'Warsaw', 'Lisbon')
# way(city, 'Stockholm', 'Ljubljana')
# way(city, 'Oslo', 'Jerusalem')
# way(city, 'Athens', 'Mexico City')
# way(city, 'Buenos Aires', 'Dublin')
# way(city, 'Bern', 'Beijing')
# way(city, 'New Delhi', 'Ankara')
# way(city, 'Reykjavik', 'Libreville')
```

```python
print("Добро пожаловать!\nЕсли вы захотите закончить: введите Stop в любое из полей\n")
while True:
    first = input("Введите столицу, из которой хотите проложить маршрут: ")
    second = input("Введите столицу, в которую хотите попасть: ")
    if first == "stop" or second == "stop":
        break
    way(city, first, second)
                    
```

```python

```

```python

```

```python

```
