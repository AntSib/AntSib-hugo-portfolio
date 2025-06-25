+++
title = 'Чекинаторы'
date = '2025-06-06'
draft = false
+++

## Одностраничные приложения, выполненные для прохождения чекинаторов на учебных занятиях

Чекинатор 1
```html
<!DOCTYPE html>
<html>
 <head>
  <title>Сибилев Антон</title><meta charset="utf-8">
  <style>
    input {width:60px;}
  </style>
 </head>
 <body>
    <h4>1149817</h4>
    <input type="number" value = "" id="n1">
    <b>X+</b>
    <input type="number" value = "" id="n2">
    <b>Y=</b>
    <input type="number" value = "" id="n3">
    <br>
    <input type="number" value = "" id="n4">
    <b>X+</b>
    <input type="number" value = "" id="n5">
    <b>Y=</b>
    <input type="number" value = "" id="n6">
    <br>
    <button id="bt" onclick="calculate()">Рассчитать X и Y</button>
    <br>
    <b>X=</b>
    <input type="number" value = "" id="result1" style="width: 100px;">
    <br>
    <b>Y=</b>
    <input type="number" value = "" id="result2" style="width: 100px;">

    <script>
        function calculate() {
            const n1 = Number(document.querySelector('#n1').value);
            const n2 = Number(document.querySelector('#n2').value);
            const n3 = Number(document.querySelector('#n3').value);
            const n4 = Number(document.querySelector('#n4').value);
            const n5 = Number(document.querySelector('#n5').value);
            const n6 = Number(document.querySelector('#n6').value);

            let denomirator = n1 * n5 - n2 * n4;
            if (denomirator == 0) {
                alert("Denomirator = 0\nX and Y undefined!")
            } else {
                let x_numerator = n3 * n5 - n6 * n2;
                let y_numerator = n1 * n6 - n3 * n4;

                document.getElementById("result1").value = x_numerator/denomirator;
                document.getElementById("result2").value = y_numerator/denomirator;
            }
        }
    </script>
 </body>
</html>
```

Чекинатор 5 (sort)
```html
<!DOCTYPE html>
<html>
 <head>
  <title>Сибилев Антон</title><meta charset="utf-8">
 </head>
 <body>
    <h4>1149817</h4>

    <!-- (0044) Напишите адрес клиентского приложения, которое нативным JS обрабатывает адрес вида 
    https://abc.def/ghi?[55,33,44], т.е. в конце адреса находится вопросительный знак и за ним массив. 
    Приложение должно отсортировать этот массив как последовательность чисел и вывести результат
    в заголовок окна (toString). В заголовке h4 должен быть ваш логин в этой системе. 
    Пожалуйста напишите адрес до знака вопроса (например https://kodaktor.ru/g/0946c74) и 
    не используйте в коде console -->
    
 </body>
  <script>
	 document.title = "https://abc.def/ghi?[55,33,44]";

    let my_string = window.location.search.substring(2).split(',');
    let new_string = [];

    for (num of my_string) {
      new_string.push(parseInt(num));
    }

    my_string = new_string.sort().toString();
    document.title = my_string;
  </script>
</html>
```


