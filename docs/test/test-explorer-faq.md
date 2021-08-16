---
title: Domande frequenti su Esplora test
description: Fare riferimento a queste domande frequenti su Visual Studio Test Explorer, che includono alcuni problemi comuni.
ms.custom: SEO-VS-2020
ms.date: 06/25/2020
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 6e5cd80c4523d74b2cf26887362e9bbffaa82d0f5369aa0f4666b02edc894a05
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352456"
---
# <a name="visual-studio-test-explorer-faq"></a>Domande frequenti su Esplora test di Visual Studio

## <a name="dynamic-test-discovery"></a>Individuazione dei test dinamici

**Esplora test non individua i test definiti dinamicamente. Ad esempio, teorie, adattatori personalizzati, tratti personalizzati, #ifdefs e così via. Come è possibile individuare questi test?**

::: moniker range=">=vs-2019"
Compilare il progetto per eseguire l'individuazione basata su assembly.
::: moniker-end
::: moniker range="vs-2017"
Compilare il progetto e assicurarsi che l'individuazione basata su assembly sia attivata in **Strumenti** > **Opzioni** > **Test**.
::: moniker-end
L'[individuazione dei test in tempo reale](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) è l'individuazione dei test in base all'origine. Non è in grado di individuare test che usano teorie, adattatori personalizzati, tratti personalizzati, istruzioni e altro ancora perché sono `#ifdef` definiti in fase di esecuzione. Per l'individuazione accurata di questi test è necessaria una compilazione. In Visual Studio 2017 versione 15.6 e versioni successive l'individuazione basata su assembly (agente di individuazione tradizionale) viene eseguita solo dopo le compilazioni. Questa impostazione significa che l'individuazione dei test in tempo reale consente di individuare il maggior numero possibile di test durante la modifica e che l'individuazione basata su assembly consente la visualizzazione dei test definiti in modo dinamico dopo una compilazione. L'individuazione dei test in tempo reale migliora la velocità di risposta, consentendo tuttavia di ottenere risultati precisi e completi dopo una compilazione.

## <a name="test-explorer--plus-symbol"></a>'+' (segno più) di Esplora test

**Cosa significa il simbolo '+' (più) visualizzato nella prima riga di Esplora test?**

Il simbolo '+' (più) indica che possono essere individuati ulteriori test dopo una compilazione quando viene eseguita l'individuazione basata su assembly. Il simbolo viene visualizzato se nel progetto vengono rilevati test definiti in modo dinamico.

