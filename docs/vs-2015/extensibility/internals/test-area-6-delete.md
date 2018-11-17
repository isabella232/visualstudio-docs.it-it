---
title: 'Area di test 6: Elimina | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1498566e1afeaf1517b7ae3bd62297444c828888
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766312"
---
# <a name="test-area-6-delete"></a>Area di test 6: Eliminare
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quest'area del plug-in test di controllo del codice sorgente illustra le azioni di eliminazione.  
  
 Di risposta per eliminare le azioni nel controllo del codice sorgente **Esplora soluzioni**.  
  
 Seguito è riportato un elenco di elementi che possono essere eliminate:  
  
- File  
  
- Cartelle  
  
- Progetto  
  
  A seconda del tipo di progetto, potrebbe essere la possibilità **rimuovere** il progetto (lascia i file su disco) o **eliminare** il progetto (rimuove i file su disco). Entrambe le azioni rimuove il progetto o un elemento dalla **Esplora soluzioni**.  
  
## <a name="expected-behavior"></a>Comportamento previsto  
 Il comportamento previsto per i test case nell'area di test di delete è:  
  
-   Elemento eliminato non è più visibile all'interno **Esplora soluzioni**.  
  
-   L'elemento padre del progetto eliminato o dell'elemento è stato estratto in base alle esigenze (eventualmente con un messaggio di richiesta.)  
  
-   Dopo avere eliminato un checked out o elemento aggiunto, non viene visualizzato nei **archiviazioni in sospeso** finestra.  
  
-   L'elemento è ancora presente all'interno dell'archivio di controllo di origine, anche dopo l'eliminazione e deve essere eliminato manualmente.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Eliminare un progetto client|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Rimuovere l'intero progetto dalla soluzione|Comportamento previsto comune.|  
|Eliminare un file vuoto|1.  Creare un progetto client.<br />2.  Aggiungere un file di zero byte per il progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Selezionare il file, eliminarlo.|Comportamento previsto comune.|  
|Eliminare una cartella con un file|1.  Creare soluzioni di singolo progetto.<br />2.  Aggiungere una cartella.<br />3.  Aggiungere un file nella cartella.<br />4.  Aggiungere la soluzione al controllo del codice sorgente.<br />5.  Estrarre il progetto per evitare richieste.<br />6.  Eliminare la cartella.|Comportamento previsto comune.|  
|Eliminare un progetto Web di File System|1.  Creare un progetto Web di File System (usare il pulsante Sfoglia per specificare un percorso UNC).<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Rimuovere l'intero progetto dalla soluzione.<br />4.  Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercita percorsi diversi tramite il codice ma ha la stessa interfaccia esterna e il comportamento).|Comportamento previsto comune.|  
|Eliminare un file da un progetto Web di File System|1.  Creare un progetto di File System Web.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Eliminare un file dal progetto.<br />4.  Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercita percorsi diversi tramite il codice ma ha la stessa interfaccia esterna e il comportamento).|Comportamento previsto comune.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

