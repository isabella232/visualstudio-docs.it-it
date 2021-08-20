---
title: Visualizzazione Riepilogo | Microsoft Docs
description: Informazioni su come la visualizzazione Riepilogo visualizza le informazioni sulle funzioni o sugli oggetti con prestazioni più costose in un'esecuzione della profilatura.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6e44ca9418a08b1e31508634b63e6c58a2acdd7d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157176"
---
# <a name="summary-view"></a>Visualizzazione di riepilogo
La visualizzazione Riepilogo mostra informazioni sulle funzioni o gli oggetti che influiscono maggiormente sulle prestazioni in un'esecuzione della profilatura. Questa visualizzazione include un grafico della sequenza temporale e due o più elenchi delle funzioni o degli oggetti che influiscono maggiormente sulle prestazioni, in base alle metriche delle prestazioni del metodo di profilatura. I dati in questa visualizzazione dipendono dal metodo di profilatura usato (campionamento, strumentazione o concorrenza) e dal fatto che siano state raccolte le allocazioni di memoria .NET.

 Per tutte le visualizzazioni Riepilogo, ad eccezione della visualizzazione Riepilogo dei dati di concorrenza, il grafico della sequenza temporale nella visualizzazione Riepilogo mostra l'utilizzo del processore (CPU) dell'applicazione profilata nel periodo di profilatura.

- Se si specifica un segmento di tempo nel grafico, è possibile rianalizzare i dati per tale segmento o ingrandire la visualizzazione della sequenza temporale fino a selezionare il segmento specificato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni report dalla sequenza temporale di riepilogo.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

- È possibile fare clic su una funzione in un elenco della visualizzazione Riepilogo per aprire la visualizzazione Dettagli funzione per la funzione. È anche possibile fare clic con il pulsante destro del mouse sulla funzione per accedere ad altre opzioni di visualizzazione.

- Per modificare il numero di elementi visualizzati negli elenchi della visualizzazione Riepilogo, aprire il menu **Strumenti**, scegliere **Opzioni** e quindi fare clic su **Strumenti per le prestazioni**. In **Impostazioni generali** modificare l'impostazione **Numero delle funzioni nella visualizzazione Riepilogo**.

## <a name="notifications-links"></a>Collegamenti di notifica
 È possibile fare clic sui collegamenti nell'elenco Notifica per impostare le opzioni di visualizzazione per il report. L'elenco è a destra del grafico della sequenza temporale.

|Opzione|Descrizione|
|-|-|
|**Mostra tutto il codice**<br /><br /> **Mostra Just My Code**|Non disponibile per il codice nativo o per i dati di profilatura raccolti tramite il metodo di strumentazione. Consente di passare dalla visualizzazione dei dati solo dal codice utente (**Mostra Just My Code**) alla visualizzazione dei dati da tutto il codice, incluso il codice di sistema (**Mostra tutto il codice**). Per impostazione predefinita, i dati sono limitati al codice utente. Per modificare l'impostazione, [vedere Procedura: Filtrare le visualizzazioni dei report](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)degli strumenti di profilatura per Just My Code .|
|**Visualizzare le linee guida**|Visualizza gli avvisi delle regola per le prestazioni nella finestra **Elenco errori**. Per altre informazioni, vedere [Usare le regole per le prestazioni per analizzare dati](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>Report
 È possibile fare clic sui collegamenti nell'elenco Rapporto per aprire visualizzazioni diverse e confrontare, salvare o filtrare il report. L'elenco è a destra del grafico della sequenza temporale.

|Opzione |Descrizione |
|----------------------------| - |
| **Mostra albero delle chiamate ridotto** | Visualizza i percorsi di esecuzione più dispendiosi nella visualizzazione Albero delle chiamate. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate.](../profiling/call-tree-view.md) |
| **Mostra righe critiche** | Non disponibile per i dati di profilatura raccolti tramite il metodo di strumentazione. Visualizza le righe di codice sorgente più dispendiose nella visualizzazione Righe. Per altre informazioni, vedere [Visualizzazione Righe.](../profiling/lines-view.md) |
| **Confronta report** | Visualizza la finestra di dialogo **Selezionare i file di analisi per il confronto** in cui è possibile specificare un altro file di dati di profilatura da confrontare con il file corrente. Per altre informazioni, vedere [Confrontare i file di dati delle prestazioni](../profiling/comparing-performance-data-files.md). |
| **Esporta dati report** | Visualizza la finestra di dialogo **Esporta rapporto** in cui è possibile specificare una o più visualizzazioni del report da salvare come file delimitati da virgole (CSV) o file XML. Per altre informazioni, vedere [Procedura: Esportare report degli strumenti di profilatura.](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)) |
| **Salva rapporto analizzato** | Salva il file di dati di profilatura corrente come file con estensione vsps, che può essere aperto più rapidamente nell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [Procedura: Salvare i file di dati di profilatura analizzati.](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)) |
| **Filtra dati report** | Visualizza il riquadro per filtrare i report di profilatura in cui è possibile specificare criteri per limitare i dati nella visualizzazione del report. Per altre informazioni, vedere [Filtro visualizzazione report prestazioni](../profiling/performance-report-view-filter.md) |
| **Attiva/Disattiva schermo intero** | Disattiva la modalità schermo intero per la visualizzazione dei report. |

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Riepilogo: dati di campionamento](../profiling/summary-view-sampling-data.md)
- [Visualizzazione Riepilogo: dati di strumentazione](../profiling/summary-view-instrumentation-data.md)
- [Visualizzazione Riepilogo: dati di memoria .NET](../profiling/summary-view-dotnet-memory-data.md)
