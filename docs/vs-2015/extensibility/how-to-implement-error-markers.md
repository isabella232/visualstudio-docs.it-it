---
title: 'Procedura: implementare i marcatori di errore | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839639"
---
# <a name="how-to-implement-error-markers"></a>Procedura: Implementare marcatori di errore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I marcatori di errore (o sottolineature ondulate rosse) rappresentano le più difficili da implementare per le personalizzazioni dell'editor di testo. Tuttavia, i vantaggi che assegnano agli utenti del pacchetto VSPackage possono superare i costi per fornirli. I marcatori di errore contrassegnano leggermente il testo che il parser del linguaggio considera errato con una linea rossa ondulata o ondulata. Questo indicatore consente ai programmatori di visualizzare visivamente codice errato.  
  
 Usare i marcatori di testo per implementare le sottolineature ondulate rosse. Come regola, i servizi di linguaggio aggiungono sottolineature ondulate rosse al buffer di testo come passaggio in background, in fase di inattività o in un thread in background.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Per implementare la funzionalità di sottolineatura ondulata rossa  
  
1. Selezionare il testo in cui si desidera posizionare la sottolineatura ondulata rossa.  
  
2. Creare un marcatore del tipo `MARKER_CODESENSE_ERROR` . Per altre informazioni, vedere [procedura: aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Successivamente, passare un puntatore di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
   Questo processo consente inoltre di creare il testo del suggerimento o un menu di scelta rapida speciale su un marcatore specificato. Per altre informazioni, vedere [procedura: aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md).  
  
   Prima di poter visualizzare i marcatori di errore, è necessario disporre degli oggetti seguenti.  
  
- Parser.  
  
- Un provider di attività, ovvero un'implementazione di, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> che mantiene un record di modifiche nelle informazioni sulla riga allo scopo di identificare le righe da analizzare nuovamente.  
  
- Un filtro di visualizzazione di testo che acquisisce gli eventi di modifica del cursore dalla visualizzazione utilizzando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> metodo).  
  
  Il parser, il provider di attività e il filtro forniscono l'infrastruttura necessaria per rendere possibili i marcatori di errore. Nei passaggi seguenti viene fornito il processo di visualizzazione dei marcatori di errore.  
  
1. In una vista filtrata, il filtro ottiene un puntatore al provider di attività associato ai dati della visualizzazione.  
  
    > [!NOTE]
    > È possibile utilizzare lo stesso filtro di comando per i suggerimenti per i metodi, il completamento delle istruzioni, i marcatori di errore e così via.  
  
2. Quando il filtro riceve un evento che indica che è stato spostato in un'altra riga, viene creata un'attività per verificare la presenza di errori.  
  
3. Il gestore attività controlla se la riga è dirty. In tal caso, analizza la riga per individuare eventuali errori.  
  
4. Se vengono rilevati errori, il provider di attività crea un'istanza dell'elemento attività. Questa istanza crea il marcatore di testo usato dall'ambiente come marcatore di errore nella visualizzazione di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare marcatori di testo personalizzati](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: Usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)
