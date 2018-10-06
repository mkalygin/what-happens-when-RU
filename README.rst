Что происходит, когда...
========================

  This repository is an attempt to answer the age old interview question "What
  happens when you type google.com into your browser's address box and press
  enter?"

Этот репозиторий — попытка ответить на извечный вопрос собеседований: «Что
происходит, когда вы вводите "google.com" в адресную строку вашего браузера и
нажимаете клавишу Enter?».

  Except instead of the usual story, we're going to try to answer this question
  in as much detail as possible. No skipping out on anything.

Только вместо заурядного ответа мы попробуем дать максимально полный и
исчерпывающий ответ, не упуская ни одной детали.

  This is a collaborative process, so dig in and try to help out! There are tons
  of details missing, just waiting for you to add them! So send us a pull
  request, please!

Это совместный процесс, поэтому любая помощь в написании ответа только
приветствуется. Очень многие подробности ещё не описаны, но вы можете о них
рассказать. Так что присылайте свои пулл реквесты, пожалуйста.

  This is all licensed under the terms of the `Creative Commons Zero`_ license.

На всю эту работу распространяются условия лицензии `Creative Commons Zero`_.

  Read this in `简体中文`_ (simplified Chinese) and `한국어`_ (Korean). NOTE: these
  have not been reviewed by the alex/what-happens-when maintainers.

Оригинал этой работы доступен на `английском`_ языке. Также есть переводы на
`китайском`_ и `корейском`_ языках. Все переводы, включая этот, не были
проверены авторами оригинала.

Содержание
==========

.. contents::
   :backlinks: none
   :local:

Нажатие клавиши "g"
-------------------

  The following sections explain the physical keyboard actions
  and the OS interrupts. When you press the key "g" the browser receives the
  event and the auto-complete functions kick in.
  Depending on your browser's algorithm and if you are in
  private/incognito mode or not various suggestions will be presented
  to you in the dropbox below the URL bar. Most of these algorithms sort
  and prioritize results based on search history, bookmarks, cookies, and
  popular searches from the internet as a whole. As you are typing
  "google.com" many blocks of code run and the suggestions will be refined
  with each key press. It may even suggest "google.com" before you finish typing
  it.

В следующих разделах объясняются действия с клавиатурой и прерывания ОС.
Когда вы нажимаете на клавишу "g", браузер получает событие нажатия клавиши,
и срабатывает функция автозаполнения адресной строки. В зависимости от
алгоритма автозаполнения браузера и от режима его работы (обычный или
инкогнито) появляются разные списки вариантов автозаполнения под адресной
строкой. Большинство из этих алгоритмов сортируют и приоритизируют варианты,
исходя из ваших истории поиска, закладок, куки, а также популярных запросов
из интернета. По мере ввода "google.com" запускается множество блоков кода,
которые обновляют варианты автозаполнения после нажатия каждой клавиши. Функция
автозаполнения может даже предложить вариант "google.com" до того, как вы
закончите набор этой строки.

Нажатие клавиши "Enter"
-----------------------

  To pick a zero point, let's choose the Enter key on the keyboard hitting the
  bottom of its range. At this point, an electrical circuit specific to the enter
  key is closed (either directly or capacitively). This allows a small amount of
  current to flow into the logic circuitry of the keyboard, which scans the state
  of each key switch, debounces the electrical noise of the rapid intermittent
  closure of the switch, and converts it to a keycode integer, in this case 13.
  The keyboard controller then encodes the keycode for transport to the computer.
  This is now almost universally over a Universal Serial Bus (USB) or Bluetooth
  connection, but historically has been over PS/2 or ADB connections.

В качестве отправной точки рассмотрим ситуацию, когда клавиша "Enter" находится
в нажатом состоянии. В этот момент связанная с клавишей "Enter" электрическая
цепь замкнута (либо напрямую, либо посредством ёмкостной связи). В результате
замыкания ток попадает в логическую схему клавиатуры, которая сканирует состояние
выключателей всех клавиш, воспринимает электрический сигнал нажатия клавиши,
а затем преобразует его в числовой код клавиши, который в этом случае равен 13.
После чего контроллер клавиатуры подготавливает числовой код клавиши для
передачи его компьютеру. Сейчас передача осуществляется через Universal Serial
Bus (USB) или через Bluetooth, но исторически осуществлялась через PS/2 или ADB
соединения.

