---
title: Domande frequenti su Esplora test di Visual Studio
ms.date: 1/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
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
manager: douge
ms.openlocfilehash: 4ac7aa7d9fbbf4e6f6ffbe5eafd82ff8f1e0bc44
ms.sourcegitcommit: e04e52bddf81239ad346efb4797f52e38de5cb98
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43054556"
---
# <a name="visual-studio-test-explorer-faq"></a>Domande frequenti su Esplora test di Visual Studio

## <a name="dynamic-test-discovery"></a>Individuazione dei test dinamici
**Esplora Test non individua i test definiti in modo dinamico. Ad esempio, teorie, adattatori personalizzati, tratti personalizzati, #ifdefs e così via. Come è possibile individuare questi test?**

  Compilare il progetto e verificare che l'individuazione basata su assembly sia attivata in **Strumenti** > **Opzioni** > **Test**.

  L'[individuazione dei test in tempo reale](https://go.microsoft.com/fwlink/?linkid=862824) è l'individuazione dei test in base all'origine. Questa funzionalità non consente di individuare test che usano teorie, adattatori personalizzati, tratti personalizzati, istruzioni `#ifdef` e così via, perché sono definiti in fase di esecuzione. Per l'individuazione accurata di questi test è necessaria una compilazione. Nelle versioni di anteprima 15.6, l'individuazione basata su assembly (agente di individuazione tradizionale) viene eseguita solo dopo le compilazioni. Questa impostazione significa che l'individuazione dei test in tempo reale consente di individuare il maggior numero possibile di test durante la modifica e che l'individuazione basata su assembly consente la visualizzazione dei test definiti in modo dinamico dopo una compilazione. L'individuazione dei test in tempo reale migliora la velocità di risposta, ma consente comunque di ottenere risultati accurati e completi dopo una compilazione.

## <a name="test-explorer--plus-symbol"></a>'+' (segno più) di Esplora test
**Cosa significa il simbolo '+' (più) visualizzato nella prima riga di Esplora test?**

  Il simbolo '+' (più) indica che possono essere individuati ulteriori test dopo una compilazione a condizione che sia attivata l'individuazione basata su assembly. Viene visualizzato se nel progetto vengono rilevati test definiti in modo dinamico.

  ![Riga di riepilogo con segno più](media/testex-plussymbol.png)

## <a name="assembly-based-discovery"></a>Individuazione basata su assembly
**L'individuazione basata su assembly non funziona più per un progetto. Come è possibile riattivarla?**

  Passare a **Strumenti** > **Opzioni** > **Test** e selezionare la casella **Individua anche i test di assembly compilati dopo le compilazioni.**

  ![Opzione basata su assembly](media/testex-toolsoptions.png)

