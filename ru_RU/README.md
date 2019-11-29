# Руководство по настройке V2Ray

## отказ

Этот репозиторий является веткой `ToutyRater / v2ray-guide`, спасибо, что помогли многим людям пересечь GFW.

Поскольку мы хотим сделать [оригинальное руководство по V2Ray] (https://github.com/ToutyRater/v2ray-guide) более ухоженным и актуальным, а также многоязычным, мы раздвоили этот новый репозиторий. , Вы можете поделиться своим опытом, переводом и исправлением этого документа, открыв выпуск. Кроме того, если вы хотите помочь нам вычитать этот перевод, пожалуйста, не стесняйтесь открывать вопрос.

Документы теперь лицензированы в соответствии с [BY-CC 4.0] (`LICENSE.md`).

## Введение

V2Ray - это инструмент в рамках проекта V. Проект V - это проект, который включает в себя набор инструментов для построения определенных сетевых сред, а V2Ray является основным. В руководстве по Project V сказано, что Project V - это набор инструментов, которые помогут вам создать собственную сеть конфиденциальности через Интернет. Ядро Project V, названное V2Ray, отвечает за сетевые протоколы и связь. Он может работать как автономно, так и в сочетании с другими инструментами. Однако с точки зрения времени запуска Project V имеет приоритет перед V2Ray. Если вы все еще не понимаете, то мы просто говорим, V2Ray - это аналог прокси-сервера для Shadowsocks. V2Ray может быть использован для доступа в Интернет (через цензуру), чтобы изучить передовые науки и технологии из бесплатного Интернета. ``

V2Ray Руководство пользователя:
 - [https://www.v2ray.com](https://www.v2ray.com) (Has been blocked in China)
 - [https://v2fly.org](https://v2fly.org)

Адрес хранилища V2Ray: [https://github.com/v2ray/v2ray-core](https://github.com/v2ray/v2ray-core) Адрес хранилища V2Ray (хранилище V2Fly): [https://github.com /v2ray/v2ray-core](https://github.com/v2fly/v2ray-core)

Дискуссионная группа пользователей V2Ray Telegram: [https://t.me/projectv2ray](https://t.me/v2fly_chat)


## Частые вопросы: Q &amp; A


#### В чем разница между V2Ray и Shadowsocks?

Разница все еще в том, что Shadowsocks - простой прокси-инструмент; это протокол шифрования. Тем не менее, V2Ray разработан как платформа, и любой разработчик может использовать модули, предоставляемые V2Ray, для разработки нового прокси-программного обеспечения.

Любой, кто знаком с историей Shadowsocks, должен знать, что это самоиспользуемое программное обеспечение, разработанное clowwindy. Первоначальная цель разработки - сделать так, чтобы было проще и эффективнее пересекать межсетевой экран и цензуру. До того, как clowwindy создал Shadowsocks с открытым исходным кодом, он долгое время использовался в качестве частного прокси-протокола. Принимая во внимание, что V2Ray был разработан после того, как clowwindy получил угрозу от правительства Китая, команда Project V была разработана в знак протеста.

Из-за различных исторических предпосылок при рождении, они имеют разные особенности.

Проще говоря, Shadowsocks - это протокол с одним прокси, а V2Ray сложнее, чем прокси с одним протоколом. Звучит немного мрачно для Shadowsocks? конечно нет! С другой стороны, Shadowsocks просты в развертывании, а V2Ray имеет более сложные конфигурации при развертывании.

#### Поскольку V2Ray сложнее, зачем мы его используем?

Преимущества и недостатки чего-то всегда приходят вместе. Например, V2Ray имеет следующие преимущества:

* ** Новый и мощный протокол: ** V2Ray использует новый протокол VMess, разработанный самим собой, который улучшает некоторые из существующих недостатков Shadowsocks и его труднее обнаружить с помощью брандмауэра.
* ** Лучшая производительность: ** Лучшая производительность сети, конкретные данные можно увидеть [официальный блог V2Ray] (https://steemit.com/cn/@v2ray/3cjiux)
* ** Дополнительные функции: ** Ниже приведены некоторые функции V2Ray:
    * mKCP: реализация протокола KCP на V2Ray, вам не нужно устанавливать другой kcptun.
    * Динамический порт: динамическое изменение порта связи для борьбы с ограничением скорости в порту с большим длительным трафиком
    * Функции маршрутизации: вы можете свободно устанавливать направление потока указанного пакета данных, блокировать рекламу и включать анти-трекинг
    * Исходящий прокси, или, скажем, цепочечный прокси, использует много ссылок для лучшей конфиденциальности
    * Запутывание: аналогично запутыванию ShadowsocksR, и пакет данных для mKCP также может быть запутан. Запутывание трафика пакетами другого трафика протокола, что делает проверку более сложной
    * Протокол WebSocket: используйте только прокси-сервер WebSocket или промежуточный прокси-сервер CDN (лучше антиблокировка)
    * Mux: мультиплексирование, дальнейшее улучшение одновременной работы прокси

#### Там нет серебряной пули

На данный момент V2Ray имеет следующие недостатки:
- Сложная конфигурация
- Отсутствие сторонних клиентов и услуг

#### Кажется, V2Ray хорош, но я просто хочу пересечь интернет-цензуру, не хочу тратить слишком много времени. Как я могу сделать?

Неважно, что вы делаете, есть усилие. Усилие не означает успех, но никакие усилия определенно не предполагают никакой выгоды. Но если ваше требование относительно простое, вы можете найти VPN, а не развертывать V2Ray самостоятельно.

#### Я решил попробовать развернуть V2Ray, так как я могу следовать этому руководству?

Руководство пользователя V2Ray объясняет все очень подробно. В этом руководстве в основном объясняются возможности V2Ray от простого к сложному в практически доступных конфигурациях, а также делается попытка уменьшить сложность для новичков, использующих V2Ray.

** У пользователей этого руководства должен быть опыт работы с оболочкой Linux, например, как купить VPS, как войти в VPS через SSH, как использовать nano (или vim) для редактирования текста и некоторые основные команды Linux. Есть много руководств онлайн. Нет необходимости повторять их и писать учебник. Если у вас нет опыта, настоятельно рекомендуем вам изучить их заранее, а затем развернуть V2Ray. **

Это руководство можно рассматривать как простую версию руководства пользователя V2Ray или как практическое руководство по V2Ray.

Вы можете следовать инструкциям в этом руководстве для сборки V2Ray, не читая это руководство пользователя, но мы не рекомендуем его. Потому что это руководство просто поможет вам настроить V2Ray. Есть определенные сочетания клавиш по сравнению с руководством пользователя, и что-то игнорируется. Поэтому мы надеемся, что все потратят на прочтение руководства пользователя V2Ray.

#### На что я должен обратить внимание, только начинающий использовать V2Ray?

Поскольку многие пользователи V2Ray имеют опыт работы с Shadowsocks, они могут в основном использовать V2Ray как Shadowsocks. Тем не менее, V2Ray не совсем то же самое, что Shadowsocks, так что мы представим различия в использовании. Обратите внимание, что разница не означает хорошо или плохо. Рекомендуется выбрать конфигурацию, соответствующую вашей сетевой среде.

- Клиент: V2Ray сам по себе является просто ядром. GUI-клиент V2Ray - это в основном оболочка, называемая ядром V2Ray, похожая на отношения между ядром Linux и операционной системой Linux. Но многие клиенты Shadowsocks повторно реализовали протокол автора. Содержание этой статьи не предполагает использования клиентов с графическим интерфейсом в данный момент.
- Политический прокси: возможно, первое воображение - это PAC. Будь то Shadowsocks (в частности, Shadowsocks-libev) или V2Ray сами не поддерживают PAC, он контролируется клиентом пользователя. В то время как Shadowsocks использует ACL, V2Ray использует свою функцию маршрутизации, и мы не говорим, хорошо это или плохо. Вы можете выбрать лучший, зависит от вас.

- Поделиться ссылкой / QR-кодом: V2Ray не имеет унифицированного формата URL, как Shadowsocks, поэтому общая ссылка / QR-код каждого графического клиента V2Ray не обязательно является универсальной. Тем не менее, мы работаем над реализацией протокола протокола конечной точки V2Ray. Он предоставит универсальную ссылку для клиентов V2Ray.
- Шифрование: V2Ray (в частности, протокол VMess) не любит Shadowsocks, который подчеркивает выбор шифрования, а шифрование VMess определяется клиентом, а сервер адаптивен.
- Время: при использовании протокола VMess от V2Ray необходимо обеспечить точное время как для клиента, так и для сервера, поскольку это для безопасного проектирования.
- Пароль: V2Ray (VMesss) использует только UUID, который действует как пароль Shadowsocks, но случайность намного лучше, чем пароль Shadowsocks, но его неудобно запоминать (противоречие безопасности и удобства).
- UDP relay: VMess - это потоковый протокол на основе TCP. Для пакетов UDP VMess будет преобразован в поток TCP, а затем ретранслирует пакеты, то есть UDP через TCP. Чтобы включить UDP, вы можете включить UDP в протоколе socks клиента. Однако обратите внимание, что это не очень хорошо для ускорения игры.
- Прокси шлюза: На самом деле они ничем не отличаются. Не думайте, что вы не сможете использовать их на роутере без плагинов.