---
title: Aggiornamento a MSTestV2
description: Informazioni su come eseguire l'aggiornamento da MSTestV1 a MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366258"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Eseguire l'aggiornamento da MSTestV1 a MSTestV2

È possibile aggiornare il progetto di test ridestinando la versione MSTest a cui si fa riferimento nel *. csproj* da MSTestV1 a MSTestV2. Non tutte le funzionalità di MSTestV1 sono state introdotte in MSTestV2, quindi alcune modifiche potrebbero essere necessarie per risolvere gli errori. Vedere le [funzionalità di MSTestV1 che non sono supportate in MSTestV2](#mstestv1-features-that-are-not-supported-in-mstestv2) per comprendere quali funzionalità non funzioneranno più. È possibile che alcuni di questi elementi debbano essere rimossi dai test.

1. Rimuovere il riferimento all'assembly in Microsoft. VisualStudio. QualityTools. UnitTestFramework dal progetto unit test.
2. Aggiungere i riferimenti ai pacchetti NuGet a MSTestV2, inclusi i pacchetti [MSTest. TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) e [MSTest. TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) in NuGet.org. È possibile installare i pacchetti nella console di gestione pacchetti NuGet con i comandi seguenti:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Esempio di csproj vecchio stile

Esempio di targeting *. csproj* MSTestV1:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

Sample *. csproj* ora destinato a MSTestV2:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> I progetti di test che sono test codificati dell'interfaccia utente o test di carico Web non sono compatibili con MSTestV2. Questi tipi di progetto sono stati deprecati. Per altre informazioni, vedere [deprecazione del test codificato dell'interfaccia utente](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) e [deprecazione del test di carico Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>Csproj di tipo SDK (.NET Core e .NET 5)

Se il *. csproj* è il più recente *. csproj* di tipo SDK, è probabile che si stia già usando MSTestV2. È possibile trovare i pacchetti NuGet per [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) e l' [Adapter MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) in NuGet.

Esempio:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Perché eseguire l'aggiornamento a MSTestV2?

In 2016 è stato rilasciato il passaggio successivo per l'evoluzione del framework MSTest con MSTestV2. Per altre informazioni su questa modifica, vedere il [post di Blog](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)sull'annuncio.

* MSTestV2 è più facile da acquisire e aggiornare perché viene fornito come [pacchetto NuGet](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 è [Open Source](https://github.com/microsoft/testfx).
* Supporto per app-Platform uniformi: MSTestV2 è un'implementazione convergente che offre un supporto uniforme per le piattaforme app in .NET Framework, .NET Core, ASP.NET Core e UWP. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* L'implementazione è completamente multipiattaforma (Windows, Linux, Mac). [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 supporta la destinazione .NET Framework 4.5.0 e versioni successive, .NET Core 1,0 e versioni successive (app di Windows universale 10 +), ASP.NET Core 1,0 e versioni successive e .NET 5 e versioni successive.
* Fornisce un meccanismo uniforme di estensibilità degli utenti finali. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Fornisce un `DataRow` supporto uniforme per tutti i progetti di test basati su MSTest. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Consente di inserire l' `TestCategory` attributo al livello di una classe o di un assembly. [Altre informazioni](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* I metodi di test delle classi base definite in un altro assembly vengono ora individuati ed eseguiti dalla classe di test derivata. Questa modifica comporta un comportamento coerente con i tipi di classe di test derivati. Se questo comportamento non è necessario per motivi di compatibilità, può essere modificato nuovamente utilizzando le seguenti impostazioni esecuzione test:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Fornisce un controllo più granulare sull'esecuzione parallela tramite [l'esecuzione parallela in assembly](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) dei test. In questo modo è possibile eseguire i test in un assembly in parallelo.
* Il `TestCleanup` metodo su un oggetto `TestClass` viene richiamato anche se il metodo corrispondente ha `TestInitialize` esito negativo. [Dettagli del problema](https://github.com/Microsoft/testfx/issues/250).
* Il tempo impiegato da `AssemblyInitialize` e `ClassInitialize` non viene conteggiato per la durata del test. Questa modifica limita l'effetto su un timeout del test.
* I test non eseguibili possono essere configurati in modo da essere contrassegnati come non riusciti tramite il `MapNotRunnableToFailed` tag, che fa parte del nodo Adapter nel `.runsettings` file.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Funzionalità MSTestV1 non supportate in MSTestV2

*   I test non possono essere inclusi in un "test ordinato".
*   L'adapter non supporta la configurazione tramite un file con estensione *testsettings* . Utilizzare il nuovo [file con *estensione runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) per la configurazione dell'esecuzione dei test.
*   L'adapter non supporta gli elenchi di test specificati come file con *estensione vsmdi* .
*   I tipi "progetto di test codificato dell'interfaccia utente" e "progetto di test di carico e prestazioni Web" non sono supportati. Per altre informazioni, vedere [deprecazione del test codificato dell'interfaccia utente](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) e [deprecazione del test di carico Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>Vedi anche

- [Configurare esecuzioni dei test con `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire il debug di unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md)
