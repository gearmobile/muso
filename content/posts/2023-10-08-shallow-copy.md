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

Spread-оператор делает _поверхностную_ копию (shallow copy).

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