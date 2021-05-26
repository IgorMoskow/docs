# Версионирование. Работа с контрольными точками

Контрольная точка в {{ ml-platform-name }} — это [сохраненное состояние](../../concepts/save-state.md) ноутбука. Контрольная точка включает код ячеек, вывод и значения переменных.

## Перед началом {#before-begin}

Если проект уже открыт, перейдите на вкладку ноутбука.

Если нет, откройте проект:
1. {% include [include](../../../_includes/datasphere/first-step.md) %}
1. Перейдите во вкладку **Проекты**.
1. Выберите проект, который хотите открыть и нажмите значок ![image](../../../_assets/datalens/horizontal-ellipsis.svg).
1. Выберите **Открыть** и дождитесь открытия проекта.

## Создание контрольной точки {#create}

Чтобы создать контрольную точку в [стандартном](../../concepts/save-state.md#default-save) режиме сохранения состояний:

1. Откройте панель ![checkpoints-panel](../../../_assets/datasphere/jupyterlab/checkpoints-panel.svg) **Checkpoints**.

    Если вы уже выполняли код в открытом проекте, то в списке **Checkpoints** будут содержаться созданные ранее контрольные точки.
1. Выполните код в ячейке или группе ячеек ноутбука.

    Запустите собственный код или воспользуйтесь [примером](snippets.md#run).
1. Дождитесь выполнения кода.

В [автоматическом](../../concepts/save-state.md#auto-save) режиме сохранения состояний вы можете создать контрольную точку принудительно. Для этого в правом верхнем углу вкладки ![checkpoints-panel](../../../_assets/datasphere/jupyterlab/checkpoints-panel.svg) **Checkpoints** нажмите значок ![plus-sign](../../../_assets/plus-sign.svg), либо используйте сочетание клавиш `CMD+K` или `Ctrl+K`.

Созданная контрольная точка появится в начале списка **Checkpoints**. Имя контрольной точки состоит из следующих элементов:
* Ключ операции, после выполнения которой была создана контрольная точка, например `[1]`.

   Такой же ключ отображается в ноутбуке слева от выполненной ячейки.
* Тип операции, после которой была создана контрольная точка, например `CELL_RUN`.
* Имя ноутбука, в котором была выполнена ячейка, например `Untitled.ipynb`.
* Дата и время создания контрольной точки в [UTC](https://ru.wikipedia.org/wiki/Всемирное_координированное_время), например `2020-10-09 06:12:08`.

Для одного проекта может быть создано не более десяти контрольных точек, более старые контрольные точки автоматически удаляются.

## Применение контрольной точки {#apply}

Чтобы вернуться к состоянию ноутбука на определенной контрольной точке:
1. Откройте панель ![checkpoints-panel](../../../_assets/datasphere/jupyterlab/checkpoints-panel.svg) **Checkpoints-panel**.
1. Выберите нужную контрольную точку в списке.
1. Нажмите кнопку **Apply**.
1. Дождитесь выполнения операции.

После восстановления состояния будет создана контрольная точка с типом операции `ROLLBACK` в имени.

## Сохранение контрольной точки {#pin}

Чтобы защитить контрольную точку от автоматического удаления, ее нужно сохранить:
1. Откройте панель ![checkpoints-panel](../../../_assets/datasphere/jupyterlab/checkpoints-panel.svg) **Checkpoints-panel**.
1. Выберите нужную контрольную точку в списке **Checkpoints** и нажмите кнопку **Pin**.
1. В открывшемся окне введите имя сохраняемой контрольной точки.
1. Нажмите кнопку **Save**.

Сохраненная контрольная точка переместится в список **Pinned checkpoints**.

Для одного проекта может быть сохранено не более пяти контрольных точек, более старые сохраненные контрольные точки автоматически удаляются.

Чтобы снять защиту контрольной точки, нажмите кнопку **Unpin**. Контрольная точка переместится в список **Checkpoints**.

## Экспорт контрольной точки {#export}

Сохраненную контрольную точку можно экспортировать:

1. Откройте панель ![checkpoints-panel](../../../_assets/datasphere/jupyterlab/checkpoints-panel.svg) **Checkpoints-panel**.
1. В списке **Pinned checkpoints** выберите контрольную точку.
1. Нажмите кнопку **Share**.
1. В открывшемся окне нажмите кнопку **Copy to clipboard**.

Ссылка на контрольную точку ноутбука будет скопирована в буфер обмена.

## Импорт контрольной точки {#import}

Чтобы импортировать ноутбук из контрольной точки:

1. В верхней панели нажмите **File** и выберите **Import notebook from checkpoint**.
1. В открывшемся окне введите `URI` контрольной точки.
1. Нажмите кнопку **import**.
1. Дождитесь выполнения операции.