Чекинатор Корреляция
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Сибилев Антон</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>

      <!-- (0051) Напишите адрес клиентского приложения, которое нативным образом обрабатывает адрес вида 
      https://abc.def/?A=55,33,44&B=21,32,43 где через запятую передаются два ряда целых чисел в качестве значений параметров A и B) 
      и отдаёт значение коэффициента корреляции Пирсона для этих двух рядов данных. 
      Приложение должно вычислить ответ вида 0.xxx (три знака после точки без округления, простое отсечение остальных цифр) 
      либо 1 (модуль, без знака) и поместить результат в заголовок окна. 
      В заголовке h4 должен быть ваш логин в этой системе. Пожалуйста напишите адрес до знака вопроса 
      (например https://kodaktor.ru/g/0946c74) и не используйте в коде console -->

  </main>
 </body>
 <script>
  	document.title = "https://abc.def/?A=55,33,44&B=21,32,43";

    let my_string = window.location.search.substring(1).split('&');
    let array_x = [];
    let array_y = [];

    for (let i = 0; i < my_string.length; i++) {
      my_string[i] = my_string[i].substring(2).split(',');
    }

    for (let i = 0; i < my_string[0].length; i++) {
      array_x[i] = parseInt(my_string[0][i]);
      array_y[i] = parseInt(my_string[1][i]);
    }

      // console.log("array_x: ", array_x);
      // console.log("array_y: ", array_y);

    let sum_x = array_x.reduce((a, b) => a + b, 0);
    let sum_y = array_y.reduce((a, b) => a + b, 0);
    
    let avg_x = (sum_x / array_x.length) || 0;
    let avg_y = (sum_y / array_y.length) || 0;
    
    let xy_dev = 0;
    let x_dev_sqrd = 0;
    let y_dev_sqrd = 0;

    for (let i = 0; i < array_x.length; i++) {
      xy_dev += (array_x[i] - avg_x) * (array_y[i] - avg_y);
      x_dev_sqrd += (array_x[i] - avg_x) * (array_x[i] - avg_x);
      y_dev_sqrd += (array_y[i] - avg_y) * (array_y[i] - avg_y);
    }

      // console.log("xy_dev: ", xy_dev);
      // console.log("x_dev_sqrd: ", x_dev_sqrd);
      // console.log("y_dev_sqrd: ", y_dev_sqrd);

    let pirson = Math.abs(xy_dev / (Math.sqrt(x_dev_sqrd * y_dev_sqrd)));

    if (pirson == parseInt(pirson)) {
      pirson = parseInt(pirson).toString();
    } else {
      pirson = pirson.toString().split('.')[0] + '.' + pirson.toString().split('.')[1].slice(0, 3);
    }

    // console.log("pirson: ", pirson);
    // console.log(typeof pirson);

    document.title = pirson;
 </script>
</html>
```

Чекинатор OptimusPrime
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0030) Напишите адрес клиентского приложения, которое нативным JS обрабатывает 
      адрес вида https://abc.def/ghi?123456, т.е. в конце адреса находится вопросительный знак 
      и за ним число. Приложение должно вычислить, сколько простых чисел располагается между числом 2 
      и этим числом N включительно т.е. [2, N] и вывести результат в заголовок окна.
      В заголовке h4 должен быть ваш логин в этой системе. 
      Пожалуйста напишите адрес до знака вопроса (например https://kodaktor.ru/g/0946c74) и не 
      используйте в коде console
    </p>-->
  </main>
 </body>
 <script>
  let search_num = parseInt(window.location.search.substring(1));
  
  let prime_nums = [2];
  let flag = true;

  for (let n = 2; n <= search_num; n++) {
    flag = true;
    prime_nums.forEach(element => {
      if (n % element === 0) {
        flag = false;
        return;
      }
    });
    if (flag) {
      prime_nums.push(n);
    }
  }

  document.title = prime_nums.length;
 </script>
</html>
```

Чекинатор typeof
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0042) Напишите код функции task(x), возвращающей результат работы функции, 
      переданной ей в качестве аргумента x и ваш логин в системе Moodle если типом x не является функция, 
      при этом не используйте инструкцию if..else
    </p>-->
  </main>
 </body>
 <script>
  function task(x) { return typeof(x) === 'function' ? x() : '1149817'; }
 </script>
</html>
```

Чекинатор promise
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0021) Предоставьте код функции task от одного аргумента x, которая возвращает промис, 
      отвергающий с причиной 'no' если x >= 18, разрешённый в значение yes, если x < 18, либо в значение, 
      равное вашему логину в систему, если x == 0.
    </p>-->
  </main>
 </body>
 <script>
  function task(x) {
    return new Promise((resolve, reject) => {
      if (x == 0) {
        resolve(1149817); // Число, Карл, число! Когда всё время до этого это была строка. Серьёзно?
      } else if (x >= 18) {
        reject('no');
      } else if (x < 18) {
        resolve('yes');
      }
    });
  }
 </script>
</html>
```

