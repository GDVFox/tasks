## Условие
Составьте на языке C++ набор функций для статистической обработки текстовых данных. Прототипы функций объявлены в заголовочном файле textstats.hpp. Реализации функций должны располагаться в отдельном файле textstats.cpp.

Функция get_tokens разбивает текст, закодированный в ASCII, на слова с переводом всех букв к нижнему регистру. Слово – это последовательность символов, не являющихся разделителями.

```c++
void get_tokens(
    // [ВХОД] Текстовая строка.
    const string &s,
    // [ВХОД] Множество символов-разделителей.
    const unordered_set<char> &delimiters,
    // [ВЫХОД] Последовательность слов.
    vector<string> &tokens
);
```

Функция get_type_freq составляет частотный словарь текста, в котором для каждого слова указано количество его вхождений в текст.

```c++
void get_type_freq(
    // [ВХОД] Последовательность слов.
    const vector<string> &tokens, 
    // [ВЫХОД] Частотный словарь
    // (ключи -- слова, значения -- количества вхождений).
    map<string, int> &freqdi
);
```

Функция get_types составляет список уникальных слов, встречающихся в тексте. Список должен быть отсортирован лексикографически.

```c++
void get_types(
    // [ВХОД] Последовательность слов.
    const vector<string> &tokens, 
    // [ВЫХОД] Список уникальных слов.
    vector<string> &wtypes
);
```

Функция get_x_length_words формирует из списка уникальных слов новый список, в который попадают только те слова, длина которых не меньше x символов.

```c++
void get_x_length_words(
    // [ВХОД] Список уникальных слов.
    const vector<string> &wtypes, 
    // [ВХОД] Минимальная длина слова.
    int x, 
    // [ВЫХОД] Список слов, длина которых не меньше x.
    vector<string> &words
);
```

Функция get_x_freq_words формирует лексикографически отсортированный список слов, взятых из частотного словаря, которые встречаются в тексте не меньше x раз.

```c++
void get_x_freq_words(
    // [ВХОД] Частотный словарь
    const map<string, int> &freqdi, 
    // [ВХОД] Минимальное количество вхождений.
    int x,
    // [ВЫХОД] Список слов, встречающихся не меньше x раз.
    vector<string> &words
);
```

Функция get_words_by_length_dict составляет словарь, в котором каждый ключ – это длина слова, а значение – это список слов заданной длины.

```c++
void get_words_by_length_dict(
    // [ВХОД] Список уникальных слов.
    const vector<string> &wtypes, 
    // [ВЫХОД] Словарь распределения слов по длинам.
    map<int, vector<string> > &lengthdi
);
```

Проверка работоспособности реализованных функций будет осуществляться с помощью тестовой программы, выполняющей статистическую обработку текста, считываемого со стандартного потока ввода. Исходный текст тестовой программы располагается в файле test.cpp.