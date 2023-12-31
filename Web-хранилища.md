### *Что такое Local Storage и Session Storage?* 

**Local Storage** - это механизм хранения данных в браузере, который позволяет сохранять данные на компьютере пользователя.   
Это может быть полезно для сохранения настроек пользователя, кэширования данных или хранения данных о состоянии приложения.  
Local Storage обычно используется вместе с JavaScript и позволяет сохранять данные в виде пар ключ-значение.  
Данные сохраняются в браузере и могут быть получены и использованы в любой момент, пока пользователь не очистит кэш или не удалит данные вручную.  

**Session Storage** - это механизм хранения данных в браузере, который позволяет сохранять данные на время сессии.   
Это означает, что данные будут доступны только в течение одной сессии работы с браузером и будут удалены после закрытия вкладки или окна браузера.   
Session Storage также используется для хранения данных в виде пар ключ-значение и может быть полезен для сохранения состояния приложения или временных данных.     

### *В чём заключается их различие?*
В отличие от Local Storage, Session Storage не сохраняет данные на длительный период времени и не доступен в других вкладках или окнах браузера.    

### *Какие существуют основные методы взаимодействия с localStorage и sessionStorage через консоль в браузере?*

**setItem(key, value)** - добавляет пару ключ-значение в localStorage или sessionStorage.  

**getItem(key)** - получает значение по ключу из localStorage или sessionStorage.  

**removeItem(key)** - удаляет пару ключ-значение из localStorage или sessionStorage по ключу.  

**clear()** - удаляет все данные из localStorage или sessionStorage.  

**key(index)** - получает ключ по индексу из localStorage или sessionStorage.    


### *Как производить сохранение, получение, удаление данных, очистку хранилища?*   

**Для сохранения данных** в localStorage или sessionStorage используется метод setItem(key, value), где key - ключ,   
по которому будет производиться доступ к значению, а value - сохраняемое значение.   
***Пример:***

localStorage.setItem('name', 'Julia');

**Для получения значения** из localStorage или sessionStorage используется метод getItem(key), где key - ключ,   
по которому будет производиться доступ к значению.  
***Пример:***

var name = localStorage.getItem('name');

**Для удаления данных** из localStorage или sessionStorage используется метод removeItem(key), где key - ключ,   
по которому будет производиться удаление пары ключ-значение.   
***Пример:***

localStorage.removeItem('name');

**Для очистки всех данных** из localStorage или sessionStorage используется метод clear().   
***Пример:***

localStorage.clear()  
  
**Для получения ключа по индексу** из localStorage или sessionStorage используется метод key(index), где index - индекс ключа в хранилище.   
***Пример:***

var key = localStorage.key(0); // получаем первый ключ из localStorage
 

### *Что такое IndexedDB?*     

**IndexedDB** - это низкоуровневая API для хранения больших объемов структурированных данных в браузере. Она позволяет приложениям веб-браузера сохранять данные на клиентской стороне и обрабатывать их без подключения к серверу.   
IndexedDB позволяет создавать объектные хранилища, которые могут содержать ключи и значения, а также индексы для быстрого доступа к данным.   
Она поддерживается всеми современными браузерами, включая Chrome, Firefox, Safari и Edge.   

### *Чем этот вид хранилища отличается от описанных выше?*

IndexedDB отличается от других видов хранилищ тем, что она предназначена для хранения больших объемов структурированных данных на клиентской стороне.   Она позволяет создавать объектные хранилища и индексы для быстрого доступа к данным. В отличие от LocalStorage, IndexedDB позволяет хранить более сложные данные, такие как объекты и массивы, а также обрабатывать их более эффективно. Кроме того, IndexedDB поддерживает транзакции, что позволяет обеспечить целостность данных и избежать потери информации при неожиданном завершении работы приложения.    

### *Как можно просмотреть содержимое всех веб-хранилищ в браузере?*

В большинстве браузеров можно воспользоваться инструментами разработчика, чтобы просмотреть содержимое всех веб-хранилищ.  
В **Google Chrome** нужно открыть меню "Дополнительные инструменты" -> "Инструменты разработчика" и перейти на вкладку "Application".   
Здесь можно просмотреть содержимое LocalStorage, SessionStorage, IndexedDB и других типов хранилищ.   
В **Firefox нужно** открыть меню "Другие инструменты" -> "Инструменты веб-разработчика" -> "Хранилище".   
В **Safari** нужно выбрать меню "Develop" -> "Show Web Inspector" и перейти на вкладку "Storage".




