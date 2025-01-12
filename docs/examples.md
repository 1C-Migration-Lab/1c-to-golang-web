# Примеры преобразования

## XML в JSON

### Исходный XML (1C)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<MetaDataObject xmlns="http://v8.1c.ru/8.3/MDClasses">
  <Document uuid="c7e0568e-21c9-4c94-a525-cc7b4d6763e9">
    <Properties>
      <Name>ЗаказПокупателя</Name>
      <Synonym>
        <v8:item>
          <v8:lang>ru</v8:lang>
          <v8:content>Заказ покупателя</v8:content>
        </v8:item>
      </Synonym>
      <Comment/>
    </Properties>
    <TabularSections uuid="c7e0568e-21c9-4c94-a525-cc7b4d6763e9">
      <Properties>
        <Name>Товары</Name>
        <Synonym>
          <v8:item>
            <v8:lang>ru</v8:lang>
            <v8:content>Товары</v8:content>
          </v8:item>
        </Synonym>
      </Properties>
    </TabularSections>
  </Document>
</MetaDataObject>
```

### Промежуточное представление (JSON)
```json
{
  "type": "Document",
  "name": "ЗаказПокупателя",
  "uuid": "c7e0568e-21c9-4c94-a525-cc7b4d6763e9",
  "synonym": {
    "ru": "Заказ покупателя"
  },
  "tabularSections": [
    {
      "name": "Товары",
      "synonym": {
        "ru": "Товары"
      }
    }
  ]
}
```

## Go код

### Сгенерированные структуры
```go
type ЗаказПокупателя struct {
    ID          string    `json:"id"`
    Номер       string    `json:"номер"`
    Дата        time.Time `json:"дата"`
    Товары      []ТоварыЗаказа `json:"товары"`
}

type ТоварыЗаказа struct {
    Номенклатура string  `json:"номенклатура"`
    Количество   float64 `json:"количество"`
    Цена         float64 `json:"цена"`
    Сумма        float64 `json:"сумма"`
}
```

## HTML форма

### Сгенерированная форма
```html
<form id="customerOrder" class="form">
    <div class="form-group">
        <label for="number">Номер</label>
        <input type="text" id="number" name="number" class="form-control">
    </div>
    <div class="form-group">
        <label for="date">Дата</label>
        <input type="datetime-local" id="date" name="date" class="form-control">
    </div>
    
    <table id="items" class="table">
        <thead>
            <tr>
                <th>Номенклатура</th>
                <th>Количество</th>
                <th>Цена</th>
                <th>Сумма</th>
            </tr>
        </thead>
        <tbody>
            <!-- Динамические строки -->
        </tbody>
    </table>
</form>
