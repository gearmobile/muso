+++
authors = ["Moe Green"]
title = "Ubuntu KVM"
date = "2023-09-29"
description = "Ubuntu ошибка с kvm при выключении"
tags = [
    "ubuntu",
    "kvm",
    "shutdown"
]
categories = [
    "linux"
]
series = ["Theme Demo"]
+++

Ubuntu 22.04 - после установки столкнулся с проблемой при выключении системы с ошибкой `kvm: exiting hardware virtualization``.

## Kvm: exiting hardware virtualization <!--more-->

Итак, система Ubuntu 22.04 свежеустановленная, все обновления установлены. Но при выключении системы в логах возникает ошибка `kvm: exiting hardware virtualization`. Перепробовал разные советы и решения по этой теме в Сети, но эффективным оказалось следующее.

1. Открываем терминал

2. В терминале вводим следующую строку:
{{< highlight bash >}}
EDITOR=gedit sudoedit /etc/default/grub
{{< /highlight >}}

3. Откроются настройки GRUB в редакторе gedit - в файле находим строку:
{{< highlight text >}}
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi"
{{< /highlight >}}
... и меняем ее на строку:
{{< highlight text >}}
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
{{< /highlight >}}
... то есть, по факту - добавляем для ключа `acpi` значение `force`.

4. Сохраняем изменения в конфиг файле.

5. В терминале делаем пересборку загрузчика командой:
{{< highlight bash >}}
sudo update-grub
{{< /highlight >}}