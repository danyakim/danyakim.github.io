---
layout: post
title:  "wxPython. Часть 1. Введение"
date:   2014-08-27
categories: blog
published: no
---

## wxPython
wxPython — это кросс-платформенная библиотека для создания настольных приложений с графическим интерфейсом. Создатель библиотеки — **Робин Данн**. С помощью wxPython разработчики могут создавать приложения для OS X, Windows и UNIX-подобрых систем. wxPython является надстройкой над wxWidgets, кросс-платформенной библиотекой написанной на С++. wxPython состоит из пяти основных модулей.

{:.center}
![wxPython modules](/assets/wxpython-1/modules.jpg)

1. Модуль **Controls** предоставляет основные элементы управления (виджеты), которые вы можете увидеть в приложениях с графическим интерфейсом (кнопка, тулбар, текстовое поле).
2. Модуль **Core** состоит из других классов, которые используются при разработке: класс Object, от которого наследуются все остальные классы, вспомогательные классы для отрисовки элементов управления, события (Events) и геометрия (Geometry), куда входят классы точки (Point) и прямоугольника (Rectangle).
3. Graphics Device Interface (**GDI**) — набор классов для отрисовки виджетов. В этом модуле содержатся классы для управления шрифтами, цветами, кистями, маркерами и изображениями.
4. **Misc** содержит прочие вспомогательные классы и функции для логов, конфигурации приложения, системных настроек и для работы с дисплеем и другими устройствами.
5. Модуль **Windows** состоит из различных окон, которые образуют приложение: Panel, Dialog, Frame или Scrolled Window.

### wxPython API
API wxPython представляет собой методы и объекты. Виджеты — это фундамент для построения графического приложения (в Windows виджеты называются элементами управления). Мы примерно можем разделить программистов на две групы: те, кто пишет билиотеки, и те, кто их использует. В нашем случае wxPython — это библиотека, которую используют другие разработчики. Формально, wxPython — это обертка над wxWidgets, GUI фреймворком, написанном на C++, то есть это не нативный API и непосредственно не написан на Python.

## Группы виджетов
wxPython предоставляет множество виджетов. Они могут быть поделены на логические группы.

### Основные виджеты
Эти виджеты предоставляют функционал для производных виджетов, напрямую не используются.

{:.center}
![Base widgets](/assets/wxpython-1/base.jpg)

### Высокоуровневые виджеты
Эти виджеты существуют независимо друг от друга.

{:.center}
![](/assets/wxpython-1/toplevel.jpg)

### Контейнеры
Контейнеры содержат другие виджеты.

{:.center}
![](/assets/wxpython-1/containers.jpg)

### Динамические виджеты
Могут быть изменены пользователем.

{:.center}
![](/assets/wxpython-1/dynamic.jpg)

### Статические виджеты
Отображают информацию. Не могут быть изменены пользователем.

{:.center}
![](/assets/wxpython-1/static.jpg)

### Прочие виджеты
Позволяют реализовать строку состояния (statusbar), панель инструментов (toolbar) и меню в приложении.

{:.center}
![](/assets/wxpython-1/bars.jpg)

### Наследование
Все виджеты в wxPython связаны между собой наследованием. Наследование — это важнейшая часть объектно-ориентированного программирования (ООП). Виджеты образуют иерархию, могут наследовать функционал от других виджетов (родительских), такие виджеты называются производными или дочерними.

#### Наследование кнопки
Допустим, мы хотим использовать кнопку (button) в нашем приложении. Кнопка наследуется от четырех родительских классов. Ближайший — класс *wx.Control*. В wxPython элементы управления (controls) — это виджеты, которые располагаются на других виджетах — **контейнерах**. Кнопка — это по сути маленькое окно. Все виджеты, которые появляются на экране, являются окнами, поэтому они наследуют класс *wx.Window*. Помимо этого, существуют объекты, которые не видны на экране: *wx.Sizer* (вспомогательный класс для размещения виджетов), информация об окружении и региональные параметры (locale). Так же есть классы, которые видны, но не являются окнами: объект цвета, курсоры. Не все виджеты являются элементами управления, например, *wx.Dialog*.

{:.center}
![](/assets/wxpython-1/inheritance.png)

Кнопка, как и все окна, может реагировать на события. При нажатии на кнопку, срабатывает событие *wx.EVT_COMMAND_BUTTON_CLICKED*. Кнопка наследует класс *wx.EvtHandler*, что дает разработчику возможность определить поведение при нажатии кнопки. Каждый виджет, который реагирует на события, наследуется от *wx.EvtHandler*. И наконец, все объекты наследуется от *wx.Object* — прародителя всех объектов в wxPython.

Эта статья является переводом [данного](http://zetcode.com/wxpython/) руководства с дополнениями.