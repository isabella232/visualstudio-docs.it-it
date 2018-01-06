---
title: 'Procedura: esclusione di avvisi tramite la voce di Menu | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5ce2369b5b97f1767a17686d3de2d4127150c05d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Procedura: Eliminare gli avvisi tramite una voce di menu
> [!NOTE]
>  Nell'origine eliminazione non è supportata per i progetti di sito web.  
  
 È possibile utilizzare la finestra Analisi codice per eliminare gli avvisi di analisi codice. Eliminare un avviso non è lo stesso come disabilitarlo. Quando si elimina un messaggio di avviso, si applica solo a una particolare istanza della violazione. Altre violazioni dello stesso avviso saranno ancora riportati nella finestra Elenco errori.  
  
 Dopo aver eseguito l'analisi del codice, è possibile che uno o più avvisi dell'analisi codice che vengono visualizzati nella finestra Analisi codice non sono applicabili all'applicazione. Ad esempio, è possibile che il codice sia corretto così com'è. In alternativa, potrebbe essere il caso in cui alcune violazioni bassa priorità e non verranno risolto nel ciclo di sviluppo corrente. A prescindere dal motivo, è spesso utile indicare che l'avviso non è applicabile per consentire i membri del team di sapere che il codice è stato rivisto e che è stato stabilito che è possibile eliminare l'avviso. Eliminazione nell'origine è utile perché consente di inserire un'eliminazione vicina in cui viene generato l'avviso.  
  
 È possibile scegliere se l'eliminazione verrà visualizzati nel codice sorgente o nel file di eliminazione globale. Alcune eliminazioni devono essere inseriti nel file di eliminazione globale. In questo caso, il **In origine** opzione sarà disabilitata.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Per eliminare un avviso usando la voce di menu  
  
1.  Nel **Analizza** menu, scegliere **Windows** e quindi scegliere **analisi del codice**.  
  
2.  Nel **analisi del codice** finestra, selezionare Elimina l'avviso.  
  
3.  Scegliere le azioni, quindi scegliere **Elimina messaggi**, quindi scegliere **In origine** o **File di eliminazione In progetto**.  
  
     Viene eliminato l'avviso specifico, e viene visualizzato l'avviso nella finestra Analisi codice barrato.  
  
> [!NOTE]
>  Le eliminazioni che non dispone di una destinazione vengono visualizzati nel file di eliminazione globale.