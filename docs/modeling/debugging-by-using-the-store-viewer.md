---
title: Esecuzione del debug utilizzando il Visualizzatore di archivio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d26c66b6bcbab2eafe2ae8b01597ef09985dcfa8
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858652"
---
# <a name="debugging-by-using-the-store-viewer"></a>Esecuzione del debug utilizzando il Visualizzatore di archivio
Con il Visualizzatore Store, è possibile esaminare lo stato di un *archiviare* usato da [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Il Visualizzatore Store consente di visualizzare tutti gli elementi di modello di dominio appartenenti a un negozio specifico, con le proprietà degli elementi e collegamenti tra elementi.

## <a name="opening-store-viewer"></a>Visualizzatore di apertura Store
 Quando si è nella build sperimentale di Visual Studio, arrestare il codice in un punto di interruzione in un'istanza dell'archivio contiene informazioni sul modello. Quindi, aprire il Visualizzatore Store digitando il comando seguente nel **Immediate** finestra:

```csharp
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
>  È necessario sostituire `mystore` con il nome dell'istanza di archivio. Inoltre, se si aggiunge lo spazio dei nomi al codice, è possibile digitare il comando per la visualizzazione Store Viewer senza il nome completo dello spazio dei nomi:
>
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
>  `...`
>
>  `StoreViewer.Show(mystore);`

 Il `Show` metodo dispone di diversi overload. È possibile specificare un'istanza di un archivio o una partizione come parametro.

 In alternativa, è possibile inserire la riga di codice che consente di visualizzare il Visualizzatore di Store in un punto qualsiasi nel codice in cui il parametro passato al `Show` metodo si trova nell'ambito. Questa azione consente di visualizzare il Visualizzatore Store quando la riga di codice viene eseguito come snapshot del contenuto dell'archivio.

### <a name="using-store-viewer"></a>Utilizzo del Visualizzatore Store
 Quando si apre il Visualizzatore Store, viene visualizzata una finestra non modale di Windows Form, come mostrato nella figura seguente.

 ![](../modeling/media/storeviewer2.png) Visualizzatore di Store

 Il Visualizzatore Store include tre riquadri: il riquadro a sinistra, riquadro superiore destro e il riquadro in basso a destra. Il riquadro a sinistra è una visualizzazione struttura ad albero dei tipi nel `DomainDataDirectory` membro di un archivio. Se si espande il nodo della partizione e fare clic su un elemento, le proprietà dell'elemento visualizzato nel riquadro superiore destro. Se l'elemento è collegato ad altri elementi, gli elementi aggiuntivi vengono visualizzati nel riquadro in basso a destra. Se si fa doppio clic su un elemento nel riquadro in basso a destra, l'elemento viene evidenziato nel riquadro sinistro.

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)