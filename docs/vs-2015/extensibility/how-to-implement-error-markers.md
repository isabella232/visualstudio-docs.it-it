---
title: 'Procedura: Implementare i marcatori di errore | Microsoft Docs'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435960"
---
# <a name="how-to-implement-error-markers"></a>Procedura: Implementare i marcatori di errore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli indicatori di errore (o sottolineature ondulate rosse) sono più difficili le personalizzazioni dell'editor di testo per implementare. Tuttavia, i vantaggi che offrono agli utenti di un VSPackage possono di gran lunga i costi per fornire loro. Gli indicatori di errore leggermente contrassegnano testo che il parser del linguaggio che considera non corretto con una riga rossa ondulata o una sottolineatura ondulata. Questo indicatore consente ai programmatori visualizzando visivamente il codice non corretto.  
  
 Usare marcatori di testo per implementare la sottolineatura ondulata rossa. Di norma, servizi di linguaggio aggiungere ondulate di colore rosso per il buffer di testo come sessione in background, in fase di inattività o in un thread in background.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Per implementare la funzionalità di sottolineatura ondulata rossa  
  
1. Selezionare il testo in cui si desidera posizionare la sottolineatura ondulata rossa.  
  
2. Creare un indicatore del tipo `MARKER_CODESENSE_ERROR`. Per altre informazioni, vedere [Procedura: Aggiungere i marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Successivamente, passare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> puntatore a interfaccia.  
  
   Questo processo consente anche di creare testo della descrizione comando o un menu di scelta rapida speciali su un marcatore specificato. Per altre informazioni, vedere [Procedura: Aggiungere i marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
   Gli oggetti seguenti sono necessari prima di visualizzare gli indicatori di errore.  
  
- Un parser.  
  
- Un provider di attività (vale a dire, un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) che gestisce un record delle modifiche nelle informazioni sulla riga allo scopo di identificare le righe per essere nuovamente analizzato.  
  
- Un filtro di visualizzazione di testo per l'acquisizione del punto di inserimento eventi di modifica dalla vista che utilizza il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) (metodo).  
  
  Il parser, provider di attività e filtro forniscono l'infrastruttura necessaria rendere possibili gli indicatori di errore. I passaggi seguenti sono disponibili il processo per visualizzare gli indicatori di errore.  
  
1. In una vista che viene filtrata, il filtro recupera un puntatore per il provider di attività associato ai dati della visualizzazione.  
  
    > [!NOTE]
    > È possibile usare lo stesso filtro di comando per suggerimenti di metodo, il completamento delle istruzioni, i marcatori di errore e così via.  
  
2. Quando il filtro riceve un evento che indica che è stato spostato in un'altra riga, viene creata un'attività per verificare la presenza di errori.  
  
3. Il gestore di attività verifica se la riga è stata modificata. In questo caso, lo analizza la riga per gli errori.  
  
4. Se vengono rilevati errori, il provider di attività crea un'istanza dell'elemento attività. Questa istanza crea il marcatore di testo che l'ambiente viene utilizzato come indicatore di errore nella visualizzazione di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di marcatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: Aggiungere i marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: Creare i marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: usare i marcatori di testo](../extensibility/how-to-use-text-markers.md)
