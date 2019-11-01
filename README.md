# botapitamtam
Попытка создать набор простых инструментов для написания ботов на базе API мессенджера TamTam. Набор содержит базовый функционал взаимодействия бота с пользователями и предназначен для начинающих программистов. Синтаксис методов позволяет легко их модифицировать или создавать на их базе новые методы используя официальную документацию https://dev.tamtam.chat/ .

Примеры реализации ботов с использованем библиотеки:   

https://github.com/registriren/filelink

https://github.com/registriren/yatranslate
  

Библиотека находится в стадии разработки, поэтому возможны изменения синтаксиса, которые приведут к неработоспособности вашего кода, проверяйте перед применением изменений на своей системе.

Чат для обсуждения вопросов, связанных с работой библиотеки https://tt.me/botapitamtam

Принцип взаимодействия с библиотекой:
- 
1. Методы, которые начинаются с *get_* получают события, произошедшие с ботом (написанные или пересланные сообщения, результат нажатия кнопок, вложения и т.д.).
2. Методы, которые начинаются с *send_* формируют события в боте (отправляют сообщения, генерируют кнопки и т.д.).
3. Методы не имеющие указанные "префиксы" позволяют удалять, изменять сообщения, либо являются вспомогательными.
4. В основном цикле Вашей программы осуществляем запрос происходящих с ботом событий методом [get_updates()](doc/get_updates.md). Результат помещаем в переменную, например [upd = get_updates()](doc/get_updates.md).
5. Результат работы сформированных вами событий так же можно поместить в переменную, например [upd = send_message(text, chat_id)](doc/send_message.md).
6. Для получения "тела" события, которое необходимо обработать, передаем переменную *upd* выбранному методу *get_* , например [get_text(upd)](doc/get_text.md), работаем с результатом. 
7. Если запрошенное событие не произошло в ответ получим *None*.
8. В зависимости от интенсивности событий и частоты запросов на получение обновлений, [get_updates()](doc/get_updates.md) может возвращать несколько событий списком, в этом случае потребуется добавить еще один цикл для обработки этого списка, пример подобной реализации: https://github.com/registriren/yatranslate
9. Для работы с библиотекой поместите файл [botapitamtam.py](botapitamtam.py) в каталог с вашим кодом. Для удобного использования библиотеки во многих ботах с возможностью получения обновлений необходимо клонировать репозиторий в отдельный каталог
(*git clone https://github.com/registriren/botapitamtam*), а символьную ссылку на файл [botapitamtam.py](botapitamtam.py) разместить в каталогах с вашими ботами.

## Описание методов (в разработке, смотрите в основном коде):
- [attach_audio](doc/attach_audio.md) - готовит аудио к совместной отправке с другим контентом.
- [attach_buttons](doc/attach_buttons.md) - готовит кнопки к совместной отправке с другим контентом.
- [attach_file](doc/attach_file.md) - готовит файл к совместной отправке с другим контентом.
- [attach_image](doc/attach_image.md) - готовит изображения к совместной отправке с другим контентом.
- [attach_image_url](doc/attach_image_url.md) - готовит изображения (по их URL) к совместной отправке с другим контентом.
- [attach_video](doc/attach_video.md) - готовит видео к совместной отправке с другим контентом.
- [add_members](doc/add_members.md) - добавляет пользователя в чат.
- [delete_message](doc/delete_message.md) - удаляет сообщение (контент) по его идентификатору (message_id).
- [edit_bot_info](doc/edit_bot_info.md) - редактирует информацию текущего бота.
- [edit_chat_info](doc/edit_chat_info.md) - редактирует информацию чата.
- [edit_content](doc/edit_content.md) - изменяет контент по его идентификатору и сформированному аттач.
- [get_callback_id](doc/get_callback_id.md) - получает значение callback_id нажатой кнопки.
- [get_subscriptions](doc/get_subscriptions.md) - возвращает список подписок.
- [get_bot_info](doc/get_bot_info.md) - получает информацию текущего бота.
- [get_chat](doc/get_chat.md) - получает информацию текущего чата.
- [get_all_chats](doc/get_all_chats.md) - получает информацию о чатах, в которых участвовал бот.
- [get_chat_admins](doc/get_chat_admins.md) - получает информацию о администраторах чата.
- [get_chat_membership](doc/get_chat_membership.md) - получает информацию о членстве в чате для текущего бота.
- [get_chat_id](doc/get_chat_id.md) - получает идентификатор чата (диалога) в которм происходит взаимодействие с ботом.
- [get_link_chat_id](doc/get_link_chat_id.md) - получает идентификатор чата пересланного сообщения.
- [get_link_name](doc/get_link_name.md) - получает имя пользователя пересланного сообщения.
- [get_link_user_id](doc/get_link_user_id.md) - получает идентификатор пользователя пересланного сообщения.
- [get_marker](doc/get_marker.md) - получает маркер (порядковый номер) следующего события.
- [get_members](doc/get_members.md) - получает members.
- [get_message_id](doc/get_message_id.md) - получает идентификатор сообщения.
- [get_name](doc/get_name.md) - получает имя пользователя.
- [get_payload](doc/get_payload.md) - получает payload (присвоенное значение) нажатой кнопки.
- [get_text](doc/get_text.md) - получает значение поля text полученного сообщения (события) .
- [get_update_type](doc/get_update_type.md) - получает тип события, произошедшего в боте.
- [get_updates](doc/get_updates.md) - получение событий, произошедших в боте.
- [get_url](doc/get_url.md) - получает значение поля URL полученного сообщения (события).  
- [get_user_id](doc/get_user_id.md) - получает идентификатор пользователя полученного сообщения.
- [leave_chat](doc/leave_chat.md) - удаляет бота из текущего чата.
- [remove_member](doc/remove_member.md) - удаляет пользователя из чата.
- [subscribes](doc/subscribes.md) - подписывается на URL для получения обновлений.
- [send_answer_callback](doc/send_answer_callback.md) - отправляет уведомление (реакцию) после нажатия кнопки.
- [send_audio](doc/send_audio.md) - отправляет аудиофайл с преобразованием в формат ТамТам.
- [send_buttons](doc/send_buttons.md) - формирует кнопки.
- [send_content](doc/send_content.md) - отправляет любой контент по сформированному attachments.
- [send_file](doc/send_file.md) - отправляет файл.
- [send_forward_message](doc/send_forward_message.md) - пересылает сообщение по его идентификатору.
- [send_mark_seen](doc/send_mark_seen.md) - отправляет уведомление о прочтении ботом сообщения.
- [send_message](doc/send_message.md) - отправляет текстовое сообщение.
- [send_photo](doc/send_photo.md) - отправляет изображение (несколько изображений) из локального файла.
- [send_photo_url](doc/send_photo_url.md) - отправляет изображение из URL.
- [send_reply_message](doc/send_reply_message.md) - формирует ответ на сообщение.
- [send_sending_audio](doc/send_sending_audio.md) - отправляет уведомление об отправке аудио.
- [send_sending_file](doc/send_sending_file.md) - отправляет уведомление об отправке файла.
- [send_sending_photo](doc/send_sending_photo.md) - отправляет уведомление об отправке изображения.
- [send_sending_video](doc/send_sending_video.md) - отправляет уведомление об отправке видео.
- [send_typing_on](doc/send_typing_on.md) - отправляет уведомление о печати сообщения.
- [send_video](doc/send_video.md) - отправляет видео.
- [token_upload_content](doc/token_upload_content.md) - вспомогательная функция получения токена загружаемого изображения.
- [unsubscribe](doc/unsubscribe.md) - отписывается от (URL).
- [upload_url](doc/upload_url.md) - вспомогательная функция получения URL загружаемого изображения.
