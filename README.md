Сгенерировать персональный токен (добавить его в переменные коллекции)
СЩЗДАНИЕ Issues1 https://api.github.com/repos/SKsesha/Attest/issues ( 1. Выбрать Метод POST 2. Добавить Headers "Accept: application/vnd.github+json" \ "Authorization: Bearer <YOUR-TOKEN>" \ "X-GitHub-Api-Version: 2022-11-28" \
добавить тело запроса {"title":"Issue 1","body":"Something went wrong.","assignees":["SKsesha"],"labels":["bug"]} "confirmPassword": "Q234erdfg!"} добавить скрипты на проверку статус-кода, 
а также временные переменные var key = "IssuesURL"
var value = pm.response.json().url
pm.collectionVariables.set(key, value); выполнить запрос)
ПОЛУЧЕНИЕ СПИСКА ISSUES https://api.github.com/issues (( 1. Выбрать Метод GET 2. Добавить Headers "Accept: application/vnd.github+json" \ "Authorization: Bearer <YOUR-TOKEN>" \ "X-GitHub-Api-Version: 2022-11-28" \
добавить скрипты на проверку статус-кода, выполнить запрос)
ИЗМЕНЕНИЕ НАЗВАНИЯ Issues 1 на issues2 https://api.github.com/repos/SKsesha/Attest/issues/"IssuesURL" ( 1. Выбрать Метод PATCH 2. Добавить Headers "Accept: application/vnd.github+json" \ "Authorization: Bearer <YOUR-TOKEN>" \ "X-GitHub-Api-Version: 2022-11-28" \
добавить тело запроса {"title":"Issue 2","body":"Something went wrong.","assignees":["SKsesha"],"labels":["bug"]} добавить скрипты на проверку статус-кода, 
а также временные переменные var key = "nodeID"
var value = pm.response.json().node_id
pm.collectionVariables.set(key, value); выполнить запрос
УДАЛЕНИЕ ISSUES https://api.github.com/graphql, используется язык запросов GRAPHQL, т.к. через REST API удалить ISSUES нет возможности (согласно документации API)
( 1. Выбрать Метод POST 2. Добавить Headers "Accept: application/vnd.github+json" \ "Authorization: Bearer <YOUR-TOKEN>" \ "X-GitHub-Api-Version: 2022-11-28" \
добавить тело запроса mutation ($issueId:ID!){deleteIssue (input:{issueId:$issueId}){clientMutationId}}
добавить временную переменную с предыдущего запроса {GRAPHQL VARIABLES   "issueId":"{{nodeID}}"}
добавить скрипты на проверку статус-кода,  выполнить запрос)
