## 3.1 Анимация автоатаки

Каждый чемпион в League of Legends имеет уникальные **комбо** (combo). Так называется последовательность действий, которая увеличивает их эффект. Например, атакующее комбо увеличивает урон чемпиона в секунду (DPS).

Чтобы исполнить любое комбо, необходимо понять и освоить работу с анимацией. Когда игрок даёт команду на любое действие, чемпион его исполняет. В это время он совершает какие-то движения. Они называются **анимацией действия**. Обычно анимация уникальна для каждого действия.

Работа с анимацией — это сложная, но важная тема. Чтобы её освоить нужны время и регулярные тренировки. Если игрок не умеет работать с анимацией, он не сможет эффективно делать следующие вещи:

1. Фармить лесных монстров.
2. Фармить миньонов на линии.
3. Участвовать в командных
сражениях.
4. Выигрывать трейды на линии.
5. Выигрывать дуэли на линии или в лесу.

I> **Трейд** (trade) — это обмен уроном между оппонентами на линии. Каждая сторона стремится нанести противнику больше урона, чем получить в ответ. Такой трейд считается успешным и даёт победителю преимущество по динамическим ресурсам.

Другими словами, работа с анимацией позволяет эффективно получать ресурсы и реализовать их. Без этого навыка ни то, ни другое невозможно.

Начнём с самой простой анимации — базовой атаки чемпиона.

### 3.1.1 Скорость автоатаки

