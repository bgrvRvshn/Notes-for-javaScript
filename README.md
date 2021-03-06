# :blue_book: Понятия и термины
###### Асинхронность в JavaScript
  Синхронность - (син греч. chronos – время) – 1. согласованность движений. Скажем у нас есть 2 строчки кода. Первая идет за второй. Синхронность означает, что строка 2 не может запуститься до тех пор, пока строка 1 не закончит своё выполнение. JavaScript сам по себе однопоточный, что означает то, что только одby блок кода может запускаться за раз. Так как движок JS выполняет наш код, обрабатывая строку за строкой, он использует один стек вызовов, чтобы продолжать отслеживать код, который выполняется в соответствии с установленным порядком.  
  В отличие от синхронности, асинхронность это модель поведения. Допустим, у нам есть 2 строчки кода, первая за второй. Первая строка это код которому нужно время. Итак, первая строка начинает запуск в фоновом режиме, позволяя второй строке запуск в фоновом режиме, позволяя второй запуститься без ожидания завершения первой строки.  
  Нам нужно такое поведение, когда что-то подтормаживает и требует времени. **Синхронность** может показаться прямолинейной и незатейливой, но всё же может быть и еще и медленной. Такие задачи, как обработка изображений, операции с файлами, создание запросов сети и ожидание ответа - всё это может тормозить и быть долгим. Так что такие вещи в стеке запросов превращаются в "задержку". Когда стек запросов заблокирован, браузер препятствует вмешательству пользователя и выполнению другого кода до тех пор, пока "задержка" не выполниться и не освободит стек запросов.
###### Promise (ES6)
  Вкратце про промисы: “Представьте, что вы ребенок. Ваша мама обещает вам, что вы получите новый телефон на следующей неделе.”
  Это объект, который представляет собой асинхронный таск, который должен завершиться.  
  Есть 3 состояния:
  1. Промис в состоянии ожидания (`pending`). Когда вы не знаете, получите ли телефон.
  2. Промис решен (`resolved`). Вам реально купят новый телефон.
  3. Промис отклонен (`rejected`). Вы не получите новый телефон.  
  В самом экземпляре промиса есть два основных метода:
  - `then` - запускает колбек, который передали, когда промис завершен.
  - `catch` - запускает колбек, который передали, когда что-то идет не так, что вызывает `reject` вместо `resolve`.
###### Async/await (ES7)
  Это функции, которые возвращают промисы.
  1. Всегда, когда нужно возвратить промис в функцию, нужно ставить спереди `async` к этой функции.
  2. Когда нужно вызвать промис, надо поставить `await`.
  3. Использовать `try { ... }` `catch(error) { ... }`, чтобы словить ошибку промиса.  
  Ваш код может встать на паузу в ожидании функции с `await`. `Await` возвращает то, что асинхронная функция отдает при завершении. `Await` м.б. использован только внутри `async` функции.  
  Если асинхнронная функция выдает исключение, то оно поднимается к родительской функции, как в обычном JS и может быть перехвачено с `try/catch`.
###### The Single Responsibility Principle, SRP
  Принцип единственно ответственности - это принцип ООП означающий, что каждый объект должен иметь одну ответсвенность и причину существования.
###### Чистая функция
- Каждый раз возвращает одинаковый результат, когда она вызывается с тем же набором аргументов.  
- Не имеет побочных эффектов. Побочные эффекты включают: меняющийся вход, HTTP-вызовы, запись на диск, вывод на экран.  
- Можно безопасно клонировать, а затем менять входные параметры, оставив оригинал без изменений.
###### Callback
  Колбэк-функция или функция обратного вызова предназначена для отложенного выполнения.
```jsx
let addUser = () => { // logic here }

<button onClick={ addUser }>Add user</button>
```
В данном примере функция была передана в качестве параметра в тег `button` и будет вызвана при событии `onClick` на кнопке. Фукнция передается туда без скобок `()`, то есть не вызывается сразу.
###### FLUX
  Это архитектурный подход или набор шаблонов программирования для организации однонаправленного потока данных в приложении. Одна из наиболее популярных реализаций flux-архитектуры - `Redux`.
###### Замыкание
  Фукнция в теле которой присутствуют ссылки на переменные, объявленные вне тела этой функции в окружающем коде и не являющиеся её параметрами. По сути это способность функции к поиску переменных в глобальной области видимости, если используемые в ней переменные не объявлены внутри тела функции и не передаются в качестве параметров.  
  Также возможны случаи, когда функции вложены в друг друга, и внутренняя функция использует параметры поступающие в оборачивающей функции.
###### Observer
  Это поведенческий паттерн проектирования, который создаёт механизм подписки, позволяющий одним объектам следить и реагировать на события, происходящие в других объектах.  
  Паттерн "Наблюдатель" - определяет отношение "один ко многим" между объектами таким образом, что при изменении состояния одного объекта (**субъекта**) все зависящие от него объекты(**наблюдатели**) получают уведомление об этом и также обновляют своё состояние. Это нужно для согласования состояния взаимосвязанных объектов без их жесткой связанности (циклической зависимости). Данный паттерн реализован при добавлении слушателя событий в js `addEventListener` или `onClick, onChange` и т.д.
###### Инкапсуляция
  Это объединение данных и функций, которые с этими данными работают, в рамках одной структуры (в объекте), внутреннее состояние которой скрыто от прямого внешнего обращения (*сокрытие деталей*). Функции в таких объектах называются методами.
###### This (Контекст)
  В javascript методами называют функции, записанные в свойства объектов. Фактически метод - это роль, которую выполняет функция будучи привязанной к объекту. В JS функции это объекты *первого рода*, то есть они ведут себя как данные: их можно записывать в переменные или константы. Свойства объектов подобны переменным, а значит в них можно сохранить функции.  
  Для доступа к данным объекта внутри метода используется ключевое слово `this`. Внутри методов оно ссылается на текущий объект, к которому привязан метод. Правда так `this` работает только для обычных функций. У стрелочных другой принцип.
###### Bind
  Метод привязывает контекст к функции. В качестве первого параметра следует передавать контекст, а последующими параметрами - параметры функции. Метод возвращает новую функцию, внутри которой `this` будет равным переданному контексту.
```js
функция.bind(контекст, параметр1, параметр2...);
```
  Не обязательно записывать результат работы `bind` в новую функцию, можно просто перезаписать.
###### Детерминированность
  Детерминированный алгоритм — алгоритмический процесс, который выдаёт **уникальный** и **предопределённый** результат для заданных входных данных.
  Детерминированность в программировании означает что функция всегда возвращает одинаквое значение при определенном вводе аргументов. Она же:
> Идемпотентность — свойство объекта или операции при повторном применении операции к объекту давать тот же результат, что и при первом.
###### Query параметры
  Это часть `get` запроса идущая после вопросительного знака `?`. Имеют синтаксис, `название параметра = значение параметра`. Несколько `query` параметров разделяются знаком амперсанда `&`. Пример: `https://www.youtube.com/watch?name=Dmitry&age=33`
