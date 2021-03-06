В проекте использовано два контейнера - vector и map, и реализовано три класса: класс User, класс Chatpool и класс Userpool. Класс User нужен для хранения данных для логина (никнейм и пароль). 
Класс Userpool - это вектор, в который добавляются объекты класса User. Userpool может, соответственно, совершать некоторые простые операции с объектами: 
проверять никнейм и пароль для логина, добавлять нового пользователя и выводить список всех пользователей. 
Класс Chatpool - это класс, у объектов которого есть вектор из словарей map и ряд методов для действий с этим вектором. Такой объект с названием chatsinmap 
создаётся при запуске программы.

Когда пользователь в меню выбирает опцию 2 для создания нового пользователя, создаётся новый объект с именем пользователя. 
В полях этого объекта хранится никнейм и пароль пользователя. 
Далее пользователь может написать, кому отправить сообщение. 
Затем написать само сообщение. После этого запускается метод sendmessage. Сначала будет создано полное сообщение, которое будет состоять из
имени отправителя, двоеточия и самого сообщения. 
Затем метод проверит, отправлено ли сообщение для всех. Если да, то цикл for пройдётся по всему chatpool_vect, посчитает размер каждого словаря в этом векторе,
и в каждый словарь добавит новую запись, где first - это порядковый номер сообщения в словаре, а second - полное сообщение. 
(Порядковый номер сообщения в словаре нигде не используется, (разве что для упорядочивания сообщений в самом словаре), 
просто мне хотелось поработать именно с map).

Если же сообщение не для всех, с помощью метода checkmap будет проверка, есть ли уже переписка с конкретным адресатом. 

Когда сообщение отправляется адресату в первый раз, то метод sendmessage создаёт новый словарь с именем mapname и в первую строку записывает туда идентификатор
словаря, состоящий из имени получателя, подчёркивания, отправителя. Этот идентификатор записывается как second, в качестве first указывается ноль.
Таким образом checkmap проходит по всем словарям в векторе, смотрит первую строку и проверяет есть ли там second равный "отправитель_получатель" или 
"получатель_отправитель". После чего происходит либо запись сообщения в существующий словарь (уже имеющуюся переписку), либо создаётся новый словарь с 
перепиской и сообщение записывается туда.

Затем снова выводится главное меню. Когда пользователь в меню выбирает опцию 1 для отправки личных сообщений, метод Userpool'a 
проверяет наличие такого никнейма и пароля. Если объект с таким никнеймом и паролем есть, логин подтверждается и пользователь 
может написать адресата - никнейм или all для отправки сообщения всем. Метод showmap объекта chatsinmap пройдёт по словарям в 
векторе chatpool_vect и выведет сообщения, которые залогиненный пользователь и адресат друг другу отправляли. Сообщения 
отправленные всем от других пользователей тоже будут здесь выведены. Затем можно ввести сообщение. 

Нажав 3, можно посмотреть никнеймы всех существующих пользователей.

Класс chatpool содержит публичный вектор chatpool_vect из словарей map<int, string>.
Имеет следующие методы: void showmap(string receiver, string nickname)- для показа переписки с конкретным пользователем; 
int checkmap(string receiver, string nickname) - проверяет, существует ли переписка пользователя nickname с конкретный адресатом (receiver).
void sendmessage(string receiver, string nickname, string message) - метод для отправки сообщения. Этот метод запишет сообщение в соответствующий словарь.

Класс User содержит два приватных поля - nickname и password, а к ним - сеттеры и геттеры.

Класс Userpool содержит публично доступный вектор с объектами класса User и следующие методы: 
void addUser(User username) - добавить нового пользователя; int checkUser(string nickname, string password) - 
логин по никнейму и паролю; void showUsers()- вывод никнеймов всех существующих пользователей.