*В случае использования USB клавиатуры:*

  - The USB circuitry of the keyboard is powered by the 5V supply provided over
    pin 1 from the computer's USB host controller.

- USB схема клавиатуры питается напряжением 5В, обеспеченным первым контактом
  USB контроллера компьютера.

  - The keycode generated is stored by internal keyboard circuitry memory in a
    register called "endpoint".

- Сгенерированный код клавиши хранится во внутренней памяти схемы клавиатуры,
  в регистре USB контроллера. Этот регистр называется «конечной точкой».

  - The host USB controller polls that "endpoint" every ~10ms (minimum value
    declared by the keyboard), so it gets the keycode value stored on it.

- USB контроллер компьютера запрашивает информацию из этого регистра с частотой
  ~10мс (минимальное значение, заявленное клавиатурой), чтобы получить значение
  кода клавиши, хранящееся в нём.

  - This value goes to the USB SIE (Serial Interface Engine) to be converted in
    one or more USB packets that follow the low level USB protocol.

- Это значение передаётся в USB SIE (Serial Interface Engine) для преобразования
  в один или более USB пакеты, которые затем передаются по низкоуровневому
  USB протоколу.

  - Those packets are sent by a differential electrical signal over D+ and D-
    pins (the middle 2) at a maximum speed of 1.5 Mb/s, as an HID
    (Human Interface Device) device is always declared to be a "low speed device"
    (USB 2.0 compliance).

- Эти пакеты пересылаются дифференциальным электрическим сигналом по контактам
  D+ и D- (средние два контакта) с максимальной скоростью 1.5Мб/с, т.к. HID (Human
  Interface Device) устройство всегда является «устройством с низкой скоростью»
  (совместимым c USB 2.0).

  - This serial signal is then decoded at the computer's host USB controller, and
    interpreted by the computer's Human Interface Device (HID) universal keyboard
    device driver.  The value of the key is then passed into the operating
    system's hardware abstraction layer.

- Этот последовательный сигнал затем декодируется в USB контроллере компьютера и
  интерпретируется универсальным драйвером HID клавиатуры. Значение клавиши затем
  передаётся в абстрактный аппаратный слой операционной системы.

*В случае виртуальной клавиатуры (как в планшетах и смартфонах):*

  - When the user puts their finger on a modern capacitive touch screen, a
    tiny amount of current gets transferred to the finger. This completes the
    circuit through the electrostatic field of the conductive layer and
    creates a voltage drop at that point on the screen. The
    ``screen controller`` then raises an interrupt reporting the coordinate of
    the key press.

- Когда пользователь нажимает пальцем на современный ёмкостный сенсорный экран,
  ток электрической цепи проходит через палец. Это замыкает электрическую цепь
  через электростатическое поле проводящей плоскости и приводит к падению напряжения
  в этой точке экрана. ``Контроллер экрана`` затем вызывает сигнал прерывания и
  сообщает координаты нажатия на экране.

  - Then the mobile OS notifies the current focused application of a press event
    in one of its GUI elements (which now is the virtual keyboard application
    buttons).

- Затем мобильная ОС уведомляет текущее активное приложение о событии нажатия
  на экран в одном из его GUI элементов (в данном случае это кнопки в приложении
  виртуальной клавиатуры).

  - The virtual keyboard can now raise a software interrupt for sending a
    'key pressed' message back to the OS.

- Виртуальная клавиатура теперь может вызвать программное прерывание для
  отправки сообщения операционной системе о нажатии клавиши.

  - This interrupt notifies the current focused application of a 'key pressed'
    event.

- Это прерывание уведомляет текущее активное приложение о событии нажатой
  клавиши.

.. _`Creative Commons Zero`: https://creativecommons.org/publicdomain/zero/1.0/
.. _`английском` : https://github.com/alex/what-happens-when
.. _`китайском`: https://github.com/skyline75489/what-happens-when-zh_CN
.. _`корейском`: https://github.com/SantonyChoi/what-happens-when-KR
