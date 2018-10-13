---
title: 'Procedura: eliminare gli avvisi tramite la voce di Menu | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c756a5ab6516d78f5370622555898c98658e8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211786"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Procedura: Eliminare gli avvisi tramite una voce di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  In origine la soppressione non è supportata per progetti di siti web.  
  
 È possibile usare la finestra Analisi codice per eliminare gli avvisi dell'analisi codice. Eliminare un avviso non è quello utilizzato per disabilitarlo. Quando si elimina un avviso, viene applicato solo a una particolare istanza della violazione. Altre violazioni dell'avviso stesso verranno ancora riportati nella finestra Elenco errori.  
  
 Dopo aver eseguito l'analisi del codice, si potrebbe determinare che una o più degli avvisi di analisi codice che vengono visualizzati nella finestra Analisi codice non sono applicabili all'applicazione. Ad esempio, si potrebbe determinare che il codice sia corretto perché è. In alternativa, potrebbe essere il caso in cui alcune violazioni per priorità bassa sono e non verranno risolto nel ciclo di sviluppo corrente. Indipendentemente dal motivo, è spesso utile indicare che l'avviso non è applicabile per informare i membri del team che è stato esaminato il codice e che è stato stabilito che è possibile eliminare l'avviso. Eliminazione nell'origine è utile perché consente di inserire un'eliminazione vicina in cui viene generato l'avviso.  
  
 È possibile scegliere se verificare che l'eliminazione verrà visualizzata nel codice sorgente o nel file di eliminazione globale. Alcune eliminazioni devono essere inseriti nel file di eliminazione globale. In questo caso, il **nell'origine** opzione sarà disabilitata.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Per eliminare un avviso tramite una voce di menu  
  
1.  Nel **Analyze** menu, scegliere **Windows** e quindi scegliere **analisi del codice**.  
  
2.  Nel **analisi del codice** finestra, selezionare Elimina l'avviso.  
  
3.  Scegliere le azioni, quindi scegliere **Elimina messaggi**e quindi scegliere **In origine** oppure **File di eliminazione progetto**.  
  
     Viene eliminato l'avviso specifico, e l'avviso viene visualizzato nella finestra Analisi codice barrato.  
  
> [!NOTE]
>  Le eliminazioni che non è una destinazione vengono visualizzati nel file di eliminazione globale.



