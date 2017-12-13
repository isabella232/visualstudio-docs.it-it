---
title: 'Procedura: Implementare un''interfaccia (Progettazione classi) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f77a079a32cadb4a994e8874df2e9ae97dd93bf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-an-interface-class-designer"></a>Procedura: implementare un'interfaccia (Progettazione classi)
In Progettazione classi è possibile implementare un'interfaccia nel diagramma classi connettendola a una classe che fornisce il codice per i metodi di interfaccia. Progettazione classi genera un'implementazione dell'interfaccia e visualizza la relazione tra l'interfaccia e la classe come relazione di ereditarietà. È possibile implementare un'interfaccia tracciando una linea di ereditarietà tra l'interfaccia e la classe oppure trascinando l'interfaccia dalla visualizzazione classi.  
  
> [!TIP]
>  È possibile creare le interfacce allo stesso modo in cui vengono creati altri tipi di elemento. Se l'interfaccia esiste ma non viene visualizzata nel diagramma classi, è necessario innanzitutto visualizzarla. Per altre informazioni, vedere [Procedura: Creare tipi usando Progettazione classi](../ide/how-to-create-types-by-using-class-designer.md) e [Procedura: Visualizzare i tipi esistenti (Progettazione classi)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Per implementare un'interfaccia tracciando una linea di ereditarietà  
  
1.  Nel diagramma classi visualizzare l'interfaccia e la classe che implementa l'interfaccia.  
  
2.  Tracciare una linea di ereditarietà dalla classe e all'interfaccia.  
  
     Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia.  
  
 Per altre informazioni, vedere [Procedura: Creare ereditarietà tra tipi (Progettazione classi)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Per implementare un'interfaccia dalla finestra Visualizzazione classi  
  
1.  Nel diagramma classi visualizzare la classe che deve implementare l'interfaccia.  
  
2.  Aprire Visualizzazione classi e individuare l'interfaccia.  
  
    > [!TIP]
    >  Se non è già visualizzata, aprire Visualizzazione classi dal menu **Visualizza**. Per altre informazioni sulla visualizzazione classi, vedere [Viewing Classes and Their Members](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333) (Visualizzazione delle classi e dei relativi membri).  
  
3.  Trascinare il nodo di interfaccia nella forma della classe nel diagramma.  
  
     Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia. A questo punto, l'interfaccia è stata implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare tipi usando Progettazione classi](../ide/how-to-create-types-by-using-class-designer.md)   
 [Procedura: Visualizzare i tipi esistenti (Progettazione classi)](../ide/how-to-view-existing-types-class-designer.md)   
 [How to: Create Inheritance Between Types (Class Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md)  (Procedura: Creare l'ereditarietà tra tipi (Progettazione classi))  
 [Refactoring di classi e tipi (Progettazione classi)](../ide/refactoring-classes-and-types-class-designer.md)