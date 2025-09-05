# API Документация

# /api/auth/token-v2

### POST:
```
{
	"login": string,
	"password": string
}
```

### Response:
```
{
    "data": {
        "token": string,
        "accessToken": string
    }
}
```

# /api/tasks/create

### POST:
```
{
	"subcatId": integer, # ID категории куда ставить задачу
	"taskText": string, # Текст задачи
	"orderedTime": datetime, # Время постановки задачи
	"performerIds": [ПУСТОЕ], # ID исполнителей
	"priorityId": 1, # Приоритет задачи
	"userToMakeOwnerId": ПУСТОЕ, # ID владельца задачи
	"subscriberIds": [ПУСТОЕ], # ID подписчиков
	"notifyIds": [ПУСТОЕ], # ID кому прислать уведомления
	"initiatorUserId": 2389, # ID инициатора
	"taskStartTime": datetime, # Время начала задачи
	"userComment": "ПУСТОЕ", # Комментарий к задаче
	"extParams": [
		{
			"id": integer, # ID параметра
			"value": string # Значение параметра
		}
	] # Дополнительные параметры задачи
}
```

### Response:
```
{
	"data": {
		"performerId": null,
		"linkId": null,
		"value": integer,
		"massResult": null
	}
}
```

