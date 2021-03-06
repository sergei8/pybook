# Лабораторная работа №1. Алгоритмы шифрования

Так как это ваша первая лабораторная работа, то в ней описаны общие требования предъявляемые к выполнению текущей и всех последующих работ.

Каждое задание оценивается в отдельности, таким образом, оценку вы получаете по совокупности выполненных заданий (в лабораторной работе №1 таких заданий - три). В оценку включается балл за стиль выполнения задания, поэтому прочитайте официальное руководство по стилю https://www.python.org/dev/peps/pep-0008/ (также некоторые пояснения по оформлению кода можно найти [здесь](https://github.com/Dementiy/pydonts)). Соответствие вашей работы PEP8 можно узнать "прогнав" исходный код вашей программы через утилиту `pep8`.

Все исходники к работам вы можете найти в [репозитории курса](https://github.com/Dementiy/pybook-assignments) (следите за его обновлениями). Чтобы получить список всех работ достаточно выполнить следующую команду:

```sh
$ git clone https://Dementiy@bitbucket.org/Dementiy/cs102_2016.git
```

<div class="alert alert-danger">
Описание работы с командой <code>git</code> читай в разделе "<a href="https://dementiy.gitbooks.io/-python/content/lab0.html">Настройка рабочего окружения</a>".
</div>

Все дальнейшие изменения в репозитории можно получать с помощью команды `git pull` (её рекомендуется использовать каждый раз, когда вы приступаете к выполнению новой лабораторной работы):

```sh
$ git pull
```

### Прежде чем приступить к выполнению работы

Перед тем как начать выполнять лабораторную работу не забудьте перейти в рабочую директорию и активировать ваше виртуальное окружение:

```sh
$ cd путь/к/рабочей_директории
$ workon cs102
```

Также создадим ветку разработки (подробнее про git workflow можно прочитать [тут](https://habrahabr.ru/post/106912/)):

```sh
(cs102) $ git checkout -b develop master
Switched to a new branch 'develop'
```

Теперь создадим ветку новой функциональности:
```sh
(cs102) $ git checkout -b feature/caesar develop
Switched to a new branch 'feature/caesar'
```

И, наконец, создадим папку, в которой будем хранить все файлы, относящиеся к первой лабораторной работе:

```
(cs102) $ mkdir homework01
```

### Шифр Цезаря

[Шифр Цезаря](https://ru.wikipedia.org/wiki/Шифр_Цезаря) является одним из самых простых методов шифрования. Для кодирования сообщения все буквы алфавита сдвигают на три символа вперед:

```
A -> D, B -> E, C -> F, и так далее
```

Сдвиг трёх последних букв алфавита:

```
X -> A, Y -> B, Z -> C
```

Используя шифр Цезаря, слово `PYTHON` будет закодировано следующим образом:

```
PYTHON
||||||
SBWKRQ
```

Вам необходимо написать тело для следующих двух функций:

```python
def encrypt_caesar(plaintext):
    """
    >>> encrypt_caesar("PYTHON")
    'SBWKRQ'
    >>> encrypt_caesar("python")
    'sbwkrq'
    >>> encrypt_caesar("Python3.6")
    'Sbwkrq3.6'
    >>> encrypt_caesar("")
    ''
    """
    # PUT YOUR CODE HERE
    return ciphertext


def decrypt_caesar(ciphertext):
    """
    >>> decrypt_caesar("SBWKRQ")
    'PYTHON'
    >>> decrypt_caesar("sbwkrq")
    'python'
    >>> decrypt_caesar("Sbwkrq3.6")
    'Python3.6'
    >>> decrypt_caesar("")
    ''
    """
    # PUT YOUR CODE HERE
    return plaintext
```

В результате переменные `ciphertext` и `plaintext` должны содержать зашифрованное и расшифрованное сообщения соответственно.

<div class="alert alert-info">
<strong><a href="https://mail.python.org/pipermail/python-win32/2005-April/003100.html">Подсказка</a></strong>: Воспользуйтесь встроенными функциями <tt>ord()</tt> и <tt>chr()</tt>. Функция <tt>ord()</tt> позволяет получить код указанного символа, например:<br/>
<tt>
>>> ord('A')<br/>
65<br/>
</tt>
Функция <tt>chr()</tt> работает наоборот - возвращает символ по его коду:<br>
<tt>
>>> chr(65)<br/>
'A'</tt>
</div>

<div class="alert alert-info">
О кодировках можно почитать <a href="http://kunststube.net/encoding/">тут</a> и <a href="http://farmdev.com/talks/unicode/">тут</a>.
</div>

В папке `homework01` создайте файл с именем `caesar.py` и шаблоном приведенным выше. Сделайте коммит с первоначальным шаблоном:

```sh
(cs102) $ git add homework01/caesar.py
(cs102) $ git commit -m "Добавлен шаблон для шифра Цезаря"
```

По завершении работы над каждой функцией не забудьте также сделать коммит, например:

```sh
(cs102) $ git commit -am "Реализована функция encrypt_caesar()"
```

и аналогично:

```sh
(cs102) $ git commit -am "Реализована функция decrypt_caesar()"
```

Проверить работу функций можно с помощью примеров, приведенных в [доктестах](https://docs.python.org/3.5/library/doctest.html) (текст внутри функции, который заключен в тройные кавычки и похож на работу с интерпретатором в интерактивном режиме). Запустить доктесты можно с помощью следующей команды (при условии, что файл с программой называется `caesar.py`):

```sh
$ python3 -m doctest -v caesar.py
```

Если все тесты были пройдены успешно, то объедините (merge) ваши изменения с веткой `develop`:

```sh
(cs102) $ git checkout develop
(cs102) $ git merge --no-ff feature/caesar
```

<div class="alert alert-info">
<strong>Замечание</strong>: Вы можете воспользоваться приложением <a href="https://www.sourcetreeapp.com/">Source Tree</a> для наглядного отслеживания вносимых изменений.
</div>

<div class="alert alert-info">
<strong>Практика</strong>: Измените ваши функции так, чтобы размер сдвига был произвольным:<br/>
<code>encrypt_caesar(plaintext, shift)</code><br/>
<code>decrypt_caesar(plaintext, shift)</code>
</div>

### Шифр Виженера

[Шифр Виженера](https://ru.wikipedia.org/wiki/Шифр_Виженера) очень похож на шифр Цезаря, за тем исключением, что каждый символ сообщения сдвигается на определяемое ключом значение. Ключ - это слово, каждый символ которого указывает на сколько позиций должен быть сдвинут соответствующий символ в шифруемом сообщении. Так, `A` означает сдвиг на `0` символов, `B` на `1` и т.д.

Если длина ключа меньше длины слова, подлежащего шифрованию, то ключ повторяется необходимое число раз, например:

```
Простой текст:           ATTACKATDAWN
Ключ:                    LEMONLEMONLE
Зашифрованный текст:     LXFOPVEFRNHR
```

Ваша задача написать тело для следующих двух функций так, чтобы переменные `ciphertext` и `plaintext` содержали зашифрованное и расшифрованное сообщения соответственно.

```python
def encrypt_vigenere(plaintext, keyword):
    """
    >>> encrypt_vigenere("PYTHON", "A")
    'PYTHON'
    >>> encrypt_vigenere("python", "a")
    'python'
    >>> encrypt_vigenere("ATTACKATDAWN", "LEMON")
    'LXFOPVEFRNHR'
    """
    # PUT YOUR CODE HERE
    return ciphertext


def decrypt_vigenere(ciphertext, keyword):
    """
    >>> decrypt_vigenere("PYTHON", "A")
    'PYTHON'
    >>> decrypt_vigenere("python", "a")
    'python'
    >>> decrypt_vigenere("LXFOPVEFRNHR", "LEMON")
    'ATTACKATDAWN'
    """
    # PUT YOUR CODE HERE
    return plaintext
```

<div class="alert alert-info">
Обратите внимание, что символы <tt>A</tt> и <tt>a</tt> в ключе не оказывают никакого влияния на шифруемое сообщение. Если же в качестве ключа мы будем использовать <tt>C</tt> или <tt>c</tt>, то получим шифр Цезаря.
</div>

Перед выполнением задания не забудьте создать новую ветвь функциональности `feature/vigenere` и сделать коммит с шаблоном (файл с шаблоном должен быть размещен в каталоге `homework01` под именем `vigener.py`):

```sh
(cs102) $ git checkout -b feature/vigener develop
(cs102) $ git add homework01/vigener.py
(cs102) $ git commit -m "Добавлен шаблон для шифра Виженера"
```

По окончании работы над каждой функцией не забудьте сделать соответствующие коммиты, как в примере с шифром Цезаря, а также объединенить изменения с веткой `develop`:

```sh
(cs102) $ git checkout develop
(cs102) $ git merge --no-ff feature/vigener
```

### RSA шифрование

Одним из современных методов шифрования является алгоритм шифрования RSA, названный так по первым буквам фамилий его авторов.

Мы не будем здесь вдаваться в [подробности работы](http://kpfu.ru/docs/F366166681/mzi.pdf) этого алгоритма (хотя и рассмотрим техническую часть), но [следующего объяснения](https://www.quora.com/How-do-you-explain-how-an-RSA-public-key-works-to-a-child) должно быть достаточно для понимания принципов шифрования с открытым ключом:

> ![](https://qph.ec.quoracdn.net/main-qimg-8ad399b007bf86350675e8cbf5be6e34-c?convert_to_webp=true)
> 
> Show your kid a padlock. This is a kind of lock that locks when you click it (i.e it doesn't require a key) but requires the key to open the lock.
> 
> So, I can send these padlocks to all my friends who want to communicate with me. I will send them only the lock but will keep the key with me.
> 
> My friends can write me messages, put it in a box, lock it with my padlock (by clicking it) and send it to me, even over high risk networks. If the box is intercepted, it's contents will not be compromised since I still have the key with me.
> 
> When the box reaches me, I can open my padlock with my key and read the contents. This way, I can send padlocks (public keys) to people outside which they can use to lock boxes (encrypt messages) without being in danger of the contents being compromised as the padlock key (the private key) is always with me and never exchanged over the network.

Работу алгоритма можно разбить на три шага:
1. Генерация ключей
2. Шифрование
3. Расшифровка

<div class="alert alert-info">От вас в этом задании требуется выполнить только шаг генерации ключей, остальные два шага уже даны (см. исходники к работе).
</div>

На этапе генерации создаётся два ключа: открытый (public key, с помощью которого каждый сможет зашифровать сообщение и отправить его нам) и закрытый (private key, которым мы можем расшифровать полученные сообщения). Для этого выбирается два [простых числа](https://ru.wikipedia.org/wiki/Простое_число) `p` и `q`. Позволим пользователю вводить эти числа, но их необходимо проверять на простоту. Для этого напишем функцию, но предварительно создадим новую ветку функциональности и сделаем коммит с шаблоном для этого задания:

```sh
(cs102) $ git checkout -b feature/rsa develop
(cs102) $ git add homework01/rsa.py
(cs102) $ git commit -m "Добавлен шаблон для RSA шифрования"
```

Теперь можно начать работать над функцией `is_prime(n)`:

```python
def is_prime(n):
    """
    >>> is_prime(2)
    True
    >>> is_prime(11)
    True
    >>> is_prime(8)
    False
    """
    # PUT YOUR CODE HERE
    pass
```

<div class="alert alert-info">
Если вы не понимаете, как работают функции, то напишите небольшую программу выводящую <code>True</code> или <code>False</code> в зависимости от того, является число простым или нет. Затем полученный код скопируйте в приведенную выше функцию (вместо ключевого слова <code>pass</code>) и замените <code>print(True)</code> на <code>return True</code>, а <code>print(False)</code> на <code>return False</code>.
</div>

Если вы закончили работу над функцией `is_prime(n)` - сделайте коммит:

```sh
(cs102) $ git commit -am "Реализована функция is_prime(n)"
```

После того как были выбраны два простых числа находится их произведение `n = p * q` (по ходу объяснения заменяйте комментарий со словами `PUT YOUR CODE HERE` в приведенной ниже функции на соответствующее решение).

```python
def generate_keypair(p, q):
    if not (is_prime(p) and is_prime(q)):
        raise ValueError('Both numbers must be prime.')
    elif p == q:
        raise ValueError('p and q cannot be equal')
    
    # n = pq
    # PUT YOUR CODE HERE

    # phi = (p-1)(q-1)
    # PUT YOUR CODE HERE

    # Choose an integer e such that e and phi(n) are coprime
    e = random.randrange(1, phi)

    # Use Euclid's Algorithm to verify that e and phi(n) are comprime
    g = gcd(e, phi)
    while g != 1:
        e = random.randrange(1, phi)
        g = gcd(e, phi)

    # Use Extended Euclid's Algorithm to generate the private key
    d = multiplicative_inverse(e, phi)
    
    # Return public and private keypair
    # Public key is (e, n) and private key is (d, n)
    return ((e, n), (d, n))
```

Затем вычисляется функция Эйлера по формуе `phi=(p-1)(q-1)`.

Далее выбирается число `e`, отвечающее следующим критериям:
* `e` — простое;
* `e < phi`;
* `e` [взаимно простое](https://ru.wikipedia.org/wiki/Взаимно_простые_числа) с `phi`.

Определить, являются ли числа взаимно простыми можно с помощью алгоритма Евклида. Для этого необходимо вычислить наибольший общий делитель (НОД) и проверить, **равен ли он единице**. На этом этапе вашей задачей является реализация данного алгоритма:

```python
def gcd(a, b):
    """
    >>> gcd(12, 15)
    3
    >>> gcd(3, 7)
    1
    """
    # PUT YOUR CODE HERE
    pass
```

Не забудьте закоммитить реализацию функции `gcd(a, b)`:

```sh
(cs102) $ git commit -am "Реализована функция поиска НОД"
```

Заключительным этапом на шаге генерации ключей является вычисление `d` такого что `d * e mod phi = 1`. Для его вычисления используется расширенный (обобщенный) алгоритм Евклида (см. стр. 23 [этого учебного пособия](http://kpfu.ru/docs/F366166681/mzi.pdf) с подробными объяснениями).

```python
def multiplicative_inverse(e, phi):
    """
    >>> multiplicative_inverse(7, 40)
    23
    """
    # PUT YOUR CODE HERE
    pass
```

Таким образом, полученные пары `(e,n)` и `(d,n)` являются открытым и закрытым ключами соответственно.

Снова закоммитьте изменения:

```sh
(cs102) git commit -am "Реализованы функции multiplicative_inverse() и generate_keypair()"
```

Не забудьте сделать коммит для объединения изменений с веткой `develop`:

```sh
(cs102) $ git checkout develop
(cs102) $ git merge --no-ff feature/rsa
```

### После выполнения всех заданий

После выполнения всех задач лабораторной работы создайте новый релиз:

```sh
(cs102) $ git checkout -b release-1.0 develop
(cs102) $ git commit -m "Релиз 1.0"
```

Если ваша работа была **зачтена**, то закройте ветвь релиза:

```sh
(cs102) $ git checkout master
(cs102) $ git merge --no-ff release-1.0
(cs102) $ git tag -a 1.0
```

Соответствующие ветви функциональности можно удалить, например:

```sh
(cs102) $ git branch -d feature/caesar
```