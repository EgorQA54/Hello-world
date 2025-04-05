# Подробный гайд по Git для macOS  

Привет! Если ты хочешь разобраться с Git, это руководство поможет тебе. Здесь всё расписано максимально подробно. Теперь я добавил ещё полезные команды для работы с терминалом, чтобы тебе было легче ориентироваться и управлять файлами прямо из консоли.

---

## 1. Что такое Git?  

Git — это система для отслеживания изменений в коде. Она создаёт "снимки" твоего проекта, которые ты можешь сохранять и просматривать. Это удобно для отката к старым версиям проекта, работы в команде и хранения проекта в облаке (например, на GitHub).

---

## Полезные команды терминала, которые понадобятся  

### Навигация по файловой системе  

Ты будешь часто перемещаться между папками и работать с файлами в терминале. Вот основные команды для навигации:

- **Показать, в какой папке ты находишься сейчас (текущая директория)**:
  ```
  pwd
  ```
  Пример: терминал покажет что-то вроде `/Users/Username/my-project`.

- **Отобразить список файлов и папок в текущей директории**:
  ```
  ls
  ```
  Например: выдаст список файлов и папок, например `index.html style.css script.js`.

- **Показать скрытые файлы и папки** (иногда важно для Git):
  ```
  ls -a
  ```
  Все файлы и папки, начинающиеся с точки (например, `.git`), тоже будут видны.

- **Перейти в другую папку**:  
  Если папка лежит в текущей директории:
  ```
  cd <имя_папки>
  ```
  Пример:  
  ```
  cd first-project
  ```

- **Перейти в подкаталог (папка внутри папки)**:
  ```
  cd first-project/html
  ```

- **Перейти на уровень выше (в родительскую папку)**:
  ```
  cd ..
  ```

- **Перейти в домашнюю директорию**:
  ```
  cd ~
  ```

- **Перейти в корневую директорию**:
  ```
  cd /
  ```

---

### Работа с файлами и папками  

Эти команды помогут тебе создавать, перемещать, копировать и удалять файлы:

#### Создание:
- **Создать файл**:
  ```
  touch <имя_файла>
  ```
  Пример:  
  ```
  touch index.html
  ```

- **Создать несколько файлов сразу**:
  ```
  touch index.html style.css script.js
  ```

- **Создать папку**:
  ```
  mkdir <имя_папки>
  ```
  Пример:  
  ```
  mkdir second-project
  ```

#### Копирование и перемещение:
- **Скопировать файл в другую папку**:
  ```
  cp <имя_файла> <путь_куда>
  ```
  Пример:  
  ```
  cp file.txt ~/my-dir
  ```

- **Переместить файл или папку**:
  ```
  mv <имя_файла/папки> <путь_куда>
  ```

#### Чтение:
- **Посмотреть содержимое текстового файла**:
  ```
  cat <имя_файла>
  ```

#### Удаление:
- **Удалить файл**:
  ```
  rm <имя_файла>
  ```
  Пример:  
  ```
  rm about.html
  ```

- **Удалить пустую папку**:
  ```
  rmdir <имя_папки>
  ```

- **Удалить папку с её содержимым**:
  ```
  rm -r <имя_папки>
  ```
---

## 2. Установка Git  

### Проверяем, установлен ли Git на macOS  
Открой **Терминал** (нажми `Command + пробел` → напиши **Terminal** → нажми Enter).  

Введи команду:  
```
git --version
```

- Если Git уже установлен, терминал покажет что-то вроде: `git version 2.xxxx`. В этом случае можно сразу перейти к следующему пункту.  
- Если Git не установлен, macOS сама предложит тебе загрузить **Xcode Command Line Tools**. Просто согласись — нажми кнопку **Install**, и система всё сделает сама.  

### Установка через Homebrew
Если ты пользуешься Homebrew (менеджер пакетов на macOS) и хочешь установить последнюю версию Git:  
1. Убедись, что у тебя есть Homebrew. Введи в терминале:
   ```
   brew --version
   ```  
   Если brew не установлен, установи его командой (скопируй этот длинный текст в терминал):  
   ```
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```  

