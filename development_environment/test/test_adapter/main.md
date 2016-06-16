# Запуск Nunit тестов в среде Visual Studio 2015 без Reshaper #

---

Для запуска Nunit тестов без установки в систему JetBrains ReSharper (как для Visual Studio 2010)  необходимо установить в проекты содержащие тесты, компонент
[NUnit Test Adapter](https://www.nuget.org/packages/NUnitTestAdapter/) с помощью NuGet Package Manager или вручную скачав
[отсюда](https://development.nesterof.com/development_environment/test/test_adapter/_file/NUnitVisualStudioTestAdapter-2.0.0.vsix). **Внимание! устанавливается версия
NUnit Test Adapter без Framework (в NuGet Gallery присутствует расширение [NUnitTestAdapter.WithFramework](https://www.nuget.org/packages/NUnitTestAdapter.WithFramework/)) **

Проекты содержащие [Nunit Framework](http://nunit.org/index.php?p=download) по состоянию проекта на 16.03.2016 (в проекте используется версия **2.6.4**):

* BarcodeLibTest
* DataSets
* DataSetsTest
* ExcelReport
* ExchangeDataWorker
* FTPClient
* Pila
* PrintFill
* Raspil
* SpsExchangeServer
* WorkPriceUpdater

*Это делается единожды, при первой настройке проекта, после перехода с VS2010 на VS2015 *