![Riga di riepilogo con segno più](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Individuazione basata su assembly

**L'individuazione basata su assembly non funziona più per il progetto. Ricerca per categorie riattivarlo?**

Passare a **Strumenti** Opzioni Test e selezionare la casella Individuare anche i test dagli >  >  **assembly compilati dopo le compilazioni.**

![Opzione basata su assembly](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Individuazione dei test in tempo reale

**I test vengono ora visualizzati in Esplora test durante la digitazione, senza dover compilare il progetto. Cosa è cambiato?**

Questa funzionalità è denominata [individuazione dei test in tempo reale](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Usa un analizzatore Roslyn per trovare i test e popolare Esplora test in tempo reale, senza che sia necessario compilare il progetto. Per altre informazioni sul comportamento dell'individuazione dei test per i test definiti in modo dinamico, ad esempio teorie o tratti personalizzati, vedere [Individuazione dei test dinamici](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Compatibilità dell'individuazione dei test in tempo reale

**Quali linguaggi e framework di test possono usare l'individuazione dei test in tempo reale?**

L'[individuazione dei test in tempo reale](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) funziona solo per i linguaggi gestiti (C# e Visual Basic), perché viene compilata con il compilatore Roslyn. Per il momento, l'individuazione dei test in tempo reale funziona solo per i framework xUnit, NUnit e MSTest.

## <a name="test-explorer-logs"></a>Log di Esplora test

**Come è possibile attivare i log per Esplora test?**

Passare a **Strumenti**  >  **Opzioni**  >  **Test** e individuare la sezione Registrazione.

## <a name="uwp-test-discovery"></a>Individuazione dei test UWP

**Perché i test nei progetti UWP vengono individuati solo dopo la distribuzione dell'app?**

I test UWP usano un runtime diverso come destinazione quando l'app viene distribuita. Questo significa che per trovare i test in modo accurato per i progetti UWP non è sufficiente compilare il progetto, ma è anche necessario distribuirlo.

## <a name="test-explorer-sorting"></a>Ordinamento di Esplora test

**Come funziona l'ordinamento dei risultati di test nella visualizzazione gerarchia?**

Nella visualizzazione gerarchia i test sono disposti in ordine alfabetico anziché in base al risultato. Le impostazioni precedenti raggruppano i risultati dei test in base al risultato e quindi in ordine alfabetico. È comunque possibile abilitare l'ordinamento in base al risultato facendo clic con il pulsante destro del mouse sull'intestazione di colonna in Esplora test, abilitando la colonna Stato e quindi facendo clic sull'intestazione di colonna Stato per applicare l'ordinamento a tale colonna. È possibile fornire commenti e suggerimenti sulla progettazione in questo [GitHub problema](https://github.com/Microsoft/vstest/issues/1425).

## <a name="test-explorer-hierarchy-view"></a>Visualizzazione gerarchia in Esplora test

**Nella visualizzazione gerarchia sono presenti icone passate, non riuscite, ignorate e non eseguite accanto ai raggruppamenti dei nodi padre. Cosa significano queste icone?**

Le icone accanto ai raggruppamenti Progetto, Spazio dei nomi e Classe indicano lo stato dei test all'interno di tale raggruppamento. Vedere la tabella seguente.

![Icone nella gerarchia in Esplora test](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Ricerca per percorso file

**Nella casella di ricerca Esplora test non è più disponibile un filtro per il percorso file.**

Il filtro per il percorso file nella casella di ricerca **Esplora test** è stato rimosso in Visual Studio 2017 versione 15.7. Questa funzionalità era poco usata ed Esplora Test può recuperare i metodi di test più velocemente se la funzionalità viene esclusa. Se questa modifica interrompe il flusso di sviluppo, comunicarlo aggiungendo un commento nella [community degli sviluppatori](https://aka.ms/feedback/suggest?space=8).

## <a name="remove-undocumented-interfaces"></a>Rimuovere le interfacce non documentate

**Alcune API correlate ai test non sono più presenti in Visual Studio 2019. Cosa è cambiato?**

In Visual Studio 2019, verranno rimosse alcune API di finestra di test in precedenza contrassegnate come pubbliche, ma mai documentate ufficialmente. Sono state contrassegnate come "deprecate" in Visual Studio 2017 per avvisare tempestivamente chi gestisce le estensioni. In base a quanto osservato, sono pochissime le estensioni che hanno rilevato queste API e hanno dipendenze dalle stesse. Sono incluse `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken` e `SearchFilterTokenType`. Se questa modifica interessa l'estensione in uso, segnalare un bug in [Developer Community](https://aka.ms/feedback/suggest?space=8).

## <a name="test-adapter-nuget-reference"></a>Riferimento NuGet all'adattatore di test

**In Visual Studio 2017 versione 15.8 i test vengono individuati, ma non eseguiti.**

Tutti i progetti di test devono includere il riferimento NuGet all'adattatore di test .NET nel relativo file csproj. In caso contrario, viene visualizzato l'output di test seguente nel progetto se viene avviata l'individuazione da parte di un'estensione dell'adattatore di test dopo una compilazione o se l'utente tenta di eseguire i test selezionati:

**Il progetto {} di test non fa riferimento ad alcun adattatore NuGet .NET. L'individuazione o l'esecuzione dei test potrebbe non funzionare per questo progetto. È consigliabile fare riferimento NuGet adattatori di test in ogni progetto di test .NET nella soluzione.**

Invece di usare le estensioni dell'adattatore di test, i progetti devono usare i pacchetti NuGet dell'adattatore di test. Questo requisito migliora notevolmente le prestazioni e causa meno problemi con l'integrazione continua. Altre informazioni sulla deprecazione dell'estensione dell'adattatore di test .NET sono disponibili nelle [note sulla versione](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Se si usa l'adattatore di test NUnit 2 e non è possibile eseguire la migrazione all'adattatore di test NUnit 3, è possibile disattivare questo nuovo comportamento di individuazione in Visual Studio versione 15.8 **in** Strumenti  >  **Opzioni**  >  **Test**.

![Comportamento dell'adattatore nelle opzioni degli strumenti di Esplora test](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>Oggetto TestContainer UWP non trovato

**I test UWP non vengono più eseguiti in Visual Studio 2017 versione 15.7 e successive.**

I progetti di test UWP recenti specificano una proprietà di compilazione della piattaforma di test che consente di migliorare le prestazioni durante l'identificazione delle app di test. Se si dispone di un progetto di test UWP inizializzato prima Visual Studio versione 15.7, è possibile che venga visualizzato questo errore in **Test di**  >  **output**:

**System.AggregateException: Si sono verificati uno o più errori. ---> System.InvalidOperationException: Impossibile trovare il seguente oggetto TestContainer {} in Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync>d__61.MoveNext()**

Per correggere l'errore: 

- Aggiornare la proprietà di compilazione del progetto di test usando il codice seguente:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aggiornare la versione SDK di TestPlatform usando il codice seguente:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Uso delle funzionalità di anteprima

In Visual Studio 2019 è possibile acconsentire esplicitamente alle funzionalità di anteprima in Strumenti **> opzioni > ambiente > funzionalità di anteprima**.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Uso dei flag di funzionalità

**Come è possibile attivare i flag di funzionalità per provare le nuove funzionalità di test?**

I flag di funzionalità vengono usati per fornire parti del prodotto sperimentali o non completate agli utenti ansiosi di fornire commenti e suggerimenti prima del rilascio ufficiale delle funzionalità. Questi flag potrebbero destabilizzare l'esperienza dell'IDE. Usarli solo in ambienti di sviluppo protetti, come le macchine virtuali. I flag di funzionalità sono sempre impostazioni usate a proprio rischio. È possibile attivare le funzionalità sperimentali con l'[estensione per i flag di funzionalità](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) o dal prompt dei comandi per sviluppatori.

![Estensione per i flag di funzionalità](media/testex-featureflag.png)

Per attivare un flag di funzionalità tramite il prompt dei comandi per sviluppatori di Visual Studio, usare il comando seguente. Modificare il percorso in cui è installato Visual Studio nel computer e modificare la chiave del Registro di sistema per il flag di funzionalità necessario.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> È possibile disattivare il flag con lo stesso comando, usando il valore 0 anziché 1 dopo dword.
::: moniker-end
## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code](/previous-versions/dd293546(v=vs.110)) (Creare ed eseguire unit test per il codice esistente)
- [Eseguire unit test del codice](unit-test-your-code.md)
- [Domande frequenti su Live Unit Testing](live-unit-testing-faq.yml)