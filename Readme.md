# Multilanguage Readme

[![en](https://img.shields.io/badge/lang-en-blue.svg)](https://github.com/Hostwerk-Labs/t3rn-node/blob/main/Readme-EN.md)
[![ru](https://img.shields.io/badge/lang-ru-red.svg)](https://github.com/Hostwerk-Labs/t3rn-node/blob/main/Readme.md)

# T3RN executor нода

C использованием Ansible и Docker для масштабированных установок

Мы всегда используем контейнеризированные версии экзекуторов с открытым исходным кодом

# Гайд

## Требовнаия

- ansible core >= 2.17.4
- docker >= 26.1

## Настройка и запуск ноды

1. Развертываем конфигурацию на наши целевые серверы

   `ansible-playbook -i inventory --limit "cluster0" t3rn.yml`

   Или для всех кластеров

   `ansible-playbook -i inventory --limit "cluster0" t3rn.yml`

2. Заходим на сервер и запускаем ноду

   `cd /storage/nodes/hostwerk`

   `docker compose up -d`

3. Проверяем логи запущенного сервера
   `docker compose logs -f --tail=300`

# Эксплуатация

## Типовые ошибки

    - `{"level":"error","time":1737492475413,"environment":"testnet","sourceNetwork":"blss","address":"0x9c5eE6A43e9823D95518cCBDe598D4C7feae3228","code":"NETWORK_ERROR","error":"could not detect network (event=\"noNetwork\", code=NETWORK_ERROR, version=providers/5.7.2)","msg":"❌ RPC error at getBalance"}`

- неверно указли RPC сети, в нашем случае blss - Blast

  - `👨‍⚖️Your bid was not accepted because it failed our Bid Difficulty measures filter. This helps ensure bids remain fair & saves on your gas.` - текущие ставки и ваш газ в конфиге не соответствуют сделке

  - `📝💔 Order is not profitable. Skip order` - ваши настройки по газу, а также текущие сделки не попадают в профитую зону

## Типовой успех

    - `🥊 Start processing txs in Transmitter...` - вы что то пытаетсь обработать - шанс завешрить транзацию и получить токен за нее

    - `🧡 Processing new profitable Order` - скорее всего ваш bid сыграл и вам досталась транзакция на execute

Больше про ноды и web3 инфраструктуру в нашем [Telegram](https://t.me/+irchepr8HtllZWIy)
