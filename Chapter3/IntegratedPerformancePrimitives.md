## [П]|[РС]|(РП) IPP - Integrated Performance Primitives

У Intel-а есть продукт под названием Integrated Performance Primitives (IPP) library. Эта библиотека позволяет оптимизировать задачи обработки мультимедиа и другие операции процессора, тем самым повышая популярность использования процессоров от Intel. 

Как уже говорилось ранее, OpenCV поддерживает тесные отношения с IPP, как на программном уровне, так и на организационном уровне внутри компании. В результате, OpenCV автоматически распознает IPP и использует её для повышения производительности.

Имея такую библиотеку под рукой, можно выполнять широкий спектр задач. В большинстве далее обсуждаемых задачах будут использованы подпрограммы из библиотеки IPP. Не секрет, что обрабатывать большой объем данных выгоднее всего параллельно (MMX, SSE, SSE2 и т.д.).


### Проверка установки

Проверить и убедиться, что IPP установлена и работает правильно, позволяет функция *cvGetModuleInfo()* (пример 3-21). Эта функция проверит установленную версию OpenCV и версию дополнений.

Пример 3-21. Использование функции *cvGetModuleInfo()* для проверки

```cpp
char* libraries;
char* modules;
cvGetModuleInfo( 0, &libraries, &modules );
printf("Libraries: %s/nModules: %s/n", libraries, modules );
```

Код в примере 3-21 будет генерировать текстовые строки, описывающие установленные библиотеки и модули. Результат может быть следующим:

```
Libraries cxcore: 1.0.0
Modules: ippcv20.dll, ippi20.dll, ipps20.dll, ippvm20.dll
```

Перечисленные модули являются модулями IPP. Эти модули сами по себе являются фактически прокси для более низкоуровневых определений специфических библиотек. Детали реализации выходят за рамки данной книги.

