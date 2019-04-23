---
title: Visualizzazione Riepilogo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7482fb99114b4a30281d84045faa14d1a6562471
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110901"
---
# <a name="summary-view"></a>Visualizzazione Riepilogo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione Riepilogo mostra informazioni sulle funzioni o gli oggetti che influiscono maggiormente sulle prestazioni in un'esecuzione della profilatura. Questa visualizzazione include un grafico della sequenza temporale e due o più elenchi delle funzioni o degli oggetti che influiscono maggiormente sulle prestazioni, in base alle metriche delle prestazioni del metodo di profilatura. I dati in questa visualizzazione dipendono dal metodo di profilatura usato (campionamento, strumentazione o concorrenza) e dal fatto che siano state raccolte le allocazioni di memoria .NET.  
  
 Per tutte le visualizzazioni Riepilogo, ad eccezione della visualizzazione Riepilogo dei dati di concorrenza, il grafico della sequenza temporale nella visualizzazione Riepilogo mostra l'utilizzo del processore (CPU) dell'applicazione profilata nel periodo di profilatura.  
  
- Se si specifica un segmento di tempo nel grafico, è possibile rianalizzare i dati per tale segmento o ingrandire la visualizzazione della sequenza temporale fino a selezionare il segmento specificato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni report dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
- È possibile fare clic su una funzione in un elenco della visualizzazione Riepilogo per aprire la visualizzazione Dettagli funzione per la funzione. È anche possibile fare clic con il pulsante destro del mouse sulla funzione per accedere ad altre opzioni di visualizzazione.  
  
- Per modificare il numero di elementi visualizzati negli elenchi della visualizzazione Riepilogo, aprire il menu **Strumenti**, scegliere **Opzioni** e quindi fare clic su **Strumenti per le prestazioni**. In **Impostazioni generali** modificare l'impostazione **Numero delle funzioni nella visualizzazione Riepilogo**.  
  
## <a name="notifications-links"></a>Collegamenti nell'elenco Notifica  
 È possibile fare clic sui collegamenti nell'elenco Notifica per impostare le opzioni di visualizzazione per il report. L'elenco è a destra del grafico della sequenza temporale.  
  
|||  
|-|-|  
|**Mostra tutto il codice**<br /><br /> **Mostra Just My Code**|Non disponibile per il codice nativo o per i dati di profilatura raccolti tramite il metodo di strumentazione. Consente di passare dalla visualizzazione dei dati solo dal codice utente (**Mostra Just My Code**) alla visualizzazione dei dati da tutto il codice, incluso il codice di sistema (**Mostra tutto il codice**). Per impostazione predefinita, i dati sono limitati al codice utente. Per modificare l'impostazione, vedere [Procedura: Visualizzazioni dei rapporti per visualizzare Just My Code degli strumenti di profilatura filtro](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Visualizza materiale sussidiario**|Visualizza gli avvisi delle regola per le prestazioni nella finestra **Elenco errori**. Per altre informazioni, vedere[Uso di regole per le prestazioni per analizzare dati](../profiling/using-performance-rules-to-analyze-data.md).|  
  
## <a name="report"></a>Report  
 È possibile fare clic sui collegamenti nell'elenco Rapporto per aprire visualizzazioni diverse e confrontare, salvare o filtrare il report. L'elenco è a destra del grafico della sequenza temporale.  
  
|||  
|-|-|  
|**Mostra albero delle chiamate ridotto**|Visualizza i percorsi di esecuzione più dispendiosi nella visualizzazione Albero delle chiamate. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md).|  
|**Mostra righe critiche**|Non disponibile per i dati di profilatura raccolti tramite il metodo di strumentazione. Visualizza le righe di codice sorgente più dispendiose nella visualizzazione Righe. Per altre informazioni, vedere [Visualizzazione Righe](../profiling/lines-view.md).|  
|**Confronta report**|Visualizza la finestra di dialogo **Selezionare i file di analisi per il confronto** in cui è possibile specificare un altro file di dati di profilatura da confrontare con il file corrente. Per altre informazioni, vedere [Confronto tra file di dati delle prestazioni](../profiling/comparing-performance-data-files.md).|  
|**Esporta dati report**|Visualizza la finestra di dialogo **Esporta rapporto** in cui è possibile specificare una o più visualizzazioni del report da salvare come file delimitati da virgole (CSV) o file XML. Per altre informazioni, vedere [Procedura: I report degli strumenti di profilatura esportazione](http://msdn.microsoft.com/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Salva rapporto analizzato**|Salva il file di dati di profilatura corrente come file con estensione vsps, che può essere aperto più rapidamente nell'interfaccia per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [Procedura: Salva i file di dati di profilatura analizzati](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtra dati report**|Visualizza il riquadro per filtrare i report di profilatura in cui è possibile specificare criteri per limitare i dati nella visualizzazione del report. Per altre informazioni, vedere [Filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).|  
|**Attiva/Disattiva schermo intero**|Disattiva la modalità schermo intero per la visualizzazione dei report.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-sampling-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-instrumentation-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-dotnet-memory-data.md)
