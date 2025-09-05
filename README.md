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

# /api/storage/subcategories/{subcatId}

## Headers:
```
1formaauth: <token>
```

## GET:
No body required.

## Response:

### Можно получить все ДП и их значения:
```
"extParams": [
  {
    "subcatId": 0,
    "extParamId": 0,
    "extParamName": "string",
    "isRequired": true,
    "newTask": true,
    "subcatOrder": 0,
    "isReadonly": true,
    "accessControl": 0,
    "syncToParent": true,
    "syncToChild": true,
    "stateControl": true,
    "newTaskMode": 0,
    "defaultValue": "string",
    "notifyOnChange": true,
    "allowEditHistory": true,
    "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "changeWithComment": true,
    "hidden": true,
    "defaultValueSmartExpressionID": 0,
    "blocksLinks": [
      {
        "blockId": 0,
        "extParamId": 0,
        "subcatId": 0,
        "order": 0,
        "colspan": 0,
        "isHiddenOnNewTaskForm": true,
        "isHiddenOnMainTaskForm": true
      }
    ],
    "validatorId": 0,
    "colspan": 0,
    "maxLength": 0,
    "allowHistory": true,
    "dontCopySourceTaskValue": true,
    "smartAccessControl": true,
    "encrypt": true,
    "extParamType": "string",
    "extParam": {
      "id": 0,
      "version": 0,
      "name": "string",
      "type": "Text",
      "toolTip": "string",
      "regExp": "string",
      "regExpErrorMessage": "string",
      "localizable": true,
      "settings": {}
    }
  }
]
```

