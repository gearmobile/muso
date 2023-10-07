+++
authors = ["Muso Verda"]
title = "Shallow and Deep Copy"
date = "2023-10-08"
description = "Shallow and Deep Copy"
tags = [
    "javascript",
    "собес",
]
categories = [
    "development"
]
+++

Спред-оператор делает поверхностную копию, поэтому ссылка на исходный объект изменяется. Это позволяет менять примитивы без мутации исходного объекта. Однако стоит помнить о ссылочных типах, подробнее о них можно почитать в Доке.

{{< highlight javascript >}}
const a = { firstname: 'Алексей', address: { city: 'Самара' } };
const b = a;
const c = {...a}

b.firstname = 'Николай';
c.firstname = 'Михаил';

b.address.city = 'Ульяновск';
c.address.city = 'Краснодар';

console.log(a.firstname, a.address.city);
{{< /highlight >}}