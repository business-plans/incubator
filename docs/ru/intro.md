# Для чего этот репозиторий?

Этот репозиторий содержит заготовки бизнес-планов.

# Какова структура репозитория?

Структура репозитория должна быть следующая:
```
- LICENSE
- README.md
- docs/
  - ru/
    - intro.md
  - en/
    - intro.md
- bakery/
  - main.yaml
  - equipments.yaml
  - materials-in.yaml
  - materials-out.yaml
  - material-conversion.yaml
  - workers.yaml
  - vehicles.yaml
  - real-estates.yaml
  - ads.yaml
  - target-auditories.yaml
  - credit.yaml
- grocery/
  - main.yaml
  - equipments.yaml
  - materials-in.yaml
  - materials-out.yaml
  - material-conversion.yaml
  - workers.yaml
  - vehicles.yaml
  - real-estates.yaml
...
```
В каждом файле должна находиться соответствующая модель без учета пользователя, только основные данные.

# Как выглядят эти файлы?

```yaml
# equipments.yaml
version: v1
kind: EquipmentSet
unit: 
  name: kitchen
  subUnits:
    - name:  "плита"
      price: 30000
      mass:  50
      watts: 10000
      count: 2
    - name:  "холодильник"
      price: 50000
      mass:  60
      watts: 2000
      count: 1
    - name:  "стол"
      count: 3
      price: 3000
      watts: 0
      mass:  5
    - name:  "утварь"
      count: 5
      price: 2000
      watts: 500
      mass:  5
```

Сначала описывается версия API, для которого эта модель подходит. На данный момент пока готовится версия `v1`. 

Далее в поле `kind` идет название модели, строго согласно названиям моделей Django.

В поле `unit` должно находиться всё то, что относится к конкретной группе моделей (в случае примера - `kitchen`, то есть кухня).

Если необходимо вписать название не на английском языке - пишите в кавычках.

Если в модели поле объявлено со значением по дефолту, то его не обязательно проставлять - в это случае будет взято значение из дефолта модели.

В поле `subUnits` должны находиться все те модели, которые ссылаются ForeignKey-ами на данную модель.

- `EquipmentSet -> subUnit = Equipment`
- `WorkersSet   -> subUnit = Role`
- `AdsSet       -> subUnit = Ads`

и т.д.