Чекинатор async promise
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0023) Предоставьте код async-функции task от одного аргумента x, которая возвращает в виде установленного промиса 
      (строчное) значение свойства name переданного ей объекта (это значение само является установленным промисом), 
      сконкатенированное с вашим логином в этой системе.
    </p>-->
  </main>
 </body>
 <script>
  async function task(x) { 
    const name = await x.name;
    return `${name}1149817`;
   }
 </script>
</html>
```

Чекинатор constructor (key 1)
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0026)В последнем-нижнем поле напишите код функции task(name, familyname, login), 
      которая в качестве конструктора создаёт объект с тремя собственными полями – name, 
      familyname и login. По умолчанию значение поля login – строковое значение, равное вашему 
      логину в системе. Кроме того, в прототипе должен быть метод getFullName, который возвращает 
      результат конкатенации name, familyname и восклицательного знака. 
    </p>-->
  </main>
 </body>
 <script>
  function task(name, familyname, login) {
    this.name = name;
    this.familyname = familyname;
    this.login = '1149817';
    
    task.prototype.getFullName = function() {
      return this.name + this.familyname + "!";
    }
  }

  let Me = new task("Ant", "Sib");

  console.log(Me);
  console.log(Me.getFullName());
 </script>
</html>
```

Чекинатор DOM
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <button id="bt" onclick="create_article()">Выполнить задание</button>
  </main>
 </body>
  <script>
      function create_article() {
        let article = document.createElement('article');
        document.body.appendChild(article);

        for (let i = 0; i < 1000; i++) {
          let newDiv = document.createElement('div');
          newDiv.id = `i${i}`;
          article.appendChild(newDiv);
        }
      }
  </script>
</html>
```

Чекинатор enumerable and non-enumerable (key 2)
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0025)В последнем-нижнем поле напишите код функции task(x), возвращающей объект: 
      у объекта должно быть собственное перечислимое свойство login со строковым значением, 
      равным вашему логину в системе. И ещё 3 свойства key1 – несобственное неперечислимое, 
      key2 – несобственное перечислимое, key3 – собственное неперечислимое. 
      Их значениями должны быть числа от 2022 до 2024 соответственно. 
      Не используйте __proto__ и console.log в своём ответе
    </p>-->
  </main>
 </body>
 <script>
  function task(x) {
    let proto = {};

    Object.defineProperty(proto, 'key1', { value: 2022, enumerable: false });
    Object.defineProperty(proto, 'key2', { value: 2023, enumerable: true });

    const obj = Object.create(proto);
    
    obj.login = '1149817';
  
    Object.defineProperty(obj, 'key3', { value: 2024, enumerable: false });

    return obj;
  }

  let new_obj = task();

  console.log(new_obj);
 </script>
</html>
```

Чекинатор form with fetch
```html
<!DOCTYPE html>
<html>
<head>
  <title>Простая форма</title>
  <meta charset="utf-8">
</head>
<body>
  <form id="customForm">
    <input id="nameInput" name="name" placeholder="Введите имя" />
    <button type="submit">Отправить</button>
  </form>
  <iframe id="responseFrame" name="i" width="500" height="50"></iframe>
  
  <script>
    document.getElementById('customForm')
    .addEventListener('submit', async function(event) {
      event.preventDefault();

      const nameValue = document.getElementById('nameInput').value;
      const responseFrame = document.getElementById('responseFrame');

      try {
        const response = await fetch('/api/body', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({ name: nameValue })
        });

        const result = await response.text();
        
        responseFrame.contentDocument.textContent(result);
        
      } catch (error) {
        console.log('Ошибка при отправке запроса:', error);
        responseFrame.contentDocument.textContent(`Error encountered: ${error.message}`);
      }
    });
  </script>
</body>
</html>
```

