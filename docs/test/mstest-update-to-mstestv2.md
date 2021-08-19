---
title: Eseguire l'aggiornamento a MSTestV2
description: Informazioni su come eseguire l'aggiornamento da MSTestV1 a MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 68ca8dbe123fd0585a321fbefd49fd61713f4329
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038448"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Eseguire l'aggiornamento da MSTestV1 a MSTestV2

È possibile aggiornare il progetto di test ridestinando la versione di MSTest a cui si fa riferimento nel file con estensione *csproj* da MSTestV1 a MSTestV2. Non tutte le funzionalità di MSTestV1 sono state inoltrate in MSTestV2, pertanto potrebbero essere necessarie alcune modifiche per risolvere gli errori. Per informazioni sulle funzionalità che non funzioneranno più, vedere Funzionalità msTestV1 non supportate [in MSTestV2.](#mstestv1-features-that-are-not-supported-in-mstestv2) Alcuni di questi potrebbero dover essere rimossi dai test.

1. Rimuovere il riferimento all'assembly a Microsoft.VisualStudio.QualityTools.UnitTestFramework dal unit test progetto.
2. Aggiungere NuGet riferimenti al pacchetto a MSTestV2, inclusi i pacchetti [MSTest.TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) e [MSTest.TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) nuget.org. È possibile installare i pacchetti nella console NuGet Gestione pacchetti con i comandi seguenti:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Esempio di csproj in stile precedente

File *con estensione csproj* di esempio per MSTestV1:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

File *con estensione csproj* di esempio che ha ora come destinazione MSTestV2:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> I progetti di test che sono test codificati dell'interfaccia utente o test di carico Web non sono compatibili con MSTestV2. Questi tipi di progetto sono stati deprecati. Per altre informazioni, [vedere Deprecazione del test codificato dell'interfaccia utente e](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) Deprecazione del test di carico [Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>Csproj di tipo SDK (.NET Core e .NET 5)

Se il *file con estensione csproj* è il file con estensione *csproj* di tipo SDK più recente, probabilmente si sta già usando MSTestV2. È possibile trovare i NuGet per [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) e [l'adapter MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) NuGet.

Esempio:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Perché eseguire l'aggiornamento a MSTestV2?

Nel 2016 è stato rilasciato il passaggio successivo per l'evoluzione del framework MSTest con MSTestV2. Per altre informazioni su questa modifica, vedere il post di [blog dell'annuncio](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/).

* MSTestV2 è più facilmente acquisito e aggiornato perché viene recapitato come NuGet [pacchetto](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 è [open source](https://github.com/microsoft/testfx).
* Supporto uniforme della piattaforma app: MSTestV2 è un'implementazione convergente che offre un supporto uniforme della piattaforma app in .NET Framework, .NET Core, ASP.NET Core e UWP. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* L'implementazione è completamente multipiattaforma (Windows, Linux, Mac). [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 supporta la destinazione .NET Framework 4.5.0 e versioni successive, .NET Core 1.0 e versioni successive (Universal Windows Apps 10+), ASP.NET Core 1.0 e versioni successive e .NET 5 e versioni successive.
* Fornisce un meccanismo di estendibilità uniforme per l'utente finale singolo. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Fornisce un supporto uniforme `DataRow` per tutti i progetti di test basati su MSTest. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Consente di posizionare `TestCategory` l'attributo al livello di una classe o di un assembly. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* I metodi di test delle classi di base definiti in un altro assembly vengono ora individuati ed eseguiti dalla classe Test derivata. Questa modifica comporta un comportamento coerente con i tipi di classe di test derivati. Se questo comportamento non è necessario per motivi di compatibilità, può essere modificato usando le impostazioni di esecuzione seguenti:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Fornisce un controllo più granulare sull'esecuzione parallela tramite [l'esecuzione parallela in assembly](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) dei test. Ciò consente l'esecuzione di test all'interno di un assembly in parallelo.
* Il `TestCleanup` metodo su un oggetto viene `TestClass` richiamato anche se il metodo corrispondente ha `TestInitialize` esito negativo. [Dettagli del problema](https://github.com/Microsoft/testfx/issues/250).
* Il tempo impiegato da `AssemblyInitialize` e `ClassInitialize` non viene conteggiato per la durata del test. Questa modifica limita l'impatto sul timeout di un test.
* I test che non possono essere eseguiti possono essere configurati per essere contrassegnati come non riusciti tramite il tag , che fa parte del nodo `MapNotRunnableToFailed` dell'adapter nel `.runsettings` file.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Funzionalità MSTestV1 non supportate in MSTestV2

*   I test non possono essere inclusi in un "test ordinato".
*   L'adapter non supporta la configurazione tramite un file *con estensione testsettings.* Usare il nuovo file [ *con estensione runsettings* per](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) la configurazione dell'esecuzione dei test.
*   L'adapter non supporta gli elenchi di test specificati come file con estensione *vsmdi.*
*   I tipi "Coded UI Test Project" e "Web Performance and Load Test Project" non sono supportati. Per altre informazioni, [vedere Deprecazione del test codificato dell'interfaccia utente e](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) Deprecazione del test di carico [Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>Vedi anche

- [Configurare le esecuzioni dei test con `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire il debug di unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md)
