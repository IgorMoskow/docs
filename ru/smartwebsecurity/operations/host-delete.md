---
title: "Отключить профиль безопасности от виртуального хоста"
description: "Следуя данной инструкции, вы сможете отключить профиль безопасности от виртуального хоста."
---

# Отключить профиль безопасности от виртуального хоста

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором вы хотите отключить [профиль безопасности](../concepts/profiles.md) от [виртуального хоста](../../application-load-balancer/concepts/http-router.md#virtual-host) сервиса [{{ alb-full-name }}](../../application-load-balancer/).
  1. В списке сервисов выберите **{{ sws-name }}**.
  1. Напротив профиля, который вы хотите отключить от хоста, нажмите ![options](../../_assets/options.svg) и выберите ![pencil](../../_assets/pencil.svg) **Редактировать**.
  1. Перейдите на вкладку **Подключенные к профилю хосты**.
  1. Напротив хоста, от которого вы хотите отключить профиль, нажмите ![options](../../_assets/options.svg) и выберите ![disconnect](../../_assets/smartwebsecurity/disconnect.svg) **Отключить от профиля**.
  1. Подтвердите отключение.
  1. Нажмите кнопку **Сохранить**. 

{% endlist %}