2. Установи Git:
   ```
   brew install git
   ```  

### Проверка установки Git  
После установки ещё раз выполни команду:  
```
git --version
```
Если терминал показывает нормальный ответ с номером версии, всё готово!

---

## 3. Первоначальная настройка  

Теперь, когда Git установлен, давай настроим кто ты такой, чтобы эта информация отображалась в истории изменений.

1. Укажи своё имя (это имя будет видно при каждом твоём сохранении):  
   ```
   git config --global user.name "Твое имя"
   ```
2. Укажи свой email (желательно тот же, что ты будешь использовать на GitHub):  
   ```
   git config --global user.email "твой.email@example.com"
   ```
   
3. Убедись, что настройки сохранены:  
   ```
   git config --list
   ```  
   Команда выведет что-то вроде:
   ```
   user.name=Твое имя
   user.email=твой.email@example.com
   ```

Если всё так, как задумано, значит, настройка прошла успешно.

---

## 4. Начало работы с Git  

Когда ты начнёшь работу над проектом, тебе нужно будет создать репозиторий (хранилище) для твоего кода. Всё, что ты будешь делать с проектом, будет записываться в эту папку.

### 1. Создай новую папку для проекта  
В терминале выполни команду:  
```
mkdir my-project
cd my-project
```  
Эта команда:
- создаёт новую папку с именем `my-project`,
- переходит внутрь этой папки.

### 2. Инициализируй репозиторий Git  
Чтобы папка начала отслеживать изменения с помощью Git, выполни команду:  
```
git init
```  
Теперь Git создал в этой папке скрытую папку `.git`, где будет храниться вся информация об истории изменений.  

> Проверить, действительно ли репозиторий создан, можно командой:  
> ```
> ls -a
> ```
> Она покажет все файлы, включая скрытые `.git`.

---

## 5. Основные команды Git  

Теперь, когда у нас есть проект, давай разберём самые важные команды, которые понадобятся постоянно.

---

### **1. Проверка состояния репозитория**  
Каждый раз, когда ты вносишь изменения в файл/проект, полезно проверить статус. Эта команда покажет, какие файлы изменены, добавлены или не отслеживаются:
```
git status
```
Если ты только что создал проект, всё, что здесь будет, — это сообщение вроде *"No commits yet"*.

---

### **2. Отслеживание изменений (стейджинг)**  
Git не сохраняет изменения автоматически. Сначала ты говоришь ему, какие файлы нужно сохранить. Это называется «добавление в индекс» (или **staging**).  

- Чтобы начать отслеживать конкретный файл:
  ```
  git add <имя_файла>
  ```
  
- Чтобы сразу добавить все файлы, которые есть в проекте:
  ```
  git add .
  ```

После команды `git add` статус изменится:  
```
git status
```  
Теперь файлы будут помечены как «готовы для коммита».

---

### **3. Сохранение изменений (коммит)**  
Когда ты добавил файл в индекс, его нужно сохранить. Сохранение изменений в истории называется **коммитом**.  

Создай коммит с описанием:
```
git commit -m "Добавил первые файлы проекта"
```  
Придумывай информативные и короткие описания, чтобы было понятно, что сделано.

Каждый коммит — это как «снимок» состояния твоего проекта.

---

### **4. Просмотр истории изменений**  
Ты можешь посмотреть, какие изменения ты (или кто-то ещё) добавлял в проект:  
```
git log
```
Каждый коммит будет отображаться как уникальный идентификатор (хэш), дата и сообщение.  

Чтобы история была короче и понятнее:  
```
git log --oneline
```

---

## 6. Подключение к GitHub и загрузка проекта  

Теперь, когда у нас есть локальные изменения, мы можем загрузить их на GitHub.