### Список всех настроек категории:
```
{
  "data": {
    "id": 0,
    "version": 0,
    "subcategory": {
      "id": 0,
      "version": 0,
      "subcatTypeID": 0,
      "enableRecurrence": true,
      "displayEmptyAttachments": true,
      "description": "string",
      "details": "string",
      "categoryId": 0,
      "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "entity": "string",
      "consisImplementOptions": {
        "consisImplementEnable": true,
        "consisImplementDefaultSubcat": 0,
        "consisImplementRestricSubcats": "string",
        "consisImplementDisableAlerts": true,
        "consisImplementFinishMainTask": true
      },
      "resourceManagementOptions": {
        "resourceManagementEnabled": true,
        "planningMode": "FixLength",
        "needAcceptPlannedResources": true,
        "needAcceptPlannedPerformer": true,
        "performerDefaultResourceId": 0,
        "syncPlans": true,
        "resourcesVisibilitySmartExpressionId": 0,
        "disablePlansAutocalculation": true,
        "adjustAbsoultePlanToManual": true
      },
      "automationOptions": {
        "newTaskSPName": "string",
        "saveTaskSPName": "string",
        "stepSignsFromSysRobot": true,
        "defaultCopySubscribers": true,
        "subtasksOnly": true,
        "commentTreeSubTasks": true,
        "isProlongOrderedTime": true,
        "clearPerformersOnCopyMove": true,
        "rejectSubTasksWhenRejected": true,
        "createSystemFileVersionsOnSignatureSign": true,
        "mainRouteStepsAvailableSmartExpressionId": 0
      },
      "taskParticipantsOptions": {
        "doNotSelectOwner": true,
        "restrictPerformerRemove": true,
        "restrictedSubscribtion": true,
        "allowGroupSubcription": true,
        "performerMode": "Allow",
        "delegateTaskConfirmSignatureId": 0,
        "delegateTaskConfirmSignatureSmartExpressionId": 0,
        "taskOwnerChangeConfirmSignatureId": 0,
        "taskOwnerChangeSmartExpressionId": 0,
        "taskHelpersTimeVisible": true,
        "notifyOwnerOnWorkAmountExcess": true,
        "notifyAboutOverdueTaskOnlyResponsibleGroup": true,
        "taskHelpersGradeMode": "Disabled",
        "taskHelperGradeNecessary": true,
        "canDeleteLastPerformer": true,
        "multiFinishAction": "DoNothing",
        "helpersAction": "AddAsPerformer",
        "forwardCommentsToAllHelpers": true,
        "specialUsersSmartExpressionId": 0,
        "specialUsersTitle": "string",
        "allowSetSinglePerformer": true
      },
      "textOptions": {
        "fixTaskText": true,
        "allowNullTask": true,
        "disableTaskDescription": true,
        "allowHTMLTaskText": true,
        "allowImagesInTaskText": true,
        "showTasksTextAsHtml": true,
        "ownerCanChangeText": true,
        "adMinCanEditText": true,
        "subscriberCanEditText": true,
        "anyoneCanEditText": true,
        "enableComments": true,
        "enableCommentsEdit": true,
        "denyEnterComments": true,
        "allowHTMLCommentsText": true,
        "notAllowCommentWithoutRecipients": true,
        "hideSystemComments": true,
        "denyPostCommentsInClosedTasks": true,
        "autoMarkQuestions": true,
        "showAllCommentsFromTaskTreeByDefault": true,
        "forRootTasks": true,
        "showCommentAttachments": true,
        "taskTextSearchType": "Framing",
        "tasksEncryptionMode": "None",
        "commentReplacerId": 0,
        "taskTextReplacerId": 0,
        "taskTextMaxLength": 0
      },
      "dueOptions": {
        "defaultDuration": 0,
        "defaultDurationMode": 0,
        "minSrok": 0,
        "minSrokMode": 0,
        "recommendedDueDate": 0,
        "recommendedDueDateMode": 0,
        "allowChangeDuration": true,
        "allowSetTaskStartTime": true,
        "fillNewTaskStartTimeWithCreatedDate": true,
        "allowSetTimeParamsInPast": true,
        "allowStepsInOverdueTask": true,
        "allowChangePerformersInOverdueTask": true,
        "allowOrderedTimeOnlyInWorkPeriod": true,
        "allowOrderedTimeOnlyInWorkTime": true,
        "allowChangeTaskStartTimeInClosedTasks": true,
        "restrictDueDateEdit": true,
        "changeDueConfirmSignatureId": 0,
        "changeDueConfirmSignatureSmartExpressionId": 0,
        "notShowChangeDueDateCount": true,
        "orderedTimeCanBeLocked": true,
        "srokControl": 0,
        "smart25": true,
        "smart50": true,
        "smart75": true,
        "smart100": true
      },
      "viewAndPermissions": {
        "allowChangeTaskOwner": true,
        "allowChat": true,
        "allowPriority": true,
        "showTaskCountInTitle": true,
        "showAllTaskCountInTree": true,
        "showNewTaskCountInTree": true,
        "showOverdueTaskCountInTree": true,
        "showResources": true,
        "classicCalendar": true,
        "showTasksInTerminalStatusInCalendar": true,
        "showLoadingIndicator": true,
        "displaySubscribeDuringNewTask": true,
        "displayNotifyDuringNewTask": true,
        "displayTaskSubcategoryPath": true,
        "displayTaskId": true,
        "displayTaskState": true,
        "displayTaskStartDate": true,
        "displayTaskDelegateButton": true,
        "displayTaskChangeDueDateButton": true,
        "attachFilesPermission": "Allow",
        "newTaskFormTemplateID": 0,
        "newTaskFormTemplateIdSmartExpressionId": 0,
        "mainTaskFormTemplateID": 0,
        "mainTaskFormTemplateIdSmartExpressionId": 0,
        "mtfDefaultTemplateVisibilityMode": "Hidden",
        "mtfDefaultTemplateVisibilitySmartId": 0,
        "redirectFromNewTask": "string",
        "redirectFromGridHref": "string",
        "notLoadGridAndShowSearch": true,
        "useShortNewTaskView": true,
        "defaultViewType": "feed",
        "showPinToChatIcon": true,
        "allowNewTaskPriority": true,
        "allowNewTaskSeparate": true,
        "allowNewTaskRecurrenceSetup": true,
        "hideQuickCreateInEp": true,
        "hideCreateButtonInAllCategoryViews": true,
        "maxSumAttachmentSizeOnCreate": 0,
        "newStateId": 0
      },
      "sendButton": "string",
      "srokName": "string",
      "requireSubtaskFinish": true,
      "defaultText": "string",
      "forMailAdministrators": "string",
      "responsibleGroupID": 0,
      "newTaskMessage": "string",
      "chatTemplate": "string",
      "useChatTemplate": true,
      "customerID": 0,
      "forInvitations": true,
      "disableMail": true,
      "isDictionary": true,
      "reminderTextTemplate": "string",
      "perfOnCreateAssignedText": "string",
      "inviteTemplate": "string",
      "inactiveTaskWarningTime": 0,
      "extParamIDToWriteInSubjects": 0,
      "textToAppendToSubjects": "string",
      "taskHelperDefaultPlan": 0,
      "invidedUserGroupID": 0,
      "autoTaskTextTemplate": "string",
      "extUsersMailerFrom": "string",
      "extUsersMailerFromName": "string",
      "recipientsTitle": "string",
      "useEPTemplate": true,
      "epTemplate": "string",
      "enableSms": true,
      "taskStartTimeName": "string",
      "parentTaskDescriptionReference": "string",
      "forbidUploadFilesIntoClosedTasks": true,
      "notifyResponsibleStateChange": true,
      "groupToInformOnPlanTimeOverdueID": 0,
      "isPortal": true,
      "isNotice": true,
      "forbidMovingTasks": true,
      "memo": "string",
      "fullPath": "string",
      "docxTemplateProtectionLevel": 0,
      "fullPathIds": "string",
      "isForProjects": true,
      "isForProjectTasks": true,
      "projectTasksSubcatId": 0,
      "giveRightsOnlyToADGroups": true,
      "autoDeletePrevVersionsOfFiles": true,
      "allowSignatureRevoke": true,
      "allowSignatureRevokeByAcceptors": true,
      "taskHelpersPlanTimeMode": "Disabled",
      "projectPlannedSumEpId": 0,
      "projectFactSumEpId": 0,
      "projectCurrencyName": "string",
      "projectDefaultViewPreset": "Hours",
      "projectShortDateView": true,
      "additionalSyndicateLink": "string",
      "disableTasksMove": true,
      "addSubscriberText": "string",
      "addSubscribersText": "string",
      "oneFMainVisibilityMode": "ShowAll",
      "isSystemSubcat": true,
      "isResourceReservation": true,
      "isTasksLayoutSubcat": true,
      "isForSurveys": true,
      "taskLikesEnabled": true,
      "reactionsEnabled": true,
      "enableTaskViewsCounter": true,
      "enableTaskUserCommentsCounter": true,
      "allowSignatureRevokeByOwner": true,
      "allowSignatureRevokeByRequester": true,
      "mobileTemplateID": 0,
      "confidentialMode": "Disable",
      "showExtParamsAfterBlocks": true,
      "severalDecompositions": true,
      "isForProjectForceTasks": true,
      "mtfDefaultExtParamTableColumns": 0,
      "ntfDefaultExtParamTableColumns": 0,
      "extParamsBlocksColor": "string",
      "mobileTaskTemplateId": 0,
      "msOfficeInteractionSettingId": 0,
      "isCalendar": true,
      "tasksIsNotOverdue": true,
      "isSaveUsersSettingsForGrid": true,
      "isPinnedToChats": true,
      "disableTasksCopyFromSubcategory": true,
      "disableTasksCopyToSubcategory": true,
      "toolbarConfig": {
        "toolbarSave": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "refresh": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "subTasks": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "signatures": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "documents": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "taskMember": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "time": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "remFav": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "project": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "newGantt": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "allDecompositions": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "otherActions": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "vcActions": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        },
        "cardDisplayChangeMode": {
          "languageKey": "string",
          "show": true,
          "isAvailable": true,
          "child": [
            "string"
          ]
        }
      },
      "srokMode": "Required",
      "localizedDescriptionId": 0,
      "localizedEntityId": 0,
      "taskHelpersTimeMode": "Disabled",
      "isTechnicalWorksNow": true,
      "technicalWorksText": "string",
      "localizedTechnicalWorksTextId": 0,
      "notUseNewTaskForm": true,
      "allowPartialSurveyComplete": true,
      "instructionTaskId": 0,
      "additionalSettings": {
        "availableRepresentations": [
          "Grid"
        ],
        "defaultResourceDisplayScale": "Week",
        "availableResourceDisplayScales": [
          "Week"
        ],
        "defaultCalendarDisplayScale": "Month",
        "availableCalendarDisplayScales": [
          "Month"
        ]
      },
      "color": "string",
      "icon": "string",
      "surveyType": 0
    },
    "extParams": [
      {
        "subcatId": 0,
        "extParamId": 0,
        "extParamName": "string",
        "isRequired": true,
        "newTask": true,
        "subcatOrder": 0,
        "isReadonly": true,
        "accessControl": 0,
        "syncToParent": true,
        "syncToChild": true,
        "stateControl": true,
        "newTaskMode": 0,
        "defaultValue": "string",
        "notifyOnChange": true,
        "allowEditHistory": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "changeWithComment": true,
        "hidden": true,
        "defaultValueSmartExpressionID": 0,
        "blocksLinks": [
          {
            "blockId": 0,
            "extParamId": 0,
            "subcatId": 0,
            "order": 0,
            "colspan": 0,
            "isHiddenOnNewTaskForm": true,
            "isHiddenOnMainTaskForm": true
          }
        ],
        "validatorId": 0,
        "colspan": 0,
        "maxLength": 0,
        "allowHistory": true,
        "dontCopySourceTaskValue": true,
        "smartAccessControl": true,
        "encrypt": true,
        "extParamType": "string",
        "extParam": {
          "id": 0,
          "version": 0,
          "name": "string",
          "type": "Text",
          "toolTip": "string",
          "regExp": "string",
          "regExpErrorMessage": "string",
          "localizable": true,
          "settings": {}
        }
      }
    ],
    "stateRouteInSubcats": [
      {
        "stateID": 0,
        "stateNextID": 0,
        "actionID": 0,
        "ownerOnly": true,
        "userOnly": true,
        "subcatID": 0,
        "stepDescr": "string",
        "hiddenStep": true,
        "stepToolTip": "string",
        "autoPerformerSignatureID": 0,
        "autoperformerAssingAction": 0,
        "termMinutes": 0,
        "transparentApproval": true,
        "forceComment": true,
        "resetDueTime": true,
        "stepOwnerToolTip": "string",
        "stepUserToolTip": "string",
        "isButtonPresserAutoPerformer": true,
        "autoAssignCustomer": true,
        "cycleApproval": true,
        "disableMail": true,
        "autoPerformStepOnSubtasksClose": true,
        "onOverduePerformStepID": 0,
        "confirmText": "string",
        "termDateSourceExtParamID": 0,
        "requestDirectorSignatureOnReject": true,
        "forAdmin": true,
        "forViewver": true,
        "taskStartTimeAction": 0,
        "askPermissionToPerformTSTAction": true,
        "autoPerformerSourceExtParamID": 0,
        "isAutoPerfomedOnPostTask": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "storedProcedures": "string",
        "changeTaskText": true,
        "changeTaskTextTemplate": "string",
        "forPerfRight": true,
        "forAddRight": true,
        "forResponsiblePerformer": true,
        "notifyUsersInSubcat": true,
        "notifyUsersInSubcatText": "string",
        "notifyUsersInSubcatGroupID": 0,
        "actionsWithExtParams": 0,
        "visibilitySmartFilterID": 0,
        "disallowRevisionsOnSign": true,
        "doSetComplainted": true,
        "removeCommentsOnSignWhenEP": 0,
        "redirectUrlAfterStepSmartExpressionID": 0,
        "isMainRouteStep": true,
        "isMainRouteAvailable": true,
        "requireChangeDateBefore": true,
        "localizedStepDescrId": 0
      }
    ],
    "stepSubTasks": [
      {
        "stepId": 0,
        "subcatId": 0,
        "taskDescr": "string",
        "includeParentDescr": true,
        "isLinked": true,
        "copySubscribersFromParent": true,
        "fromWhom": 0,
        "assignToParentTaskOwner": true,
        "customerRoleToAssignID": 0,
        "copyPerformers": true,
        "copyOnlyResponsiblePerformer": true,
        "separateTaskForEachPerformer": true,
        "performersFromGroupID": 0,
        "orderedTimeMode": 0,
        "orderedTimeExtParam": 0,
        "copyAttachmentsFromParent": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "orderedTimeOffset": 0,
        "orderedTimeOffsetUnit": 0,
        "smartFilterID": 0
      }
    ],
    "stateRoutesSignatures": [
      {
        "id": 0,
        "stepId": 0,
        "signatureId": 0,
        "subcatId": 0,
        "isNecessarily": true,
        "isByPerformer": true,
        "signatureOrder": 0,
        "maxTimeToSign": 0,
        "isForMainAcceptor": true,
        "spName": "string",
        "reason": "string",
        "returnIfNotSignedStateId": 0,
        "canChangeSigRequestReason": true,
        "sigRequestReasonRequired": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "actionIfNotSigned": 0,
        "excludeAlreadySigned": true,
        "smartFilterId": 0,
        "requestReasonOnAccept": true,
        "isByResponsiblePerformer": true,
        "canBeEscalated": true,
        "timeToSignSmartId": 0,
        "escalateOnOverDue": true,
        "isOwnerSignature": true,
        "enabled": true,
        "reasonSmartId": 0,
        "splitForEachAcceptor": true,
        "acceptorsEvalutionBaseUser": 0,
        "baseUserSmartId": 0,
        "canBeDelegated": true,
        "isEds": true
      }
    ],
    "customButtons": [
      {
        "id": 0,
        "subcatId": 0,
        "name": "string",
        "memo": "string",
        "iconUrl": "string",
        "isVisible": true,
        "actionsPackId": 0,
        "jsExpression": "string",
        "actionId": 0,
        "forOwner": true,
        "forPerformer": true,
        "forResponsiblePerformer": true,
        "forAdmin": true,
        "forAddRight": true,
        "forViewer": true,
        "visibilitySmartFilterId": 0,
        "urlSmartExpressionId": 0,
        "redirectActionTypeId": "NotSet",
        "catSmartExpressionId": 0,
        "subcatSmartExpressionId": 0,
        "taskSmartExpressionId": 0,
        "taskSourceSmartExpressionId": 0,
        "sourceTaskSmartExpressionId": 0,
        "hideOnVisibilitySmartFilter": true,
        "disabledReasonSmartExpressionId": 0,
        "disabledReason": "string",
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "orderId": 0,
        "urlLink": "string",
        "urlNewTaskSubcategoryId": 0,
        "urlNewTaskTaskId": 0,
        "urlNewTaskMakeSubtask": true,
        "urlNewTaskMakeLinked": true,
        "urlTaskFormTaskId": 0,
        "urlSubcategoryId": 0,
        "urlCategoryId": 0,
        "openLinkTarget": "CurrentWindow",
        "urlTaskDataSourceId": 0,
        "urlSourceType": "Fix",
        "urlNewTaskSubcategorySourceType": "Fix",
        "urlNewTaskTaskSourceType": "Fix",
        "urlNewTaskSubtaskSourceType": "Fix",
        "urlNewTaskLinkedSourceType": "Fix",
        "urlTaskFormSourceType": "Fix",
        "urlCategorySourceType": "Fix",
        "urlSubcategorySourceType": "Fix",
        "urlTaskDataSourceSourceType": "Fix"
      }
    ],
    "extParamBlocks": [
      {
        "id": 0,
        "name": "string",
        "subcatId": 0,
        "canFold": true,
        "defaultMinimized": true,
        "defaultBlock": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "order": 0,
        "color": "string",
        "localizedNameId": 0,
        "blocksLinks": [
          {
            "blockId": 0,
            "extParamId": 0,
            "subcatId": 0,
            "order": 0,
            "colspan": 0,
            "isHiddenOnNewTaskForm": true,
            "isHiddenOnMainTaskForm": true
          }
        ]
      }
    ],
    "extParamBlocksGroups": [
      {
        "id": 0,
        "name": "string",
        "subcatId": 0,
        "canFold": true,
        "defaultMinimized": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "order": 0,
        "localizedNameId": 0
      }
    ],
    "subcategoryIncludes": [
      {
        "id": 0,
        "name": "string",
        "subcatId": 0,
        "includeId": 0,
        "useForMtf": true,
        "useForNewTask": true,
        "includeType": "None",
        "includeContentType": "Js"
      }
    ],
    "notes": [
      {
        "id": 0,
        "subcatId": 0,
        "noteTitle": "string",
        "note": "string",
        "isInNewTask": true,
        "inInTask": true,
        "isInTasksGrid": true,
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
      }
    ],
    "stateHints": [
      {
        "id": 0,
        "stateId": 0,
        "subcatId": 0,
        "text": "string",
        "guid": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
      }
    ],
    "extraFormTemplates": [
      {
        "name": "string",
        "templateId": 0,
        "action": "Download",
        "extParamId": 0,
        "protect": "None"
      }
    ]
  },
  "errors": [
    {
      "errorType": "TestPurposes",
      "message": "string",
      "exceptionTitle": "string"
    }
  ]
}
```