## <a name="real-time-test-discovery"></a>Individuazione dei test in tempo reale
**I test vengono ora visualizzati in Esplora test durante la digitazione senza dover compilare il progetto. Cosa è cambiato?**

  Questa funzionalità è denominata [individuazione dei test in tempo reale](https://go.microsoft.com/fwlink/?linkid=862824). Usa un analizzatore Roslyn per individuare i test e popolare Esplora test in tempo reale, senza che sia necessario compilare il progetto. Per altre informazioni sul comportamento di individuazione dei test per i test definiti in modo dinamico, ad esempio teorie o tratti personalizzati, vedere la domanda 1.

## <a name="real-time-test-discovery-compatibility"></a>Compatibilità dell'individuazione dei test in tempo reale
**Quali linguaggi e framework di test possono usare l'individuazione dei test in tempo reale?**

  L'[individuazione dei test in tempo reale](https://go.microsoft.com/fwlink/?linkid=862824) funziona solo per i linguaggi gestiti (C# e Visual Basic), perché viene compilata con il compilatore Roslyn. Per il momento, l'individuazione dei test in tempo reale funziona solo per i framework xUnit, NUnit e MSTest.

## <a name="test-explorer-logs"></a>Log di Esplora test
**Come è possibile attivare i log per Esplora test?**

  Passare a **Strumenti** > **Opzioni** > **Test** e individuare la sezione Registrazione.

## <a name="uwp-test-discovery"></a>Individuazione dei test UWP
**Perché i test nei progetti UWP vengono individuati solo dopo la distribuzione dell'app?**

  I test UWP usano un runtime diverso come destinazione quando l'app viene distribuita. Questo significa che per individuare i test in modo accurato per i progetti UWP non è sufficiente compilare il progetto, ma è anche necessario distribuirlo.

## <a name="test-explorer-sorting"></a>Ordinamento di Esplora test
**Come funziona l'ordinamento dei risultati di test nella visualizzazione gerarchia?**

  Nella visualizzazione gerarchia i test sono disposti in ordine alfabetico anziché in base al risultato. Le altre impostazioni di raggruppamento solitamente dispongono i risultati dei test in base al risultato e poi in ordine alfabetico. Vedere le diverse opzioni di raggruppamento nell'immagine seguente per un confronto. È possibile inviare commenti e suggerimenti sulla progettazione [in questo problema GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Visualizzazione gerarchia in Esplora test
**Nella visualizzazione gerarchia, accanto ai raggruppamenti Progetto, Spazio dei nomi e Classe vengono visualizzate icone per i test superati, non superati, ignorati e non eseguiti. Cosa significano queste icone?**

  Le icone accanto ai raggruppamenti Progetto, Spazio dei nomi e Classe rispecchiano lo stato dei test all'interno di tale raggruppamento. Fare riferimento alla tabella riportata di seguito.

  ![Icone nella gerarchia in Esplora test](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Ricerca per percorso file
**Nella casella di ricerca Esplora test non è più disponibile un filtro per il percorso file.**

Il filtro per il percorso file nella casella di ricerca **Esplora test** è stato rimosso in Visual Studio 2017 versione 15.7 anteprima 3. Questa funzionalità era poco usata ed Esplora Test può recuperare i metodi di test più velocemente se la funzionalità viene esclusa. Se questa modifica interrompe il flusso di sviluppo di progetti in corso, comunicarlo aggiungendo un commento nella [community degli sviluppatori](https://developercommunity.visualstudio.com/).

## <a name="test-adapter-nuget-reference"></a>Riferimento NuGet all'adattatore di test
**In Visual Studio 2017 versione 15.8 i test vengono individuati, ma non eseguiti.**

Tutti i progetti di test devono includere il riferimento NuGet all'adattatore di test .NET nel relativo file csproj. In caso contrario, viene visualizzato l'output di test seguente nel progetto se viene avviata l'individuazione da parte di un'estensione dell'adattatore di test dopo una compilazione o se l'utente tenta di eseguire i test selezionati: 

Il **progetto di test{} non fa riferimento ad alcun adattatore NuGet .NET. L'individuazione o l'esecuzione dei test potrebbe non funzionare per questo progetto. È consigliabile fare riferimento agli adattatori di test NuGet in ogni progetto di test .NET nella soluzione.**

Invece di usare le estensioni dell'adattatore di test, i progetti devono usare i pacchetti NuGet dell'adattatore di test. Ciò migliora notevolmente le prestazioni e causa meno problemi con l'integrazione continua. Altre informazioni sulla deprecazione dell'estensione dell'adattatore di test .NET sono disponibili nelle [note sulla versione](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

## <a name="using-feature-flags"></a>Uso dei flag di funzionalità
**Come è possibile attivare i flag di funzionalità per provare le nuove funzionalità di test?**

I flag di funzionalità vengono usati per fornire parti del prodotto sperimentali o non completate agli utenti ansiosi di fornire commenti e suggerimenti prima del rilascio ufficiale delle funzionalità. Questi flag potrebbero destabilizzare l'esperienza dell'IDE. Usarli solo in ambienti di sviluppo protetti, come le macchine virtuali. I flag di funzionalità sono sempre impostazioni usate a proprio rischio. È possibile attivare le funzionalità sperimentali con l'[estensione per i flag di funzionalità](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) o dal prompt dei comandi per sviluppatori.

![Estensione per i flag di funzionalità](media/testex-featureflag.png)

Per attivare un flag di funzionalità tramite il prompt dei comandi per sviluppatori di Visual Studio, usare il comando seguente. Modificare il percorso in cui è installato Visual Studio nel computer in uso e modificare la chiave del Registro di sistema per il flag di funzionalità desiderato.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> È possibile disattivare il flag con lo stesso comando, usando il valore 0 anziché 1 dopo dword.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) (Creare ed eseguire unit test per il codice esistente)
- [Eseguire unit test del codice](unit-test-your-code.md)
- [Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)
