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

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_16_51_29](https://github.com/luckydog228/lab02/assets/128289395/7ddd544e-8c98-4993-9ce2-80880a18654f)


3. Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.
```
#include <iostream>

using namespace std;

int main(int argc, char** argv) {

   cout << "Hello world" << endl;
}
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_16_52_48](https://github.com/luckydog228/lab02/assets/128289395/feebdd8d-ac5d-4151-bc5c-1c6eb578d164)

4. Добавьте этот файл в локальную копию репозитория.
```
$ git add Helloworld.cpp
```

5. Закоммитьте изменения с осмысленным сообщением.
```
$ git commit -m "This is first file"
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_16_54_48](https://github.com/luckydog228/lab02/assets/128289395/d7b6444b-6fc3-4e4c-b228-751c76fc0d74)

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
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_16_57_07](https://github.com/luckydog228/lab02/assets/128289395/dcfcca45-d6cd-4c8a-b7b4-fff10ed06e64)

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
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_16_58_17](https://github.com/luckydog228/lab02/assets/128289395/49c75fa6-da3c-4962-aa72-bf5c362716c6)

4. Проверьте, что ветка patch1 доступна в удалёный репозитории.


5. Создайте pull-request patch1 -> master.
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_16_59_07](https://github.com/luckydog228/lab02/assets/128289395/2820722b-9c71-4cfa-bb0b-ab6021f32cc5)


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
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_00_00](https://github.com/luckydog228/lab02/assets/128289395/2d829e52-d7a2-4470-8686-58a0b502865d)

8. Проверьте, что новые изменения есть в созданном на шаге 5 pull-request.

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_01_11](https://github.com/luckydog228/lab02/assets/128289395/ff453018-e274-4350-ba27-7204ebe2445b)

9. В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_01_25](https://github.com/luckydog228/lab02/assets/128289395/9e802e96-8c8f-4f2e-94ad-cdb5b20e080a)

10. Локально выполните pull.
```
$ git checkout main
$ git pull origin main
```

11. С помощью команды git log просмотрите историю в локальной версии ветки master.
```
$ git log
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_02_04](https://github.com/luckydog228/lab02/assets/128289395/4de2643f-4409-42e9-a965-e4e23e2b0aa3)

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
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_03_46](https://github.com/luckydog228/lab02/assets/128289395/26b5b452-e276-4058-9508-2229b4b57c5e)

3. commit, push, создайте pull-request patch2 -> master.
```
$ git add Helloworld.cpp
$ git commit -m "changed codestyle"
$ git push origin patch2
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_09_34](https://github.com/luckydog228/lab02/assets/128289395/b2ef7602-ffd0-4ab5-a7be-91f35e85c321)

4. В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_10_40](https://github.com/luckydog228/lab02/assets/128289395/48922506-1e5e-47a4-8a98-ff727415084b)

5. Убедитесь, что в pull-request появились конфликтны.

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_14_07](https://github.com/luckydog228/lab02/assets/128289395/6b4045ff-f846-40a3-b31e-4714e2362534)

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


![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_15_15](https://github.com/luckydog228/lab02/assets/128289395/a00a3929-6b77-4770-a436-4c553a65b99d)


7. Сделайте force push в ветку patch2
```
$ git push -f origin patch2
```
8. Убедитель, что в pull-request пропали конфликтны.

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_30_05_2023_17_18_53](https://github.com/luckydog228/lab02/assets/128289395/7b36c2aa-4980-4e42-abd2-0a86c7f3b4a6)


9. Вмержите pull-request patch2 -> master.

