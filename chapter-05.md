# Установка OpenVPN на Linux и Unix системы

Установка OpenVPN проста и не зависит от платформы. В этой главе мы установим его на различные версии Linux и FreeBSD.

## Предпосылки

Все системы Linux/Unix должны соответствовать следующим требованиям для успешной установки OpenVPN:
* Ваша система должна обеспечивать поддержку универсального драйвера TUN/TAP. Ядра новее версии 2.4 почти всех современных дистрибутивов Linux обеспечивают поддержку устройств TUN/TAP. Только если вы используете старый дистрибутив или создали собственное ядро, вам придется добавить эту поддержку в свою конфигурацию. В разделе этой главы, _Включение поддержки ядра Linux для устройств TUN/TAP_, рассматривается эта проблема. Веб-сайт этого проекта можно найти по адресу http://vtun.sourceforge.net/tun/.
* Библиотеки OpenSSL должны быть установлены в вашей системе. Я никогда не встречал ни одной современной системы Linux/Unix, которая не удовлетворяла бы этому требованию. Однако, если вы хотите скомпилировать OpenVPN из исходных кодов, пакет разработки SSL может быть необходим. Веб-сайт: http://www.openssl.org/.
* Необходимо установить библиотеку сжатия **Lempel-Ziv-Oberhumer (LZO)**. Опять же, большинство современных систем Linux/Unix предоставляют эти пакеты, так что не должно быть никаких проблем. LZO - это библиотека сжатия в реальном времени, используемая OpenVPN для сжатия данных перед отправкой. Пакеты можно найти на http://openvpn.net/download.html, и веб-сайт этого проекта http://www.oberhumer.com/opensource/lzo/.
* Большинство средств установки Linux/Unix систем способны самостоятельно решить эти так называемые зависимости, но было бы полезно знать, где взять необходимое программное обеспечение.
* Большинство коммерческих систем Linux, таких как SuSE, предоставляют средства установки, такие как **Yet another Setup Tool (YaST)**, и содержат последние версии OpenVPN на своих установочных носителях (CD или DVD). Кроме того, системы, основанные на программном обеспечении RPM, могут также устанавливать и управлять программным обеспечением OpenVPN из командной строки.
* Системы Linux, такие как Debian, используют сложные инструменты управления пакетами, которые могут устанавливать программное обеспечение, предоставляемое репозиториями на веб-серверах. Локальный носитель не требуется, управление пакетами само решит потенциальные зависимости и установит самую новую и безопасную из возможных версий OpenVPN.
* FreeBSD и другие системы в стиле BSD используют свои инструменты управления пакетами, такие как `pkg_add` или система портов.
* Как и все проекты с открытым исходным кодом, исходный код OpenVPN доступен для загрузки. Этот сжатый файл `tar.gz` или `tar.bz2` может быть загружен с http://openvpn.net/download.html и распаковки в локальный каталог. Этот исходный код должен быть сконфигурирован и переведен (скомпилирован) для вашей операционной системы.
* Вы также можете установить нестабильную, разрабатываемую или более старую версию OpenVPN из http://openvpn.net/download.html это может быть интересно, если вы хотите протестировать новые возможности будущих версий.
* Ежедневные (неустойчивые!) сборки исходных кодов OpenVPN можно получить на http://sourceforge.net/cvs/?group_id=48978, здесь вы найдете репозиторий **системы параллельных версий (Concurrent Versions System - CVS)**, где все разработчики OpenVPN размещают свои изменения в файлах проекта.

## Установка OpenVPN на SuSE Linux

Установка OpenVPN на SuSE Linux почти так же проста, как установка под Windows или Mac OS X. Пользователи Linux могут считать, что это еще проще. На SuSE Linux практически все административные задачи можно выполнять с помощью интерфейса администрирования YaST. OpenVPN может быть установлен полностью с помощью этого. Люди, распространяющие SuSE, всегда старались включать в свой дистрибутив самое современное программное обеспечение. Таким образом, установочный носитель OpenSuSE 11 уже содержит версию OpenVPN 2.0.9, а также как корпоративные версии SLES 10, так и предстоящие SLES 11, которые предлагают пятилетнюю поддержку. Обновления включают в себя обновленные версии OpenVPN. Как OpenSuSE, так и SLES используют YaST для установки программного обеспечения.

