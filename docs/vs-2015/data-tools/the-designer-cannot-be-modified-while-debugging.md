---
title: La finestra di progettazione non può essere modificato durante il debug | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9efa18c7b27f744b56aa3c3c192903690b79e47b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533049"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Impossibile modificare la finestra di progettazione durante il debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la finestra di progettazione non può essere modificato durante il debug](https://docs.microsoft.com/visualstudio/data-tools/the-designer-cannot-be-modified-while-debugging).  
  
  
Questo messaggio viene visualizzato quando si tenta di modificare elementi in Progettazione relazionale oggetti durante l'esecuzione dell'applicazione in modalità di debug. Quando l'applicazione è in esecuzione in tale modalità, Progettazione relazionale oggetti è di sola lettura.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Fare clic su **Termina debug** nel **Debug** menu.  
  
     Il debug viene interrotto e sarà quindi possibile modificare gli elementi in Progettazione relazionale oggetti.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

