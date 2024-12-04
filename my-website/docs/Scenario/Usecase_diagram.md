# Диаграмма прецендентов

```plantuml

@startuml
skin rose
title "Use-case диаграмма"

"Сотрудник поддержки"
"Методист"
"Автор контента" 

usecase (Регистрация) as (reg)
usecase (Заполнение анкеты) as (ank)
usecase (Просмотр анкет) as (ank_view)
usecase (Общение в чате) as (chat)
usecase (Конференция) as (conf)
usecase (Просмотр ЛК) as (lk)
usecase (Публикация контента) as (publ)
usecase (Обращение в поддержку) as (help)
usecase (Модерация сообщений) as (mod)
usecase (Редактирование контента) as red_content

Пользователь -down-> reg
Пользователь -down-> ank
Пользователь -down-> lk
Пользователь -down-> chat
Пользователь -down-> conf
Пользователь -down-> help
Пользователь -down-> ank_view

"Сотрудник поддержки" -down-> help
"Сотрудник поддержки" -down-> mod
"Автор контента" -->publ
Методист -down->publ
Методист -down->red_content
"Автор контента" -down->red_content

ank .up.>reg: include
chat ..> conf: extend
ank_view ..>ank: include
lk .-right-.> reg: include
mod .right.> help: extend
chat ..> ank_view: include
conf .left.> ank_view: include
red_content .down.> publ:extend
@enduml