### Использование YaST для установки программного обеспечения

Запустите YaST. Как в GNOME, так и в **среде K Desktop** (**KDE** — стандартный рабочий стол под SuSE Linux), вы найдете YaST в главном меню под **System | YaST**, или в виде значка на рабочем столе. Если вы вошли в систему как обычный пользователь, вам будет предложено ввести пароль root и подтвердить его. Запустится центр управления YaST.

![](/pics/pic5-1.png)

Этот интерфейс администрирования состоит из множества различных модулей, которые представлены символами в правой половине окна и сгруппированы по меткам слева.

![](/pics/pic5-2.png)

После запуска YaST нажмите на символ с надписью **Software Management** в правом столбце, чтобы запустить интерфейс управления программным обеспечением YaST.

Инструмент управления программным обеспечением в YaST очень мощный. В рамках SuSE данные об установленном и устанавливаемом программном обеспечении хранятся в базе данных, которую можно очень легко найти. Выберите пункт **Search** в раскрывающемся списке **Filter**: и введите **openvpn** в поле поиска.

YaST найдет по крайней мере одну запись, которая соответствует вашему поисковому значению **openvpn**. В зависимости от настроенных вами источников установки (онлайн) будут найдены различные дополнения и инструменты для OpenVPN. Если вы решили добавить репозитории сообщества, как я сделал в этой системе, то OpenSuSE будет перечислять более 10 подсказок.

![](/pics/pic5-3.png)

Выберите запись **openvpn**, установив флажок рядом с записью в первом столбце. Если вы хотите получить информацию о пакете OpenVPN, посмотрите на нижнюю половину правой стороны — здесь вы найдете **Description (Описание)**, **Technical Data (технические данные)**, **Dependencies (зависимости)** программного обеспечения и дополнительную информацию о пакете, который вы выбрали. Нажмите на кнопку **Accept (Принять)**, чтобы начать установку OpenVPN.

Если вы установили дистрибутив с локального носителя, то теперь вставьте CD или DVD-диск в локальный дисковод. YaST извлекет файлы OpenVPN с вашего установочного носителя. Если вы настроили свою систему на использование одного из web/FTP-серверов SuSE для установки, то это может занять некоторое время. Файлы распаковываются и устанавливаются в вашей системе, а YaST обновляет конфигурацию. Это управляется сценарием SuSEconfig и другими сценариями, которые вызываются им.

SuSEconfig и YaST когда-то были очень печально известны тем, что удаляли локальную конфигурацию, созданную локальным администратором или пропускали соответствующие изменения. Эта проблема возникает только при обновлении и повторной установке программного обеспечения, которое было установлено ранее. Однако последние версии SuSE оказались очень надежными, и средства настройки системы уже не удаляют файлы конфигурации, добавленные вручную. Вместо этого стандартные конфигурационные файлы, установленные вместе с новым пакетом программного обеспечения, могут быть переименованы в `<file>.rpmnew` или аналогичный и ваша конфигурация загрузится.

Во время установки SuSEconfig вызывает несколько вспомогательных скриптов, обновляет конфигурацию и сообщает о ходе выполнения в отдельном окне. После успешной установки программного обеспечения вам будет предложено установить дополнительные пакеты или завершить установку. Нажмите на кнопку Finish.

Команды Novell/OpenSuSE добавили очень удобный инструмент под названием `zypper` для управления пакетами. Начиная с версии 10.1, вы можете просто установить программное обеспечение из консоли root'а, набрав `zypper in openvpn`. Конечно, это работает только в том случае, если вы знаете точное имя пакета, который хотите установить. Если нет, то вам придется искать его, например, с помощью `zypper search vpn`.

![](/pics/pic5-4.png)
