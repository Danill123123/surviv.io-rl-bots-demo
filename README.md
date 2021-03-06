# surviv.io-rl-bots-demo

## Проект - создать RL-агента для игры https://surviv.io/

Если агента просто закинуть в игру через selenium и заставить обучаться на картинке-скриншоте вкладки, то потребуется слишком много времени для получения хорошего результата. Поэтому приходим к выводу, что нужно предобучить агента на видеозаписях-летсплеях некоторых игроков, например: https://www.youtube.com/watch?v=ERDmPJ_0QJc&t= с помощью методов, позволяющих использовать чужой опыт (как минимум, DQN).

Чтобы предобучить агента по видео, нужно знать state (картинка) и action(s) в каждый момент времени, поэтому приходим к пониманию, нужно вытащить информацию, что делает игрок в каждый момент времени. 
Создание автоматической разметки к видео. Возможно, понадобятся текстуры от разработчика в формате .png: https://drive.google.com/drive/folders/1qhaDdNCsisBu_7gvMNmyn_zkG4kyAZix
______________________________________________________________________________

## CV-Задачи для создания разметки (состояние1-действие-состояние2-награда):
- [x] 1)  Распознавать направление движения и нажатие клавиш [W][A][S][D]
- [x] 2)  Распознавать координаты курсора
- [x] 3)	Распознавать цифры для распознавания:
  - лутания предмета (или выбрасывания)
  - стрельбы
  - зума
  - уровня каски, брони и рюкзака
  - количества фрагов
  - количества оставшихся в живых игроков
- [x] 4) Распознавать, на каких кадрах карта открыта во весь экран (для сохранения инвентаря в последнем состоянии)
- [x] 5) Распознавать % HP и % SP
- [x] 6) Распознавать использование предмета (в центре экрана появилась табличка "Using...") и перезарядку оружия (в центре экрана появилась табличка "Reloading...")
- [x] 7) Распознавать открытие/закрытие всех дверей (в центре экрана появляется табличка "Open/Close...")
- [x] 8) Распознавать активное оружие, которое игрок держит в данный момент (1,2,3 или 4)
- [x] 9) Распознавать лутание нового оружия 
- [x] 10) Распознавать атаки рукой/холодным оружием
- [x] 11)	Сделать общий пайплайн обработки одного летсплея. Решить, что делать с разными координатами всех цифр и надписей (для разных видосов масштаб интерфейса может быть разным) - привлекаем разметчиков 
- [ ] 12)	Создать базу данных видосов, прогнать каждый из видосов через общий пайплайн. Создать датасет в нужном виде четверок (состояние1-действие-состояние2-награда)

## RL-Задачи для выбора и реализации алгоритма:
- [x] 1) QDN для google dino (CV+RL)
- [ ] 2) Попробовать прикрутить дефолтный QDN
- [ ] 3) Чекнуть, какую архитектуру обучали OpenAI для Dota2 (big LSTM?) и каким образом
- [ ] 4) Посерчить другие алгоритмы, позволяющие использовать чужой опыт

## DevOps-Задачи:
- [x] 1) Научиться управлять агентом через selenium
- [x] 2) Потестить время отклика сайта после команды селениума
- [x] 3) Подготовить скрипт, управляющий агентом через селениум (все кнопки и кликанья мышкой)
- [ ] 4) Решить, как будем получать состояние инвентаря агента в реальной игре (парсинг html-кода или через CV-алгоритмы)
- [ ] 5) Найти платформу/сайт/другое для того, чтобы любой человек мог наблюдать за действиями запущеного агента в реальной игре (мультиплеер)

______________________________________________________________________________
Доп заметки:
- аугментация данных: из 1 видео получим 4: если каждый кадр отражать зеркально, получим 4 кадра с разными действиями персонажа