### 1. Создание репозитория на GitHub  
1. Перейди на [GitHub](https://github.com) и зарегистрируйся, если ещё не зарегистрировался.  
2. Нажми кнопку **+** в правом верхнем углу → **New repository**.  
3. Введи имя репозитория (например, `my-project`) и нажми **Create repository**.  

### 2. Подключение локального репозитория к удалённому  
Теперь нужно "прикрепить" твой локальный проект к репозиторию на GitHub.  
1. Скопируй ссылку на репозиторий (она будет наподобие: `https://github.com/твой-ник/my-project.git`).
2. Выпони в терминале команду:  
   ```
   git remote add origin https://github.com/твой-ник/my-project.git
   ```

### 3. Отправка изменений на GitHub  
Теперь отправляем наши локальные коммиты на сервер:  
```
git push -u origin main
```

Первый раз Git может попросить тебя авторизоваться (введи логин и пароль или используй токен с GitHub).

После этого проект появится на GitHub!

---

## 7. Как работать дальше?  

Каждый раз, когда ты делаешь изменения в коде, повторяй этот процесс:  
1. Проверь состояние файлов:
   ```
   git status
   ```
2. Добавь изменённые/новые файлы в индекс:
   ```
   git add .
   ```
3. Сделай коммит:
   ```
   git commit -m "Короткое описание изменений"
   ```
4. Отправь изменения на GitHub:
   ```
   git push
   ```

Если что-то будет непонятным, или ты хочешь изучить что-то посложнее (например, как работать с ветками), просто скажи. Помогу разобраться! :)

---

### Что такое Хеш в Git

Хеш в Git — это уникальный идентификатор коммита, который генерируется специальным алгоритмом. Он помогает Git определять и находить конкретный коммит в истории изменений.

#### Как хеш создается:
1. Когда ты делаешь коммит, Git берет всю информацию о нём:
   - дату и время,
   - автора,
   - содержимое файлов,
   - ссылку на предыдущий коммит.
2. Эта информация преобразуется с помощью алгоритма **SHA-1**. В результате получается строка из 40 символов (цифры и буквы от A до F).

#### Свойства хеша:
- **Уникальность:** каждый хеш однозначно соответствует одному конкретному коммиту.  
- **Повторяемость:** если информация о коммите одинаковая — хеш всегда будет одинаковым.  
- **Чувствительность к изменениям:** если ты изменишь даже один символ в содержимом файла или информации о коммите, хеш полностью поменяется.

#### Зачем нужен хеш:
- Хеш — это как «имя» коммита. Зная его, ты можешь получить всё про коммит: кто его сделал, когда, что изменил.  
- Его можно использовать в Git-командах, чтобы явно указать, с каким коммитом ты хочешь работать (например, вернуть изменения к определённому состоянию или посмотреть их).  
- Git хранит все хеши и данные о коммитах в скрытой папке `.git` внутри проекта.

#### Пример:
Когда ты вводишь в терминале `git log`, ты видишь историю коммитов, где рядом с каждым указан его хеш — это странная строка вида `1a2b3c4d...`. Это тот самый уникальный идентификатор.

---

### Как исследовать лог в Git

Команда `git log` — это инструмент, с помощью которого можно посмотреть историю всех коммитов в репозитории. Давай разберёмся, из чего состоит информация в логе и как быстро находить нужные коммиты.

#### Что ты увидишь в описании коммита:
1. **Хеш** — строка из цифр и латинских букв рядом со словом `commit`. Это уникальный идентификатор коммита.
2. **Author** — имя автора коммита и его почта.
3. **Date** — дата и время, когда был создан коммит.
4. **Сообщение** — текстовое описание, которое ты добавляешь к коммиту (например, зачем или что именно было изменено).

---

#### Как вывести сокращённый лог:
Если в проекте много коммитов, удобнее использовать сокращённую версию лога. Для этого введи команду:

```
git log --oneline
```

**Что она покажет:**
- Первые символы хеша (несколько символов вместо полного длинного хеша).
- Сообщение коммита.

---

