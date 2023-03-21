---
title: "{{ mch-name }}. Ответы на вопросы"
description: "Что такое {{ mch-name }}? Для каких задач стоит использовать {{ mch-name }}, а для каких — виртуальные машины с базами данных? Какую часть работы по управлению и сопровождению баз данных берет на себя {{ mch-name }}? Ответы на эти и другие вопросы в данной статье."
---

# Общие вопросы про {{ mch-name }}

#### Что такое {{ mch-short-name }}? {#what-is}

{{ mch-short-name }} — это сервис, который помогает вам создавать, эксплуатировать и масштабировать базы данных {{ CH }} в облачной инфраструктуре.

С {{ mch-short-name }} вы можете:
- создавать базы данных с необходимыми параметрами производительности;
- масштабировать вычислительные мощности и выделенный объем хранилища для баз данных по мере необходимости;
- получать журналы работы баз данных.

{{ mch-short-name }} берет на себя трудоемкие задачи администрирования инфраструктуры {{ CH }}:
- предоставляет мониторинг потребляемых ресурсов;
- автоматически создает резервные копии баз данных;
- обеспечивает отказоустойчивость за счет автоматического переключения на резервные реплики;
- своевременно обновляет программное обеспечение СУБД.

Вы взаимодействуете с кластером БД в {{ mch-short-name }} как с обычной базой данных в вашей локальной инфраструктуре. Благодаря этому вы можете управлять внутренними настройками БД в соответствии с требованиями вашего приложения.

#### Для чего используется {{ CH }}? Какую СУБД мне выбрать? {#why-ch}

