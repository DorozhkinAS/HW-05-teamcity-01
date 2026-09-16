
# 09-ci-05-teamcity (Домашнее задание к занятию 11 «Teamcity»)

## Подготовка к выполнению

### Teamcity

Подготовка виртуальных машин:
``` bash
terrafrom apply
```
![PrepareTeamcity](./pictures/0_Teamcity_Terraform_Apply.png)

Веб браузер http://<IP_Teamcity_Server>:8111
![TeamcityFirst](./pictures/0_Teamcity_First_Start.png)

Добавление агента:
![TeamcityAddAgent](./pictures/0_Add_Agent.png)

Добавление форка https://github.com/aragastmatb/example-teamcity.git в GitFlic
![TeamcityAddFork](./pictures/0_Gitflic_Fork_Repo.png)

### Nexus

Подготовка виртуальных машин:
``` bash
terrafrom apply
```
![PrepareNexus](./pictures/0_Nexus_Terraform_Apply.png)

Подготовка конфигурации:
``` bash
ansible-playbook -i ./inventory/hosts.yml site.yml
```
![AnsibleNexus](./pictures/0_Nexus_Ansible.png)

### Web GUI
![NexusGUI](./pictures/0_Nexus_Web.png)
![TeamcityGUI](./pictures/0_Teamcity_Web.png)

## Основная часть

### 1,2. Создание проекта, autodetect конфигурации
![Add](./pictures/2_Autodetect.png)

### 3. Первая сборка
![Build](./pictures/3_Build.png)

### 4. Смена условий сборки
![Build1](./pictures/4_If.png)

### 5. settings.xml
[settings.xml](./add/settings.xml)

### 6. pom.xml
[pom.xml](./add/pom.xml)

### 7. Сборка master
![Build2](./pictures/7_Build.png)
Проверка артефакта в nexus:
![Nexus](./pictures/7_Nexus.png)

### 8. Миграция в репозиторий.
![BuildConfig](./pictures/8_Build_Config.png)

### 9. Ветка feature/add_reply
![Branch](./pictures/9_New_Branch.png)

### 10. Добавление метода
![Method1](./pictures/10_Method1.png)
![Method2](./pictures/10_Method2.png)

### 11. Тесты
![Tests](./pictures/11_Test.png)

### 12,13. Сборка feature/add_reply
![Build](./pictures/13_Build.png)
![Tests](./pictures/13_Test.png)

### 14. Merge
![Merge](./pictures/14_Merge.png)

### 15. No Master
![NoMaster](./pictures/15_No_Master.png)

### 15. Nexus 
![NexusJar](./pictures/16_Jar.png)

### 16,17. Build, log
![Build](./pictures/17_Build.png)
![BuildLog](./pictures/17_Build_Log.png)

### 18. Синхронизация Teamcity => Repo
![Sync](./pictures/18_Sync.png)
