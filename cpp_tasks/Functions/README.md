## Условие
Function<A, R, F> – "обёртка" вокруг функции (или объекта класса с перегруженной операцией "()") типа F, принимающей параметр
типа A и возвращающей значение типа R.

Операции, перегружаемые для Function<A, R, F>:

1. "( )" – вызов функции (принимает значение типа A и
возвращает значение типа R);
2. "∗" – композиция двух функций.

Конструктор класса Function<A, R, F> должен принимать параметр типа F.