{{ CH }} предназначен прежде всего для [аналитики](../../glossary/data-analytics.md) (OLAP) и поддерживает только добавление и чтение данных. Обновление данных возможно, но с [рядом оговорок](https://stackoverflow.com/questions/37901642/updating-data-in-clickhouse). Для других целей, скорее всего, удобнее использовать другие СУБД.

#### Какую часть работы по управлению и сопровождению баз данных берет на себя {{ mch-short-name }}? {#services}

При создании кластеров {{ mch-short-name }} выделяет ресурсы, устанавливает СУБД и создает базы данных.

Для созданных и запущенных баз данных {{ mch-short-name }} автоматически создает резервные копии, а также устанавливает исправления и обновления СУБД.

Также {{ mch-short-name }} обеспечивает репликацию данных между хостами БД (как внутри, так и между зонами доступности) и автоматически переключает нагрузку на резервную реплику в случае аварии.

#### Для каких задач стоит использовать {{ mch-short-name }}, а для каких — виртуальные машины с базами данных? {#mdb-advantage}

{{ yandex-cloud }} предлагает два варианта работы с базами данных:

- {{ mch-short-name }} позволяет вам эксплуатировать шаблонные базы данных, не заботясь об администрировании.
- Виртуальные машины {{ compute-full-name }} позволяют вам создавать и настраивать собственные базы данных. Такой подход позволяет использовать любые СУБД, подключаться к базам данных по [SSH](../../glossary/ssh-keygen.md) и так далее.

#### Что такое хост базы данных и кластер базы данных? {#what-is-cluster}

_Хост БД_ — это изолированная среда базы данных в облачной инфраструктуре с выделенными вычислительными ресурсами и зарезервированным объемом хранилища данных.

_Кластер БД_ — это один или более хостов БД, между которыми можно настроить репликацию.

#### Как начать работу с {{ mch-short-name }}? {#quickstart}

{{ mch-short-name }} доступен всем зарегистрированным пользователям {{ yandex-cloud }}.

Чтобы создать кластер базы данных в {{ mch-short-name }}, необходимо определиться с его характеристиками:

- [Класс хостов](../../managed-clickhouse/concepts/instance-types.md) (характеристики производительности — процессоры, память и т. п.).
- Объем хранилища (резервируется в полном объеме при создании кластера).
- Сеть, к которой будет подключен ваш кластер.
- Количество хостов для кластера и зона доступности для каждого хоста вы можете выбрать зону доступности.

Подробные инструкции см. в разделе [{#T}](../../managed-clickhouse/quickstart.md).

#### Сколько хостов БД может содержать кластер? {#how-many-hosts}

Минимальное количество хостов зависит от типа используемого [хранилища](../../managed-clickhouse/concepts/storage.md):

- при использовании хранилища на нереплицируемых SSD-дисках — не менее 3;
- при использовании хранилища на локальных SSD-дисках — не менее 2;
- при использовании хранилища на сетевых HDD-дисках или на сетевых SSD-дисках допускается создание кластера из одного хоста.

Максимальное количество хостов в кластере ограничено только запрошенными вычислительными ресурсами и объемом хранилища для кластера.

Подробнее см. в разделе [{#T}](../../managed-clickhouse/concepts/limits.md).

#### Как получить доступ к запущенному хосту базы данных? {#db-access}

Вы можете подключаться к базам данных {{ mch-short-name }} способами, стандартными для СУБД.

[Подробнее о подключении к кластерам](../../managed-clickhouse/operations/connect.md).

#### Сколько кластеров можно создать в рамках одного облака? {#db-limit}

Технические и организационные ограничения MDB приведены в разделе [{#T}](../../managed-clickhouse/concepts/limits.md).

#### Как происходит обслуживание кластеров БД? {#service-window}

Под обслуживанием в {{ mch-short-name }} понимается:

- автоматическая установка обновлений и исправлений СУБД для хостов БД (в т. ч. для выключенных кластеров);
- изменение класса хостов и объема хранилища;
- другие сервисные работы {{ mch-short-name }}.

Подробнее см. в разделе [{#T}](../../managed-clickhouse/concepts/maintenance.md).

#### Как редактировать внешние словари? {#external-dict}

Чтобы переименовать словарь, выполните запрос:

```sql
RENAME DICTIONARY <имя_словаря> TO <новое_имя>
```

Для прочих изменений воспользуйтесь методом API [update](../../managed-clickhouse/api-ref/Cluster/update.md).

#### Какую версию {{ CH }} использует {{ mch-short-name }}? {#dbms-version}

{{ mch-short-name }} использует несколько последних стабильных версий {{ CH }}. Подробнее см. в разделе [{#T}](../../managed-clickhouse/concepts/update-policy.md).

#### Какую версию {{ CH }} выбрать? {#choose-version}

Рекомендуется выбирать последнюю доступную LTS-версию {{ CH }}. Подробнее см. в разделе [{#T}](../../managed-clickhouse/concepts/update-policy.md).

#### Что происходит, когда выпускается новая версия СУБД? {#new-version}

При выходе новых минорных версий программное обеспечение кластеров автоматически обновляется после короткого периода тестирования. 

Владельцы затронутых кластеров БД получают предварительное оповещение о сроках проведения работ и доступности баз данных. 

#### Что происходит, когда версия СУБД становится неподдерживаемой (deprecated)? {#dbms-deprecated}

Когда версия СУБД становится неподдерживаемой, {{ mch-short-name }} автоматически оповещает владельцев кластеров БД, созданных с этой версией, по электронной почте.

Создание новых хостов с СУБД неподдерживаемых версий становится невозможным. Кластеры с неподдерживаемой версией {{ CH }} обновляются в соответствии с [политикой работы с версиями](../../managed-clickhouse/concepts/update-policy.md).

Владельцы затронутых кластеров БД получают предварительное оповещение о сроках проведения работ и доступности баз данных.

#### Как рассчитывается стоимость потребления для хоста базы данных? {#db-cost}

В {{ mch-short-name }} стоимость потребления рассчитывается исходя из следующих параметров:

- Выбранный класс хостов.
- Объем хранилища, зарезервированного для хоста БД.
- Объем резервных копий кластера БД. Объем резервных копий, равный объему хранилища, не тарифицируется. Хранение резервных копий сверх этого объема оплачивается по [тарифам](../../managed-clickhouse/pricing.md).
- Количество часов работы хоста БД. Неполные часы округляются до целого значения. Стоимость часа работы для каждого класса хостов приведена в разделе [{#T}](../../managed-clickhouse/pricing.md).

#### Сколько стоит использование моего кластера? {#cluster-cost}

В [консоли управления]({{ link-console-main }}) перейдите на страницу каталога, выберите сервис **{{ mch-short-name }}** и нажмите на нужный кластер. В правой части экрана вы увидите стоимость использования кластера за месяц. Подробнее см. [{#T}](../../managed-clickhouse/pricing.md).

#### Как изменить вычислительные ресурсы и объем хранилища для кластера БД? {#resources-change}

Вы можете изменять вычислительные ресурсы и объем хранилища в консоли управления — просто выберите другой класс хостов для нужного кластера.

Характеристики кластера изменяются в течение 30 минут. В этот период также могут быть включены другие сервисные работы по кластеру, например, установка обновлений.


{% include [fz-152.md](../../_qa/fz-152.md) %}


{% include [logs](../logs.md) %}