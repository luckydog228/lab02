# lab02
Part1
1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).

https://github.com/luckydog228/lab02.git


2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
```
$ echo "# lab02" >> README.md
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git branch -M main
$ git remote add origin https://github.com/luckydog/lab02.git
$ git push -u origin main
```



3. Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.
```
#include <iostream>

using namespace std;

int main(int argc, char** argv) {

   cout << "Hello world" << endl;
}
```

4. Добавьте этот файл в локальную копию репозитория.
```
$ git add Helloworld.cpp
```

5. Закоммитьте изменения с осмысленным сообщением.
```
$ git commit -m "This is first file"
```

6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
```
include <iostream>
include <string>
using namespace std;
int main() {
cout << "Hello world!";
string name;
cout << "Please enter name";
cin >> name;
cout << "Hello world from " << name;
}
```
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
```
$ git add Helloworld.cpp
$ git commit -m "updated Hello world.cpp"
```

8. Запуште изменения в удалёный репозиторий.
```
$ git push origin main
```
9. Проверьте, что история коммитов доступна в удалёный репозитории.


Part 2
1. В локальной копии репозитория создайте локальную ветку patch1.
```
$ git branch patch1
$ git checkout patch1
```
2. Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.
```
include <iostream>
include <string>
int main() {
std::string name;
std::cout << "Please enter name";
std::cin >> name;
std::cout << "Hello world from " << name;
}
```

3. commit, push локальную ветку в удалённый репозиторий.
```
$ git add Helloworld.cpp
$ git commit -m "patched Hello world.cpp"
$ git push origin patch1
```
4. Проверьте, что ветка patch1 доступна в удалёный репозитории.


5. Создайте pull-request patch1 -> master.


6. В локальной копии в ветке patch1 добавьте в исходный код комментарии.
```
include <iostream>
include <string>
int main() {
std::string name;
std::cout << "Please enter name";
std::cin >> name; //введите имя
std::cout << "Hello world from " << name;
}
```

7. commit, push.
```
$ git add Helloworld.cpp
$ git commit -m "added comment"
$ git push origin patch1
```

8. Проверьте, что новые изменения есть в созданном на шаге 5 pull-request.


9. В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.


10. Локально выполните pull.
```
$ git checkout main
$ git pull origin main
```

11. С помощью команды git log просмотрите историю в локальной версии ветки master.
```
$ git log
```

12. Удалите локальную ветку patch1.
```
$ git branch -d patch1
```

Part 3
1. Создайте новую локальную ветку patch2.
```
$ git branch patch2
$ git checkout patch2
```
2. Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.
```
$ sudo apt install clang-format
$ clang-format "/home/kali/lab02/Helloworld.cpp" -style=Mozilla -i "/home/kali/lab02/Helloworld.cpp"
```

3. commit, push, создайте pull-request patch2 -> master.
```
$ git add Helloworld.cpp
$ git commit -m "changed codestyle"
$ git push origin patch2
```

4. В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.


5. Убедитесь, что в pull-request появились конфликтны.


6. Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.
```
$ git pull origin main --rebase
```
```
include<iostream> include<string>
int
main()
{
  std::string name;
  std::cout << "Please enter name";
  std::cin >> name; //enter the name
  std::cout << "Hello world from " << name;
}
```
```
$ git rebase --continue
```




7. Сделайте force push в ветку patch2
```
$ git push -f origin patch2
```
8. Убедитель, что в pull-request пропали конфликтны.


9. Вмержите pull-request patch2 -> master.

