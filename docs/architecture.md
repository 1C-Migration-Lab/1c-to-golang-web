# Архитектура проекта

## Общий пайплайн

```mermaid
graph TD
    A[1C XML Конфигурация] --> B[Parser]
    B --> C[Промежуточное представление IR]
    C --> D[Generator]
    D --> E[Go Backend]
    D --> F[Web Frontend]
    
    subgraph Parser
        B1[XML Parser] --> B2[BSL Parser]
        B2 --> B3[IR Builder]
    end
    
    subgraph Generator
        D1[Go Structures] --> D2[REST API]
        D3[HTML Forms] --> D4[JS Controllers]
    end
```

## Компоненты системы

### Parser
- Чтение XML конфигурации 1С
- Извлечение метаданных (справочники, документы, реквизиты)
- Парсинг BSL кода (модули, процедуры)
- Формирование промежуточного представления (IR)

### Generator
- Генерация Go структур для справочников и документов
- Создание REST API эндпоинтов
- Генерация HTML форм
- Генерация JavaScript контроллеров

### Backend (Go)
- REST API для работы с данными
- Бизнес-логика (на основе правил из 1С)
- Работа с БД

### Frontend (Web)
- HTML формы для редактирования данных
- JavaScript для обработки событий
- Взаимодействие с REST API
