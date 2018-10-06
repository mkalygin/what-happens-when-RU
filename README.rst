Что происходит, когда...
====================

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
====================

.. contents::
   :backlinks: none
   :local:

Нажатие клавиши "g"
----------------------

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

.. _`Creative Commons Zero`: https://creativecommons.org/publicdomain/zero/1.0/
.. _`английском` : https://github.com/alex/what-happens-when
.. _`китайском`: https://github.com/skyline75489/what-happens-when-zh_CN
.. _`корейском`: https://github.com/SantonyChoi/what-happens-when-KR
