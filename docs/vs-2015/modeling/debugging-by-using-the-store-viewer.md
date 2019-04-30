---
title: Debug tramite il Visualizzatore Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a76cd9b726e534271937cb67a8d3f946d4eb477
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433202"
---
# <a name="debugging-by-using-the-store-viewer"></a>Esecuzione del debug utilizzando il Visualizzatore di archivio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con il Visualizzatore Store, è possibile esaminare lo stato di un *archiviare* usato da [!INCLUDE[dsl](../includes/dsl-md.md)]. Il Visualizzatore Store consente di visualizzare tutti gli elementi di modello di dominio appartenenti a un negozio specifico, con le proprietà degli elementi e collegamenti tra elementi.  
  
## <a name="opening-store-viewer"></a>Visualizzatore di apertura Store  
 Quando si utilizza il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sperimentale di compilazione, arrestare il codice in un punto di interruzione in un'istanza dell'archivio contiene informazioni sul modello. Quindi, aprire il Visualizzatore Store digitando il comando seguente nel **Immediate** finestra:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
> È necessario sostituire `mystore` con il nome dell'istanza di archivio. Inoltre, se si aggiunge lo spazio dei nomi al codice, è possibile digitare il comando per la visualizzazione Store Viewer senza il nome completo dello spazio dei nomi:  
>   
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
> `…`  
>   
> `StoreViewer.Show(mystore);`  
  
 Il `Show` metodo dispone di diversi overload. È possibile specificare un'istanza di un archivio o una partizione come parametro.  
  
 In alternativa, è possibile inserire la riga di codice che consente di visualizzare il Visualizzatore di Store in un punto qualsiasi nel codice in cui il parametro passato al `Show` metodo si trova nell'ambito. Questa azione consente di visualizzare il Visualizzatore Store quando la riga di codice viene eseguito come snapshot del contenuto dell'archivio.  
  
### <a name="using-store-viewer"></a>Utilizzo del Visualizzatore Store  
 Quando si apre il Visualizzatore Store, viene visualizzata una finestra non modale di Windows Form, come mostrato nella figura seguente.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Visualizzatore di Store  
  
 Il Visualizzatore Store include tre riquadri: il riquadro a sinistra, riquadro superiore destro e il riquadro in basso a destra. Il riquadro a sinistra è una visualizzazione struttura ad albero dei tipi nel `DomainDataDirectory` membro di un archivio. Se si espande il nodo della partizione e fare clic su un elemento, le proprietà dell'elemento visualizzato nel riquadro superiore destro. Se l'elemento è collegato ad altri elementi, gli elementi aggiuntivi vengono visualizzati nel riquadro in basso a destra. Se si fa doppio clic su un elemento nel riquadro in basso a destra, l'elemento viene evidenziato nel riquadro sinistro.  
  
## <a name="see-also"></a>Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
