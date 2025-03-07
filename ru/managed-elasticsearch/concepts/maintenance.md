---
title: "Техническое обслуживание в {{ mes-name }}"
description: "Под техническим обслуживанием понимается автоматическая установка обновлений и исправлений {{ ES }} для хостов (в т. ч. для выключенных кластеров), изменение класса хостов и объема хранилища, а также другие сервисные работы."
---

# Техническое обслуживание в {{ mes-name }}

{% include [Elasticsearch-end-of-service](../../_includes/mdb/mes/note-end-of-service.md) %}

Под техническим обслуживанием понимается:

* автоматическая установка обновлений и исправлений {{ ES }} для хостов (в т. ч. для выключенных кластеров);
* изменение класса хостов и объема хранилища;
* другие сервисные работы.

Техническое обслуживание включает изменения в рамках одной мажорной версии {{ ES }}. О том, как происходит переход между мажорными версиями см. в разделе [{#T}](../operations/cluster-version-update.md).

## Окно обслуживания {#maintenance-window}

Предпочтительное время технического обслуживания можно задать при [создании кластера](../operations/cluster-create.md) или [изменении его настроек](../operations/cluster-update.md):

* **{{ ui-key.yacloud.mdb.cluster.overview.label_anytime-maintenance-warning-value }}** (по умолчанию) — разрешает проведение технического обслуживания в любое время.
* **{{ ui-key.yacloud.mdb.forms.value_maintenance-type-weekly }}** — укажите предпочтительное время начала обслуживания: нужные день недели и час дня по UTC. Например, можно выбрать время, когда кластер наименее загружен.

## Порядок обслуживания {#maintenance-order}

В однохостовых кластерах {{ mes-name }} техническое обслуживание проходит единственный хост [с ролью _Data node_](./hosts-roles.md#data-node). Поэтому если во время технического обслуживания потребуется его перезагрузка, такой кластер станет недоступным.

В многохостовых кластерах хосты с ролью _Data node_ последовательно проходят техническое обслуживание. Порядок хостов в очереди определяется случайным образом. Если во время технического обслуживания потребуется перезагрузка хоста, он станет недоступным на это время. Если вы используете для доступа к кластеру FQDN хоста {{ ES }}, такой кластер может стать недоступным. Чтобы обеспечить бесперебойную работу приложения, подключайтесь к кластеру через [специальный FQDN](../operations/cluster-connect.md#automatic-host-selection), всегда указывающий на доступный хост.
