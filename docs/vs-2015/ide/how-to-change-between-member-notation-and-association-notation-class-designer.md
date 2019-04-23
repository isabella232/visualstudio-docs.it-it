---
title: 'Procedura: Passare dalla notazione membro alla notazione associazione (Progettazione classi) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 864edc3666164ac05d8155fd001d83c5bf515a6d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093293"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Procedura: Passare dalla notazione membro alla notazione associazione e viceversa (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Progettazione classi è possibile modificare il modo in cui il diagramma classi rappresenta una relazione di associazione tra due tipi dalla notazione membro alla notazione associazione e viceversa. I membri visualizzati come linee di associazione spesso offrono una visualizzazione utile della correlazione tra tipi.  
  
> [!NOTE]
>  Le relazioni di associazione possono essere rappresentate come proprietà del membro o campo. Per passare dalla notazione membro alla notazione associazione, un tipo deve avere un membro di un altro tipo. Per passare dalla notazione associazione alla notazione membro, i due tipi devono essere collegati da una linea di associazione. Per altre informazioni, vedere [Procedura: Creare associazioni tra tipi (Progettazione classi)](../ide/how-to-create-associations-between-types-class-designer.md). Se il progetto contiene più diagrammi di classi, le modifiche apportate al modo in cui un diagramma visualizza le relazioni di associazione influiscono solo tale diagramma. Per modificare il modo in cui un altro diagramma visualizza le relazioni di associazione, aprire o visualizzare tale diagramma ed seguire questi passaggi.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Per passare dalla notazione membro alla notazione associazione  
  
1. Dal nodo del progetto in Esplora soluzioni, aprire il file del diagramma classi (con estensione CD).  
  
2. Nella forma tipo del diagramma classi, fare doppio clic su proprietà del membro o sul campo che rappresenta l'associazione e scegliere **Mostra come associazione**.  
  
    > [!TIP]
    >  Se non sono visibili campi o proprietà nella forma tipo, i raggruppamenti nella forma potrebbero essere compressi. Per espandere la forma tipo, fare doppio clic sul nome del raggruppamento o fare clic con il pulsante destro del mouse sulla forma tipo e scegliere **Espandi**.  
  
     Il membro scompare dal raggruppamento della forma tipo e viene visualizzata una linea di associazione per connettere i due tipi. La linea di associazione è contrassegnata con il nome della proprietà o del campo.  
  
### <a name="to-change-association-notation-to-member-notation"></a>Per passare dalla notazione associazione alla notazione membro  
  
- Nel diagramma classi, fare clic con il pulsante destro del mouse sulla linea di associazione e scegliere **Mostra come proprietà** o **Mostra come campo**, come appropriato.  
  
     La linea di associazione scompare e la proprietà viene visualizzata nel raggruppamento appropriato all'interno della forma tipo nel diagramma.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare ereditarietà tra tipi (Progettazione classi)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Procedura: Visualizzare l'ereditarietà tra tipi (Progettazione classi)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Viewing Types and Relationships (Class Designer)](../ide/viewing-types-and-relationships-class-designer.md)  (Visualizzazione dei tipi e delle relazioni (Progettazione classi))  
 [Procedura: Visualizzare un'associazione di raccolte (Progettazione classi)](../ide/how-to-visualize-a-collection-association-class-designer.md)
