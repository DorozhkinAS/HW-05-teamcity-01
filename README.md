# Домашнее задание к занятию 11 «Teamcity» - `Дорожкин Артем`

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

## Решение - подготовка к выполнению

Создал три ВМ в соответствии с заданием:

<img width="1192" height="273" alt="1" src="https://github.com/user-attachments/assets/6e881a52-9949-4724-8177-c9e4fddde92e" />

Авторизовал агент:

<img width="1266" height="384" alt="2" src="https://github.com/user-attachments/assets/6c3c8272-4e3d-4f25-be59-85718c50a973" />

Запустил [playbook]

<img width="901" height="436" alt="3" src="https://github.com/user-attachments/assets/136cee8f-c4ed-4cc7-9e5b-0433311c2837" />

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
8. Мигрируйте `build configuration` в репозиторий.
9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.

## Решение - основная часть

1. Создал новый проект в teamcity на основе fork.
2. Сделал autodetect конфигурации.
3. Сохранил необходимые шаги, запустил первую сборку master. Сборка прошла успешно:

<img width="1041" height="497" alt="10" src="https://github.com/user-attachments/assets/d6316a9c-8c03-47e0-97f0-0f51f9d91007" />

4. Поменял условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`:

<img width="958" height="656" alt="11" src="https://github.com/user-attachments/assets/3cd2273a-b058-4d33-8700-69ae9334dc98" />

5. Для deploy загрузил [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus:

<img width="989" height="472" alt="12" src="https://github.com/user-attachments/assets/0e6553bc-b8a4-4676-bcc7-4f523af0b3c4" />

6. В pom.xml поменял ссылки на репозиторий и nexus:

<img width="573" height="156" alt="13" src="https://github.com/user-attachments/assets/f72ece42-d165-426f-a5e1-b9f0fbb263d3" />

7. Запустил сборку по master, убедился, что всё прошло успешно и артефакт появился в nexus:

<img width="583" height="504" alt="20" src="https://github.com/user-attachments/assets/961043b4-fa0a-48f2-870c-22361b3b9f5c" />

8. Мигрировал `build configuration` в репозиторий:

<img width="737" height="475" alt="21" src="https://github.com/user-attachments/assets/35fc8c5a-831d-48bc-97d2-ca61fd3ca7dc" />

<img width="701" height="447" alt="22" src="https://github.com/user-attachments/assets/f7cf2382-931d-4f2a-abbc-7c99d3805a4d" />

9. Создал отдельную ветку `feature/add_reply` в репозитории.
10. Написал новый метод для класса Welcomer: метод возвращает произвольную реплику, содержащую слово `hunter`:

<img width="682" height="466" alt="23" src="https://github.com/user-attachments/assets/02cd3e7b-1ae3-4d92-9256-cd83d494085a" />

11. Дополнил тест для нового метода на поиск слова `hunter` в новой реплике:

<img width="667" height="586" alt="24" src="https://github.com/user-attachments/assets/91ec591d-0d16-4a7e-9991-e6155048e4aa" />

12. Сделал push всех изменений в новую ветку репозитория.
13. Убедился, что сборка самостоятельно запустилась, тесты прошли успешно:

<img width="795" height="394" alt="25" src="https://github.com/user-attachments/assets/76f374c8-55cd-4703-9408-26a9bf4bcd02" />

14. Сделал `Merge` ветки `feature/add_reply` в `master`.

<img width="824" height="105" alt="26" src="https://github.com/user-attachments/assets/c14d511e-bad1-4830-ab9d-24468e626d82" />

15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
17. Провел повторную сборку мастера, но к сожалению сборка не прошла успешно и артефакты не собраны. Пробовал изменить версию в `pom.xml` на 0.0.2, но это не помогло. Все равно сборка не прошла:

<img width="716" height="283" alt="27" src="https://github.com/user-attachments/assets/9f1df2a6-a71b-4186-96b5-854b7e9cd6a8" />

19. В ответе пришлите ссылку на репозиторий.

https://github.com/artmur1/example-teamcity прислать ссылку на мой репозиторий

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