Чекинатор jsk(1)
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0028) Напишите функцию task, объявленную с помощью слова function, 
      которая возвращает только одно: JSX-фрагмент (без имени тега) с единственным текстовым 
      потомком, равным вашему логину в этой системе
    </p>-->
  </main>
 </body>
 <script>
  function task() {
    return <>1149817</>;
  }
 </script>
</html>
```

Чекинатор jsk(2)
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0029) Напишите код функции task(x) которая возвращает только одно: 
      JSX-элемент содержащий в качестве единственного контента JSX-выражение, 
      состоящее из x и вашего логина в этой системе, соединённых оператором + 
    </p>-->
  </main>
 </body>
 <script>
  function task(x) {
    return <div>{x + '1149817'}</div>;
  }
 </script>
</html>
```

Чекинатор json read
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      Практическое задание от 05-12-2024
      Дан адрес для получения информации: https://kodaktor.ru/j/numbers, 
      сервер отдаёт в JSON-формате несколько чисел, их нужно их прочитать и просуммировать
      вторым шагом нужно обратиться к адресу для отправки информации

      https://docs.google.com/forms/u/0/d/e/1FAIpQLSeZyDJ_68Mj7io5vtjyNqul7ceNE1t5Z5KkkN7foqxbIcUsbg/formResponse

      имя параметра, которое указывается в body: entry.364005965
      и вот нужно написать код который обращается к первому адресу, 
      прочитывает и суммирует числа и далее записывает результат суммирования и в скобках 
      вашу фамилию (латинскими буквами) отправляя получившееся значение в виде одной строки методом POST 
      в указанную форму
    </p>-->
  </main>
 </body>
 <script>
   async function fetchAndSend() {
    try {
        const response = await fetch('https://kodaktor.ru/j/numbers');

        if (!response.ok) {
            throw new Error(`Errorgettingdata: ${response.statusText}`);
        }

        const data = await response.json();
        
        let sum = 0;

        for (i = 0; i < data.numbers.length; i++) {
          	sum += data.numbers[i].value;
        }

		const result = `${sum} (Sibilev)`;

		const formResponse = await fetch('https://docs.google.com/forms/u/0/d/e/1FAIpQLSeZyDJ_68Mj7io5vtjyNqul7ceNE1t5Z5KkkN7foqxbIcUsbg/formResponse', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/x-www-form-urlencoded',
            },
            body: new URLSearchParams({ 'entry.364005965': result })
        });

        if (!formResponse.ok) {
            throw new Error(`Error encountered: ${formResponse.statusText}`);
        }

        console.log('Succses', result);
    } catch (error) {
        console.error('Error:', error);
    }
}
fetchAndSend()

 </script>
</html>
```
Чекинатор prototype
```html
<!DOCTYPE html>
<html lang="ru">
 <head>
  <title>Страница HTML5</title><meta charset="utf-8">
 </head>
 <body>
  <main>
    <h4>1149817</h4>
    <!--<p>
      (0027) Напишите функцию task, принимающую объект. У этого объекта есть цепочка прототипов.
      Т.е. у него самого есть прототип, у этого прототипа есть прототип и так далее до шага, 
      на котором очередным прототипом оказывается null. Функция должна возвращать число ненулевых 
      прототипов. При передаче ей значения null она должна возвращать ваш логин в системе. 
      Функция должна быть одна - task. Не используйте console.log
    </p>-->
  </main>
 </body>
 <script>
  function task(obj) {
    if (obj == null) {
      return '1149817';
    }

    let counter = 0;
    
    while (Object.getPrototypeOf(obj) != null) {
      console.log(Object.getPrototypeOf(obj));
      obj = Object.getPrototypeOf(obj);
      counter ++;
    }
    return counter;
   }
 </script>
</html>
```
