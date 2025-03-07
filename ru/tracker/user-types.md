# Типы пользователей

В {{ tracker-name }} доступны несколько вариантов учетных записей для пользователей. Выберите, какой подходит именно вам.

## Учетные записи в Яндекс ID {#yandex-id}

Для аутентификации пользователей организации можно использовать [Яндекс ID](https://yandex.ru/support/id/index.html). Пользователи смогут регистрировать аккаунт на Яндекс ID следующими способами:

* [с почтой @yandex.ru](https://yandex.ru/support/id/authorization/registration.html);
* [с помощью аккаунта в социальной сети](https://yandex.ru/support/id/social.html);
* [с любой другой почтой](https://yandex.ru/support/id/authorization/lite.html).

Особенности использования учетных записей в Яндекс ID:

1. Аккаунт принадлежит самому пользователю.
1. Можно использовать любой сервис организаций: подойдет и {{ ya-360 }}, и {{ org-full-name }}.
1. Пользователя можно удалить из организации, и он потеряет доступ ко всем ее данным, но сможет использовать аккаунт в личных целях.

## Учетные записи в {{ ya-360 }} {#ya-360}

Если вы планируете использовать организацию {{ ya-360 }}, то для регистрации пользователей можно использовать:

* созданный в {{ ya-360 }} [домен организации](https://yandex.ru/support/business/domains/add-domain.html);
* [систему единого входа (SSO)](https://yandex.ru/support/business/sso.html).

Особенности использования учетных записей в Яндекс ID:

1. Это корпоративные учетные записи, пользователи не смогут использовать их в личных целях.
1. Поддерживаются учетные записи и вход через Яндекс ID.
1. После удаления пользователя из организации его учетная запись удаляется.
1. Пользователей можно пригласить в любое количество организаций {{ yandex-cloud }}.

## Учетные записи в {{ org-full-name }} {#cloud-org}

Если вы планируете использовать организацию {{ org-full-name }}, то для регистрации пользователей можно использовать [федерацию удостоверений](../organization/concepts/add-federation.md). При авторизации пользователи должны будут указать идентификатор федерации или использовать специальную ссылку.

Можно настроить несколько федераций для организации. Федеративные пользователи не смогут входить ни в какие другие сервисы, кроме сервисов {{ yandex-cloud }}.
