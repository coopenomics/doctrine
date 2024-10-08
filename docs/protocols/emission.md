# Протокол Эмиссии

Протокол представляет собой экономическую модель аппаратно-программной сети «Кооперативная экономика». 

## Общие положения
- Протокол реализован и исполняется в системном смарт-контракте @eosio;
- Изменить принятый протокол эмиссии могут только делегаты сети при общем консенсусе 70%;
- Протокол управляет распределенной эмиссией утилити-токена AXON;
- Посредством утилити-токена AXON кооперативы оплачивают минимальную подписку на аренду вычислительных ресурсов блокчейн-сети и доплачивают фактическую стоимость их использования;
- Подписка кооперативов на ресурсы предоставляет их пайщикам возможность совершать действия в сети;
- Результатом полезной работы AXON является юридически-значимый акт действия. 
- Протокол эмитирует новые AXON при условии роста спроса;
- Протокол останавливает эмиссию AXON, если спрос не растёт;


## Протокол

Протокол исполняется в системном контракте с идентификатором @eosio. Код контракта представлен в репозитории: [](https://github.com/coopenomics/contracts/tree/master/system). 

Эмиссия начинается с генезиса - выпуска начального количества токенов, которые в количестве 10000 AXON. Эти токены передаются первым кооперативам, начинающим работать на платформе. Токены используются ими для оплаты минимальной подписки в размере 100 AXON в месяц за вычислительные ресурсы блокчейна, что обеспечивает возможность зарегистрировать 50 пайщиков или провести 10 кооперативных операций клиринга. Превышение использования минимальной ежемесячной квоты приводит к необходимости кооперативам арендовать ресурсы по факту их использования.    

С момента передачи кооперативам первых токенов, начинается экономическое расширение системы. Расширение происходит тактами - интервалами времени, в течение которого количество собранных комиссий за такт должно превысить заданный лимит в такте для начала эмиссии AXON. 


<figure markdown="span">
  ![](/assets/protocols/tacts.png){width="50%"}
  <figcaption>порядок эмиссии по тактам</figcaption>
</figure>


Порог начала эмиссии устанавливается на уровне 1000 AXON за один такт при генезисе в 10000 AXON. Время такта - 30 дней. Таким образом, для того, чтобы эмиссия началась, система должна собрать комиссий на сумму 1000 AXON за месяц. При сборе 1000 AXON, начинается эмиссия, в процессе которой на каждый токен собранных комиссий выпускается 1.618 токена, которые отправляются в системный фонд. 

Эмиссия продолжается до истечения времени такта. При истечении времени такта, эмиссия останавливается, и начинается заново, если объем собранных комиссий превышает 61.8% от общего числа токенов в оборота. 

Математическая формула дополнительной эмиссии:

ΔVi = Qi * 0,618 – (V-Qi),

где ΔVi – количество дополнительно выпускаемых токенов на будущий
такт; Qi – количество токенов (комиссия), оплаченных делегатам за
проведение транзакций за такт; V – общий объем токенов в сети. (V-Qi) –
токены в накоплении на кошельках кооперативов.

Общий объем токенов в сети рассчитывается по формуле:

V = V1 + ΔV1 + ΔV2 + ΔV3 + … + ΔVi,

Где V1 – это первичная эмиссия токенов (генезис);


Таким образом, децентрализованная эмиссия построена на правиле дополнительной эмиссии, которое включает эмиссию при достижении минимального предела и выключает её при завершении времени такта. 

<figure markdown="span">
  ![](/assets/protocols/emission1.jpg){ width="600" }
  <figcaption>модель расширения системы</figcaption>
</figure>






