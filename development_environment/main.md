# Среда и инструменты разработки #

---

## Основные среды разработки и проектирования ##

Разработка под .NET 4.0.  
На данный момент для разработки под .net используется:  

* Visual Studio 2010 Professional ENG (переход на VS 2015 Comunity)
* Resharper 7 (под вопросом)
* IB Expert
* SQL Manager 2005 for Interbase/Firebird (необязательный)
* TortiesHg 3.7 и выше(можно использовать свое приложение для работы с HG)

Используемые сторонние библиотеки, компоненты и т.д.:

* Microsoft Office 2000 и выше (Excel API библионтеки от MS Office 2000 лежат уже в проекте)
* Firebird 1.5.6.5026 (СУБД)
* Firebird .NET Provider 4.6.4.0 (как пакет Nuget в проекте) (переход на 4.10.0.0)
* Firebird DDEX Provider 4.6.4.0 (необходимо для диалога подключения) (переход на 4.10.0.0)
* NUnit 2.6.2(версия от 2.6.х и выше, но не 3.0, пакет Nuget) (переход на последнюю версию - в планах)
* NHibernate 3.4 (пакет Nuget)

Разработка на Java 7 (Android).
На данный момент для разработки под java используется:

* Android Studio 1.5
* Genymotion (эмулятор)
* SqliteBrowser
* Плагин Android Studio для работы с Mercurial совместно TortiesHg.

Используемые сторонние библиотеки, компоненты и т.д.:

* Jaybird2_2_4.jar
* me.dm7.barcodescanner:zxing:1.8.4
* com.github.afollestad.material-dialogs:commons:0.8.5.7@aar'
* org.mockito:mockito-core:1.10.19
* junit:junit:4.12

## IDE ##

[Ветка описания настроек интергрированных средств разработки](components/main), для используемых языков програмирования в проекте.

## Компоненты ##

[Настройка компонентов операционной системы, библиотек, плагинов](components/main.md)

## Система управления версиями ##

[Ветка о настройках систем управления версиями и нюансов работы с ними](vcs/main.md)

## Тесты ##

[Запуск Nunit тестов](test_adapter/main.md)

## Firebird ##

[Настройка Firebird](firebird/main.md)