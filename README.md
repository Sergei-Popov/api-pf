# API Документация

# /api/auth/token-v2

## POST:

```
{
	"login": string,
	"password": string
}
```

## Response:

```
{
    "data": {
        "token": string,
        "accessToken": string
    }
}
```

# /api/tasks/create

## Headers:

```
1formaauth: <token>
```

## POST:

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

## Response:

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

# /app/v1.0/api/subcategory/{subcatId}/states

## Headers:

```
1formaauth: <token>
```

## GET:

No body required.

## Response:

```
{
  "data": [
    {
      "id": 0, # ID состояния
      "name": "string", # Название состояния
      "isActive": true # Активно ли состояние
    }
  ],
  "total": 0, # Общее количество состояний
  "aggregates": "string"
}
```

# /api/admin/subcat/extparams (Получить доп. параметры категории)

## Headers:

```
1formaauth: <token>
```

## Parameters:
- subcatId: integer (ID категории)

## GET:
No body required.

## Response:
```
{
  "data": [
    {
      "id": 0,
      "extParamId": 0,
      "extParamName": "string",
      "extParamType": "string",
      "isRequired": true,
      "toolTip": "string",
      "isReadonly": true,
      "newTaskMode": {
        "id": "string",
        "name": "string"
      },
      "accessControl": {
        "id": "string",
        "name": "string"
      },
      "regExp": "string",
      "subcatOrder": 0,
      "stateControl": true,
      "smartAccessControl": true,
      "syncToParent": true,
      "hidden": true,
      "hideIfEmpty": true,
      "syncToChild": true,
      "defaultValue": "string",
      "notifyOnChange": true,
      "allowHistory": true,
      "allowEditHistory": true,
      "changeWithComment": true,
      "defaultValueSmartExpressionId": 0,
      "targetExtParamId": 0,
      "extParamBlock": {
        "id": "string",
        "name": "string"
      },
      "extParamBlockLinks": [
        {
          "blockId": 0,
          "extParamId": 0,
          "order": 0,
          "colspan": 0,
          "isHiddenOnNewTaskForm": true,
          "isHiddenOnMainTaskForm": true,
          "blockName": "string",
          "extParamName": "string"
        }
      ],
      "validatorId": 0,
      "colspan": 0,
      "maxLength": 0,
      "encrypt": true,
      "extParamInSubcatName": "string",
      "extParamInSubcatId": 0,
      "useInSearch": true,
      "isValidatorUsed": true,
      "supportsChangeWithComment": true,
      "defaultValueSmartExpressionName": "string",
      "taskEntityPermissionControl": true,
      "askSaveConfirm": true,
      "uniqueValues": true,
      "indexCreated": true,
      "entitySetId": 0,
      "changeWithCommentMode": {
        "id": "string",
        "name": "string"
      },
      "changeWithCommentSmartExpressionId": 0,
      "accessFunc": "string",
      "accessFuncBatch": "string",
      "accessFuncOnlyForWriteAccess": true,
      "isNotDenormalized": true,
      "extParamStateViews": [
        {
          "stateId": 0,
          "stateName": "string",
          "canEdit": true,
          "canRead": true
        }
      ],
      "smartAccessForExtParamInfos": [
        {
          "id": 0,
          "name": "string",
          "usersSmartExpressionId": 0,
          "canRead": true,
          "canWrite": true,
          "usersSmartExpressionName": "string",
          "subcatId": 0,
          "subcatName": "string",
          "triggerExtParamNames": "string",
          "triggerGroupNames": "string",
          "extParamId": 0,
          "extParamName": "string"
        }
      ],
      "extParamsInSubcatValidator": {
        "valdatorId": 0,
        "smartExpressionId": 0,
        "runOnSave": true,
        "runOnTaskCreated": true,
        "steps": [
          {
            "stepId": 0,
            "stepName": "string",
            "validatorId": 0
          }
        ],
        "customButtons": [
          {
            "buttonId": 0,
            "buttonName": "string",
            "validatorId": 0
          }
        ]
      },
      "extParamInSubcatPermissions": [
        {
          "extParamId": 0,
          "subcatId": 0,
          "groupId": 0,
          "groupName": "string",
          "canRead": true,
          "canWrite": true
        }
      ],
      "extParamTableSettingsInSubcatGroupPermissions": [
        {
          "extParamId": 0,
          "subcatId": 0,
          "columnId": 0,
          "groupId": 0,
          "groupName": "string",
          "canRead": true,
          "canWrite": true
        }
      ],
      "extParamTableSettingsInSubcatStatePermissions": [
        {
          "extParamId": 0,
          "subcatId": 0,
          "columnId": 0,
          "stateId": 0,
          "stateName": "string",
          "canRead": true,
          "canEdit": true
        }
      ],
      "extParamTableSettingsInSubcat": [
        {
          "columnId": 0,
          "extParamId": 0,
          "extParamInSubcatId": 0,
          "name": "string",
          "type": "Text",
          "stateAccessControlEnabled": true,
          "groupAccessControlMode": "BYTASK"
        }
      ],
      "addNewRowsToTableDpCheckSmartExpressionId": 0,
      "removeRowsFromTableDpCheckSmartExpressionId": 0,
      "addNewRowsToTableDpCheckSmartExpressionName": "string",
      "removeRowsFromTableDpCheckSmartExpressionName": "string",
      "filterRowsInTableDpDenied": true,
      "module": {
        "id": 0,
        "name": "string"
      },
      "dontCopySourceTaskValue": true
    }
  ],
  "errors": [
    {
      "errorType": "TestPurposes",
      "message": "string",
      "exceptionTitle": "string"
    }
  ]
}
```