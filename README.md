# NEWCAR Telegram Mini App — MVP

Это фронтенд-прототип Mini App для `@NEWCAR_AutoBot`.

## Что реализовано
- Premium Dark / Telegram theme через `Telegram.WebApp`.
- Расчёт полной себестоимости.
- Комиссия NEWCAR: 5%, минимум 45 000 ₽, максимум 300 000 ₽.
- Контроль маржи.
- Gate перед отправкой КП.
- Подбор по бюджету.
- Заявка менеджеру.
- Подготовка payload для будущего backend → Bitrix24.

## Что НЕ является автоматическим расчётом
Таможенная пошлина, утильсбор, НДС/акциз и ТН ВЭД в демо вводятся вручную. Перед боевым использованием их нужно получать из проверенного расчётного ядра NEWCAR.

## Следующий backend
POST /api/leads
POST /api/calculations
POST /api/quotes
POST /api/bitrix/webhook

Backend должен:
1. Проверять Telegram initData на сервере.
2. Создавать/обновлять контакт и сделку в Bitrix24.
3. Передавать cost_total, client_price, margin, country, vehicle, VIN и источник лида.
4. Ставить стадию и задачи согласно карте автоматизации 14.57.
5. Не разрешать отправку КП при непройденном Quality/Risk/Margin Gate.