[**Базовая атака**](https://wiki.leagueoflegends.com/en-us/Basic_attack) или автоатака (basic attack, auto attack или AA) — это стандартный способ нанести противнику урон. Он доступен каждому чемпиону. Чтобы выполнить автоатаку, достаточно нажать правой кнопкой мыши по противнику.

Анимация автоатаки зависит от характеристики чемпиона, которая называется **общая скорость атаки** (total attack speed или total AS). Она складывается из следующих компонентов:

1. **Базовая скорость атаки** (base attack speed или base AS) чемпиона.

2. **Дополнительная скорость атаки** (bonus AS) за уровень чемпиона.

3. Bonus AS за предметы.

4. Bonus AS за руны.

5. Bonus AS за умения.

6. Bonus AS за усиления.

7. Штраф скорости атаки за ослабления.

Рассчитаем на примере общую скорость атаки (total AS). Возьмём чемпиона Ashe с base AS равной 0.66. На первом уровне без предметов, умений, рун на скорость атаки и усилений total AS чемпиона будет равна base AS. Это означает, что total AS равна 0.66.

Допустим, что Ashe покупает предмет [Berserker's Greaves](https://wiki.leagueoflegends.com/en-us/Berserker's_Greaves). Он даёт bonus AS 35%. Тогда total AS рассчитывается по следующей формуле:
{line-numbers: false, format: text}
```
total_AS = base_AS * (1 + bonus_AS / 100)
```

Подставим числа и получим:
{line-numbers: false, format: text}
```
total_AS = 0.66 * (1 + 35 / 100) = 0.89
```

I> У каждого чемпиона есть характеристика **коэффициент скорости атаки** (AS ratio). Это множитель для bonus AS. AS ratio у большинства чемпионов равен 1. Им предмет Berserker's Greaves даёт 35% AS. У некоторых чемпионов AS ratio меньше единицы (например, у Senna и Twisted Fate). Для них бонус от Berserker's Greaves окажется меньше 35%.

Мы рассчитали общую скорость атаки (total AS). Она определяет, сколько времени чемпион будет проигрывать анимацию одной автоатаки. Этот параметр называется **время перезарядки автоатаки** (attack cooldown). Он рассчитывается так:
{line-numbers: false, format: text}
```
attack_cooldown = 1 / total_AS
```

Подставим числа для Ashe с Berserker's Greaves и получим:
{line-numbers: false, format: text}
```
attack_cooldown = 1 / 0.89 = 1.12
```

Это означает, что между двумя автоатаками чемпиона должно пройти минимум 1.12 секунды. Другими словами, чемпион не выполнит вторую автоатаку, пока не пройдёт время перезарядки.

### 3.1.2 Фазы анимации автоатаки

Мы научились рассчитывать время перезарядки автоатаки. Пока оно идёт, чемпион проигрывает полный цикл анимации атаки. Цикл состоит из трёх фаз:

1. **Windup** — замах.

2. **Firing** — удар или выстрел.

3. **Recovery** — возврат в исходное положение.

Рассмотрим эти фазы на примере Ashe первого уровня без предметов. Её время перезарядки автоатаки равно 1.52 секунды:
{line-numbers: false, format: text}
```
attack_cooldown = 1 / 0.66 = 1.52
```

Иллюстрация 3-1 демонстрирует временную диаграмму одной автоатаки Ashe.

{caption: "Иллюстрация 3-1. Временная диаграмма автоатаки Ashe", width: "100%"}
![Временная диаграмма автоатаки](images/Micromanagement/ashe-attack-animation.png)

На иллюстрации изображена ось времени s. На ней отложены три отрезка. Каждый соответствует одной из трёх фаз анимации. Над отрезками приведены скриншоты из игры. Они демонстрируют кадры из соответствующей анимации.

Рассмотрим диаграмму по шагам:

1. В точке A игрок нажимает правой кнопкой мыши на цель. С этого момента чемпион проигрывает фазу анимации windup: натягивает тетиву лука. Она длится 21.93% от всего времени перезарядки автоатаки. Это равно 0.33 секунды, согласно следующему расчёту:
{line-numbers: false, format: text}
```
windup = 1.52 * 21.93 / 100 = 0.33
```

2. В точке B чемпион начинает фазу firing: выпускает стрелу в цель. Она длится всего 3.37% от времени перезарядки автоатаки. Это равно 0.05 секунд:
{line-numbers: false, format: text}
```
firing = 1.52 * 3.37 / 100 = 0.05
```

3. В точке C чемпион начинает фазу recovery: достаёт из колчана следующую стрелу. Эта фаза длится 74.22% времени перезарядки автоатаки. Она составляет 1.13 секунды:
{line-numbers: false, format: text}
```
windup = 1.52 * 74.22 / 100 = 1.13
```

4. В точке D чемпион заканчивает полный цикл анимации. Прошло 1.52 секунды с момента, когда игрок дал команду в точке A. Если чемпион не получит новой команды, то в точке D он начнёт следующий цикл анимации атаки по той же цели.

В любой момент на отрезка A-D игрок может дать чемпиону команду на движение. Её результат зависит от фазы анимации, которую сейчас проигрывает чемпион. Возможны [три случая](https://wiki.leagueoflegends.com/en-us/Stutter-stepping):

1. Отрезок A-B — команда попала на фазу windup:

   * Чемпион отменит автоатаку.

   * Цель атаки не получит урон.

   * Таймер перезарядки автоатаки сбросится в ноль.

   * Игрок может запустить следующую автоатаку в любой момент. Её анимация начнётся с фазы windup (точка A).

2. Отрезок B-C — команда попала на фазу firing:

   * Команда на движение попадёт в очередь.

   * Чемпион выполнит автоатаку.

   * Цель атаки получит урон, если атака в ближнем бою. В случае дальнего боя цель получит урон, когда в неё попадёт снаряд.

   * Таймер перезарядки автоатаки продолжит идти.

   * После окончания анимации firing (точка C) команда на движение извлекается из очереди. Чемпион её выполнит, вместо анимации recovery. Он идёт в указанную точку.

   * Игрок не может запустить следующую автоатаку. Сначала должен закончиться таймер перезарядки автоатаки в точке D.

3. Отрезок C-D — команда попала на фазу recovery:

   * Чемпион уже выполнил автоатаку.

   * Цель атаки уже получила урон.

   * Таймер перезарядки автоатаки продолжает идти.

   * Чемпион прекращает анимацию recovery и идёт в указанную точку.

   * Игрок не может запустить следующую автоатаку. Сначала должен закончиться таймер перезарядки автоатаки в точке D.

Из правил сочетания двух команд можно сделать следующие выводы:

1. Отмена фазы windup — это почти всегда ошибка. Она уменьшает урон чемпиона в секунду (DPS). Единственный случай, когда отмена оправдана, — игрок обнаружил опасность и вынужден немедленно отступать.

2. Фаза recovery всегда занимает большую часть времени перезарядки автоатаки. Позволять чемпиону её проигрывать — значит впустую тратить время. Вместо этого следует двигаться или использовать умение.

3. Самый эффективный способ отменить фазу recovery — дать команду во время firing. Тогда сразу после firing чемпион исполнит новую команду.

### 3.1.3 Атака и движение

Отмена фазы автоатаки recovery часто применяется на практике. Приём **attack move** (атака и движение) — это отмена анимации с помощью команды на движение.

I> Следующее [видео на канале Skill Capped](https://www.youtube.com/watch?app=desktop&v=-oyxOgtT33U) подробно объясняет приём attack move.

Рассмотрим временную диаграмму приёма attack move. Её демонстрирует иллюстрация 3-2.

{caption: "Иллюстрация 3-2. Временная диаграмма attack move", width: "100%"}
![Временная диаграмма attack move](images/Micromanagement/ashe-attack-move.png)

Шаги этого приёма следующие:

1. В точке A игрок даёт команду на атаку. Чемпион проигрывает фазу анимации windup.

2. В точке B чемпион начинает фазу firing.

3. На отрезке B-C или в точке C игрок даёт команду на движение. Чемпион начинает двигаться сразу после завершения анимации firing. Это происходит на отрезке C-D, который длится 1.13 секунды.

4. В точке D заканчивается таймер перезарядки автоатаки. Начиная с этого момента игрок может дать команду на следующую атаку.

Технику attack move применяют в двух случаях:

1. Чтобы преследовать противника и наносить ему урон.

2. Чтобы отступать и наносить противнику урон.

В **первом случае** приём увеличивает урон по отступающему противнику. Рассмотрим разницу между командой на атаку и приёмом attack move:

* Если дать чемпиону команду на атаку, он будет стоять на месте и проигрывать все три фазы анимации. Когда противник выйдет из радиуса атаки Ashe, она отреагирует на это только в точке D. Другими словами, она начнёт двигаться только после окончания фазы recovery.

* Если применить **attack move**, чемпион будет двигаться к противнику вместо проигрывания анимации фазы firing. Это означает, что Ashe будет реагировать на его перемещение намного быстрее.

Во **втором случае** приём уменьшает урон по отступающему чемпиону. Рассмотрим разницу между attack move и отдельными командами:

* Если игрок даёт команду на атаку, чемпион стоит на месте и проигрывает все три фазы анимации. В этом случае он просто разменивается с противником уроном. Такой размен называется [**stat check**](https://www.reddit.com/r/leagueoflegends/comments/10q7lmk/comment/j6ob8tk/). Его выигрывает тот чемпион, у которого характеристики больше.

* Игрок может дать команду на движение и только отступать. В этом случае он будет получать урон до тех пор, пока не выйдет из радиуса атаки противника. Противник при это не получит никакого урона.

* Если применить **attack move**, чемпион будет размениваться уроном с противником и при этом сохранять с ним дистанцию. Это открывает две возможности. Игрок может либо перейти только к отступлению, если проиграл трейд, либо перейти в all-in, если выиграл трейд. Ни одно из отдельных действий таких возможностей не даёт.

I> **All-in** (аллын) — активный бой до победы, в котором используются все доступные умения и средства атаки. Обычно all-in заканчивается смертью одного из участников, если это дуэль.

Когда attack move применяет чемпион дальнего боя против оппонента ближнего боя, это называется **kiting** (кайтинг). Если скорость движения чемпиона больше, противник не сможет его атаковать.

### 3.1.4 Исполнение приёма атака и движение

Рассмотрим, как исполнять приём attack move. Для этого надо изменить две настройки игры.

**Первая настройка** находится во вкладке "HOTKEYS". Она называется "Player Attack Move Click". Её демонстрирует иллюстрация 3-3.

{caption: "Иллюстрация 3-3. Настройка 'Player Attack Move Click'", height: "50%"}
![Настройка Player Attack Move Click](images/Micromanagement/options-player-attack-move-click.png)

Эта горячая клавиша даёт команду на движение в указанную точку. Как только в радиусе атаки окажется противник, чемпион начнёт его атаковать. Назначьте для этого действия клавишу A. Тогда при её нажатии чемпион будет атаковать ближайшую к нему цель, если она находится в радиусе атаки.

**Вторая настройка** находится во вкладке "GAME" и называется "Attack move on cursor". Её демонстрирует иллюстрация 3-4.

{caption: "Иллюстрация 3-4. Настройка 'Attack move on cursor'", width: "100%"}
![Настройка Attack move on cursor](images/Micromanagement/options-attack-move-on-cursor.png)

Эта настройка делает следующее:

* Включить — команда attack move (клавиша A) выбирает цель, ближайшую к курсору мыши.

* Выключить — команда attack move (клавиша A) выбирает цель, ближайшую к чемпиону.

Включите эту настройку. Тогда вы сможете выбирать цель для атаки с помощью положения курсора мыши.

Теперь рассмотрим, как исполнить приём attack move с новыми настройками. Для этого выполните следующие шаги:

1. Приблизьте курсор мыши к цели. Его необязательно наводить точно на цель.

2. Нажмите горячую клавишу A. Чемпион начнёт выполнять фазу windup анимации атаки.

3. Переместите курсор мыши в точку, куда должен двигаться чемпион. Это должно быть направление на противника или от него.

4. Когда чемпион начнёт фазу firing или recovery, нажмите правую кнопку мыши. Чемпион будет двигаться в указанную точку.

5. Считайте в уме таймер перезарядки автоатаки. Когда он закончится, начните следующую атаку с шага 1.

При исполнении attack move игроки совершают следующие типичные ошибки:

* Дают команду на движение слишком рано. Если она попадёт на фазу windup, то отменит атаку чемпиона. Это сильно уменьшает его DPS.

* Дают чемпиону двигаться дольше, чем идёт таймер перезарядки атаки. Это мешает реализовать высокую скорость атаки чемпиона.

Тренируйте приём attack move в режиме "Practice tool". Почувствуйте ритм атаки своего чемпиона на разных уровнях и с разными предметами. Тогда вы научитесь атаковать точно в момент окончания таймера перезарядки.

Обратите внимание на связь между скоростью атаки и характером передвижения чемпиона. При низкой скорости атаки, чемпион двигается длинными отрезками. При высокой скорости атаки эти отрезки укорачиваются.

### 3.1.5 Атака и применение умения

Мы рассмотрели отмену анимации атаки командой на движение. Это только один из четырёх способов. Вот полный список действий, которые отменяют анимацию атаки:

1. Движение
2. Умение чемпиона
3. Заклинание призывателя
4. Активный эффект предмета.

Рассмотрим второй вариант: отмена анимации атаки умением чемпиона. Назовём этот приём аналогично первому варианту — **attack ability** (атака и умение). Третий и четвёртый варианты работают аналогично ему.

Иллюстрация 3-5 показывает временную диаграмму, когда умение чемпиона отменяет анимацию атаки.

{caption: "Иллюстрация 3-5. Временная диаграмма отмены анимации атаки умением", width: "100%"}
![Временная диаграмма отмены анимации атаки умением](images/Micromanagement/ashe-attack-ability.png)

Шаги этого приёма следующие:

1. В точке A игрок даёт команду на атаку. Чемпион проигрывает фазу анимации AA windup.

2. В точке B чемпион начинает фазу AA firing.

3. На отрезке B-C или в точке C игрок даёт команду применить умение W. Чемпион начинает выполнять его анимацию сразу после завершения фазы AA firing. Это происходит на отрезке C-D и далее.

4. В точке D заканчивается таймер перезарядки автоатаки. Начиная с этого момента игрок может дать команду на следующую атаку.

Приём attack ability применяют, когда нужно выдать максимальный урон в единицу времени (DPS). При этом цель находится в радиусе атаки и умений. Это особенно хорошо работает по обездвиженной цели. Если цель двигается и разрывает дистанцию, игроку придётся чередовать приёмы attack move и attack ability.

### 3.1.6 Исполнение приёма атака и умение

Чтобы эффективно исполнять приём attack ability, надо переключить все умения чемпиона на "Quick Cast". Эта настройка находится на вкладке "HOTKEYS". Её демонстрирует иллюстрация 3-6.

{caption: "Иллюстрация 3-6. Настройка 'Quick Cast All'", width: "100%"}
![Настройка Quick Cast All](images/Micromanagement/quick-cast.png)

На вкладке "HOTKEYS" нажмите кнопку "Quick Cast All". Тогда чемпион применит умение, как только вы отпустите соответствующую кнопку (например, W). Вам больше не нужно нажимать её дважды. Это значительно ускоряет действия в игре, но к этой настройке надо привыкнуть.

Обратите внимание, что некоторые умения с [**зарядкой**](https://leagueoflegends.fandom.com/ru/wiki/Подготовка) (charging) не стоит настраивать на Quick Cast. Если чемпион может двигаться во время зарядки, его позицию можно сменить заклинанием призывателя [скачок](https://leagueoflegends.fandom.com/ru/wiki/Скачок_(заклинание_призывателя)) (flash). Зажимать клавишу Quick Cast умения и одновременно использовать скачок неудобно. Легче когда умение настроено на Normal Cast (по-умолчанию). Вот примеры умений, которым не нужен Quick Cast: Vi Q, Viego W.

Теперь рассмотрим, как исполнить приём attack ability с настройкой умений на Quick Cast. Для этого выполните следующие шаги:

1. Приблизьте курсор мыши к цели. Его необязательно наводить точно на цель.

2. Нажмите горячую клавишу A. Чемпион начнёт выполнять фазу windup анимации атаки.

3. Наведите курсор мыши так, чтобы умение попало в цель.

4. Когда чемпион начнёт фазу firing или recovery, нажмите кнопку умения. Чемпион применит его вместо того, чтобы проигрывать анимацию recovery.

Типичная ошибка при исполнении этого приёма: применить умение на фазе windup анимации атаки. Тогда чемпион отменит атаку и использует умение. Это сильно уменьшает его DPS и может сломать комбо.

Тренируйте приём attack ability в "Practice tool". Постарайтесь запомнить две вещи на вашем основном чемпионе:

1. Как выглядит анимация firing вашего чемпиона, а также её примерное время на разных уровнях и предметах. Тогда вы не будете отменять её умением.

2. Область действия всех умений. Тогда вам не придётся зажимать кнопки, чтобы проверить радиус умений. Это может сэкономить секунды, которые решат исход сражения.

{pagebreak}
