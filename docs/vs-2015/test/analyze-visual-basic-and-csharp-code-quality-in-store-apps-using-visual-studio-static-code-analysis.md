---
title: Analizza Visual Basic e C# la qualità del codice nelle app dello Store con l'analisi statica del codice
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7510b7fac5dfc633b88bd9f53347118a02227b92
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416650"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Analizzare la qualità del codice Visual Basic e C# nelle app dello Store con l'analisi statica del codice di Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Lo strumento di analisi del codice disponibile in Visual Studio Express esamina il codice alla ricerca di un set di errori comuni e di violazioni delle procedure di programmazione ottimali. Gli avvisi di analisi del codice sono diversi rispetto agli errori e avvisi del compilatore. Lo strumento di analisi del codice cerca infatti modelli di codice specifici che risultano validi ma che potrebbero causare problemi a te o ad altre persone che utilizzano il codice. L'analisi del codice può inoltre trovare difetti all'interno del codice che di solito sono difficili da individuare tramite l'esecuzione di test. L'esecuzione dello strumento di analisi del codice a intervalli regolari durante il processo di sviluppo può migliorare la qualità dell'app completata.

> [!NOTE]
> In Visual Studio Ultimate, Visual Studio Premium e Visual Studio Professional puoi utilizzare la funzionalità di analisi del codice. Vedere [Analisi della qualità dell'applicazione tramite gli strumenti di analisi del codice](https://msdn.microsoft.com/library/dd264897.aspx) in MSDN Library.

## <a name="in-this-topic"></a>Contenuto dell'argomento
 Puoi acquisire informazioni su:

 [Esecuzione dell'analisi del codice](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Analizzare e risolvere gli avvisi di analisi del codice](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Eliminazione degli avvisi di analisi del codice](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Ricerca e filtro dei risultati dell'analisi del codice](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Avvisi di analisi del codice Visual Basic e C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

## <a name="BKMK_Run"></a> Esecuzione dell'analisi del codice
 Per eseguire l'analisi del codice nella soluzione di Visual Studio:

- Dal menu **Genera** scegliere **Esegui analisi del codice sulla soluzione**.

  Per eseguire automaticamente l'analisi codice ogni volta che compili un progetto:

1. Fare clic con il pulsante destro del mouse sul nome del progetto in Esplora soluzioni e quindi scegliere **Proprietà**.

2. Nella pagina delle proprietà del progetto, scegliere **Analisi codice** e quindi **Attiva analisi codice in fase di compilazione (definisce la costante CODE_ANALYSIS)** .

   La soluzione viene compilata e viene eseguita l'analisi del codice. I risultati vengono visualizzati nella finestra Analisi codice.

   ![Finestra Analisi codice](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

## <a name="BKMK_Analyze"></a> Analizzare e risolvere gli avvisi di analisi del codice
 Per analizzare un avviso specifico, fai clic sul titolo dell'avviso nella finestra Analisi codice. L'avviso si espande per visualizzare le informazioni dettagliate sul problema.

 ![Avviso di analisi del codice espanso](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Quando si espande un avviso, la riga di codice che ha provocato l'avviso viene evidenziata nell'editor del codice di Visual Studio.

 ![Evidenziazione del testo di analisi del codice](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Dopo aver compreso il problema, potrai risolverlo nel codice. Eseguire quindi di nuovo l'analisi del codice per verificare che l'avviso non venga più visualizzato nella finestra Analisi codice e che la correzione non generi nuovi avvisi.

> [!TIP]
> Puoi rieseguire l'analisi del codice dalla finestra Analisi codice. Fare clic sul pulsante **Analizza** e quindi scegliere l'ambito dell'analisi. Puoi rieseguire l'analisi dell'intera soluzione o di un progetto selezionato.

## <a name="BKMK_Suppress"></a> Eliminazione degli avvisi di analisi del codice
 In alcuni casi potresti decidere di non correggere un avviso di analisi del codice. Puoi decidere che risolvere il problema richiede un'eccessiva ricodificazione relativamente alla probabilità che il problema si ripresenti in qualsiasi implementazione realistica del codice. Oppure potresti ritenere che l'analisi utilizzata nell'avviso sia inadeguata per il contesto specifico. Puoi eliminare gli avvisi in modo che non vengano più visualizzati nella finestra Analisi codice.

 Per eliminare un avviso:

1. Se le informazioni dettagliate non sono visualizzate, fai clic sul titolo dell'avviso per espanderlo.

2. Scegliere il collegamento **Azioni** nella parte inferiore dell'avviso.

3. Scegliere **Elimina messaggio** e quindi **nell'origine** o **nel file di eliminazione**.

   - L'opzione **nell'origine** inserisce un attributo `SuppressMessage` nel file di origine sopra al metodo che ha generato l'avviso. In questo modo l'eliminazione risulta più facilmente individuabile.

   - L'opzione **nel file di eliminazione** aggiunge un attributo `SuppressMessage` al file **GlobalSuppressions.cs** del progetto. Ciò può rendere più semplice la gestione delle eliminazioni. Si noti che anche l'attributo `SuppressMessage` aggiunto a **GlobalSuppression.cs** fa riferimento al metodo che ha generato l'avviso. Non elimina l'avviso globalmente.

     La decisione se eliminare l'avviso nel file di origine o nel file di eliminazione dipende dal tuo stile di codifica e dalle esigenze.

## <a name="BKMK_Search"></a> Ricerca e filtro dei risultati dell'analisi del codice
 Puoi effettuare una ricerca in lunghi elenchi di messaggi di avviso e filtrare gli avvisi nelle soluzioni composte da più progetti.

 ![Finestra di ricerca e filtro dell'analisi del codice](../test/media/ca-searchfilter.png "CA_SearchFilter")

 In [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)] a tutti gli avvisi di analisi del codice viene assegnato un livello di gravità Warning.

## <a name="BKMK_Warnings"></a> Avvisi di analisi del codice Visual Basic e C#
 L'analisi del codice genera gli avvisi seguenti:

 [CA1001: I tipi proprietari di campi eliminabili devono essere eliminabili](https://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Rimuovere i finalizzatori vuoti](https://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: I campi eliminabili devono essere eliminati](https://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Implementare costruttori di serializzazione](https://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](https://msdn.microsoft.com/library/ms182359.aspx)