#### Зачем нужен сокращённый лог:
- **Экономия времени.** Если у тебя в проекте сотни или тысячи коммитов, длинный лог неудобно читать. Сокращённый лог помогает быстрее находить нужный коммит.  
- **Удобство работы.** С помощью сокращённого хеша (первых символов) можно работать точно так же, как с полным хешем — он остаётся уникальным внутри репозитория, и Git поймёт, о каком коммите речь.

---

🌟 **Полезный совет:**  
Иногда Git не выходит из лога сам. Чтобы выйти, жми `Q` (от Quit — «выйти», английская раскладка).

---

### Что такое HEAD в Git

**HEAD** — это указатель на последний коммит в ветке, то есть на самый новый. Используется, чтобы Git понимал, к какому коммиту ты работаешь прямо сейчас.

---

#### Где находится HEAD?
- HEAD — это специальный файл, который хранится в скрытой папке `.git`.
- Внутри файла указано, на какую ветку HEAD ссылается (например, `refs/heads/master`).

---

#### Как это проверить:
1. Открой папку `.git`:
   ```
   cd .git
   ```
2. Посмотри, что в файле HEAD:
   ```
   cat HEAD
   ```
   Результат может быть таким:
   ```
   ref: refs/heads/master
   ```
3. Теперь проверь хеш последнего коммита, на который указывает ссылка:
   ```
   cat refs/heads/master
   ```
   Например:
   ```
   e007f5035f113f9abca78fe2149c593959da5eb7
   ```
4. Сравни этот хеш с последним коммитом в истории через `git log`. Они должны совпадать.

---

#### Как работает HEAD?
- Когда ты создаёшь новый коммит, Git записывает его хеш в файл ветки (например, `refs/heads/master`), а HEAD обновляется сам.
- Если ты переключаешься на другую ветку, HEAD начинает ссылаться на неё.

---

#### Зачем нужен HEAD:
- HEAD нужен, чтобы не писать каждый раз хеш последнего коммита. Ты просто можешь использовать слово `HEAD`.

Примеры:
- `git reset HEAD` — отменить изменения последнего коммита.
- `git checkout HEAD~1` — перейти на коммит перед последним.

---

**Просто запомни:** HEAD указывает на последний коммит текущей ветки и делает работу с Git проще! 😊

---

### Статусы файлов в Git

В Git файлы могут находиться в разных состояниях (статусах). Вот что они означают.

---

#### Основные статусы файлов:
1. **Untracked** (неотслеживаемый):  
   - Файл только что создан и пока не добавлен в Git.  
   - Git видит, что файл есть, но не следит за ним.  
   - Чтобы файл начал отслеживаться, нужно выполнить команду `git add`.

2. **Staged** (подготовленный):  
   - После команды `git add` файл попадает в **staging area**.  
   - Это список файлов, которые готовы к коммиту.  
   - Файл на этом этапе как будто «на сцене», ждет, чтобы его «зафотографировали» (закоммитили).

3. **Tracked** (отслеживаемый):  
   - Git уже следит за файлом.  
   - Включает:
     - Файлы, которые были закоммичены.
     - Файлы, добавленные в staging area.

4. **Modified** (изменённый):  
   - Если изменён файл, за которым Git уже следит, он получает статус *modified*.  
   - Такие изменения ещё не попадают в staging — для этого нужно снова выполнить `git add`.

---

#### Жизненный цикл файла в Git:
1. Создаёшь новый файл → **Untracked**.  
2. Делаешь `git add` → **Staged**.  
3. Коммитишь изменения (`git commit`) → **Tracked**.  
4. Изменяешь файл → **Modified**.  
5. Снова делаешь `git add` → **Staged**.  
6. Коммитишь → снова **Tracked**.  
7. И так по кругу.

---

#### Важные моменты:
- Если файл уже находится в **staging** (подготовлен к коммиту), но ты снова его изменишь, Git будет считать:
  - Содержимое staging «старой версией».
  - Новые изменения получат статус **Modified**.  
- Чтобы обновить staging, нужно снова выполнить `git add`.

---

Git сначала может показаться сложным, но со временем эти статусы и команды станут понятны. Если что — спрашивай, помогу разобраться! 😊