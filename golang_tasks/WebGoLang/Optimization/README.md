## Условие

-------------------------

Есть функиця, которая что-то там ищет по файлу. Но делает она это не очень быстро. Надо её оптимизировать.

Задание на работу с профайлером pprof.

Цель задания - научиться работать с pprof, находить горячие места в коде, уметь строить профиль потребления cpu и памяти, оптимизировать код с учетом этой информации. Написание самого быстрого решения не является целью задания.

Для генерации графа вам понадобится graphviz. Для пользователей windows не забудьте добавить его в PATH чтобы была доступна команда dot.

Рекомендую внимательно прочитать доп. материалы на русском - там ещё много примеров оптимизации и объяснений как работать с профайлером. Фактически там есть вся информация для выполнения этого задания.

Есть с десяток мест где можно оптимизировать.

Для выполнения задания необходимо чтобы два из параметров ( ns/op, B/op, allocs/op ) был быстрее чем в *BenchmarkSolution* ( у вас его нет в коде, не путайте с BencmarkSlow ).

Так же требуется написать отчет, где правили, почему правили и предсотавить скрины из профайлера (можно из консольного pprof, можно из графа) с выделенным местом, куда смотреть. Желательно попунктно - "1. оптмизачия ХХХ. нашлась в YYY (тест, скрин)."

*Без отчета с объяснениями ДЗ не принимается!*

По памяти ( B/op ) и количеству аллокаций ( allocs/op ) можно ориентироваться ровно на результаты *BenchmarkSolution* ниже, по времени ( ns/op ) - нет, зависит от системы.

Результат в fast.go в функцию FastSearch (изначально там то же самое что в SlowSearch).

Пример результатов с которыми будет сравниваться:
```
$ go test -bench . -benchmem

goos: windows

goarch: amd64

BenchmarkSlow-8 10 142703250 ns/op 336887900 B/op 284175 allocs/op

BenchmarkSolution-8 500 2782432 ns/op 559910 B/op 10422 allocs/op

PASS

ok optimization 3.897s
```

Запуск:

* `go test -v` - чтобы проверить что ничего не сломалось
* `go test -bench . -benchmem` - для просмотра производительности

Примечание:

* easyjson основан на рефлекции и не может работать с пакетом main. Для генерации кода вам необходимо вынести вашу структуру в отдельный пакет, сгенерить там код, потом забрать его в main