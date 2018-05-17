## Условие
Назовём биграммой слова его подстроку длиной в две буквы. Например, в слове mother имются пять биграмм:
```
mo ot th he er
```
При этом будем считать, что в однобуквенном слове ровно одна биграмма, совпадающая с самим этим словом.

Пусть даны два слова A и B. Множество биграмм в слове A обозначим как α, а множество биграмм в слове B – как β. Определим меру схожести этих слов как отношение количества биграмм в пересечении множеств α и β к количеству биграмм в объединении этих множеств.

Например, рассмотрим слова receive и recieve. Множества биграмм для них выглядят как
```
re ec ce ei iv ve
re ec ci ie ev ve
```
Пересечение этих множеств даёт три биграммы:
```
re ec ve
```
Их объединение содержит девять биграмм:
```
re ec ce ci ei ie iv ev ve
```
Тем самым, мера схожести этих двух слов равна 1/3.

Составьте на языке C++ программу spellchecker.cpp, осуществляющую исправление орфографических ошибок в английских словах на основе определённой выше меры схожести. Программа должна считывать из стандартного потока ввода набор слов, разделённых переводами строки, и выводить в стандартный поток вывода правильный вариант написания каждого слова.

Перед исправлением ошибок программа должна загрузить из файла count_big.txt частотный словарь английского языка. В этом словаре приведены правильные написания английских слов, и для каждого слова указана его частота.

Для исправления слова программа должна найти в словаре наиболее похожее слово. Если несколько слов из словаря одинаково похожи на исправляемое слово, выбирается то из них, частота которого выше. Если и это не позволяет разрешить противоречие, то выбирается слово, лексикографически меньшее других кандидатов.