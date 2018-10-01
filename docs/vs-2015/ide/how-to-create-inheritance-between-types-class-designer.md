---
title: 'Procedura: Creare ereditarietà tra tipi (Progettazione classi) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd1b47ca4be4b68c1ddf3d4b75fcdfd25407705c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530304"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Procedura: Creare ereditarietà tra tipi (Progettazione classi) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: creare ereditarietà tra tipi (Progettazione classi)](https://docs.microsoft.com/visualstudio/ide/how-to-create-inheritance-between-types-class-designer).  
  
Per creare una relazione di ereditarietà tra due tipi in un diagramma classi usando Progettazione classi, connettere il tipo di base al tipo o ai tipi derivati corrispondenti. È possibile creare una relazione di ereditarietà tra due classi, tra una classe e un'interfaccia o tra due interfacce.  
  
### <a name="to-create-an-inheritance-between-types"></a>Per creare un'ereditarietà tra tipi  
  
1.  Dal progetto in Esplora soluzioni aprire un file del diagramma classi (con estensione cd).  
  
     Se non è disponibile alcun diagramma classi, crearne uno. Vedere [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  In **Progettazione classi** nella **Casella degli strumenti** fare clic su **Ereditarietà**.  
  
3.  Nel diagramma classi tracciare una linea di ereditarietà tra i tipi desiderati, come indicato di seguito:  
  
    -   Da una classe derivata a una classe di base  
  
    -   Da una classe di implementazione all'interfaccia implementata  
  
    -   Da un'interfaccia di estensione all'interfaccia estesa  
  
4.  Facoltativamente, quando è disponibile un tipo derivato da un tipo generico, fare clic sulla linea di ereditarietà. Nella finestra **Proprietà** impostare la proprietà **Argomenti di tipo** in modo che corrisponda al tipo da usare come tipo generico.  
  
    > [!NOTE]
    >  Se una classe astratta padre include almeno un membro astratto, tutti i membri astratti saranno quindi implementati come classi ereditanti non astratte.   
    >   
    >  Anche se è possibile visualizzare i tipi generici esistenti, non si possono creare nuovi tipi generici. Non si possono inoltre modificare i parametri di tipo per i tipi generici esistenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Ereditarietà](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Nozioni fondamentali sull'ereditarietà](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [How to: View Inheritance Between Types (Class Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)  (Procedura: Visualizzare l'ereditarietà tra tipi (Progettazione classi))  
 [Classi Visual C++ in Progettazione classi](../ide/visual-cpp-classes-in-class-designer.md)



