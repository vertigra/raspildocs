# Запуск Nunit тестов

---

Для запуска Nunit тестов необходимо установить в проекты содержащие тесты, компонент  
[NUnit Test Adapter](https://www.nuget.org/packages/NUnitTestAdapter/) 
с помощью NuGet Package Manager или вручную скачав [отсюда](files/NUnitVisualStudioTestAdapter-2.0.0.vsix).   
**Внимание! устанавливается версия NUnit Test Adapter без Framework      
(в NuGet Gallery присутствует расширение [NUnitTestAdapter.WithFramework](https://www.nuget.org/packages/NUnitTestAdapter.WithFramework/)) **

Проекты содержащие [Nunit Framework](http://nunit.org/index.php?p=download) 
(в проекте используется версия **2.6.4**):

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

