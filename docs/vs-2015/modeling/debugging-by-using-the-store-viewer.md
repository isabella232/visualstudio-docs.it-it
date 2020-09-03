---
title: Debug tramite il Visualizzatore dello Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654883"
---
# <a name="debugging-by-using-the-store-viewer"></a>Esecuzione del debug utilizzando il Visualizzatore di archivio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con il Visualizzatore dello Store è possibile esaminare lo stato di un *Archivio* utilizzato da [!INCLUDE[dsl](../includes/dsl-md.md)] . Il Visualizzatore archivio Visualizza tutti gli elementi del modello di dominio presenti in un archivio specifico, insieme alle proprietà degli elementi e ai collegamenti tra gli elementi.

## <a name="opening-store-viewer"></a>Apertura del Visualizzatore di Store
 Quando ci si trova nella [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compilazione sperimentale, arrestare il codice in corrispondenza di un punto di interruzione in cui un'istanza dell'archivio contiene informazioni sul modello. Aprire quindi il Visualizzatore dello Store digitando il comando seguente nella finestra di **controllo immediato** :

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> È necessario sostituire `mystore` con il nome dell'istanza dell'archivio. Inoltre, se si aggiunge lo spazio dei nomi al codice, è possibile digitare il comando per visualizzare il Visualizzatore dell'archivio senza lo spazio dei nomi completo:
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 Il `Show` metodo dispone di diversi overload. È possibile specificare un'istanza di un archivio o una partizione come parametro.

 In alternativa, è possibile inserire la riga di codice che Visualizza il Visualizzatore dello Store in qualsiasi punto del codice in cui il parametro passato al `Show` Metodo rientra nell'ambito. Questa azione consente di visualizzare il Visualizzatore di archiviazione quando la riga di codice viene eseguita come snapshot del contenuto dell'archivio.

### <a name="using-store-viewer"></a>Uso del Visualizzatore archivio
 Quando si apre il visualizzatore del negozio, viene visualizzata una finestra Windows Forms non modale, come illustrato nella figura seguente.

 ![](../modeling/media/storeviewer2.png "storeviewer2") Visualizzatore archivio

 Il Visualizzatore dell'archivio ha tre riquadri: il riquadro sinistro, il riquadro superiore destro e il riquadro inferiore destro. Il riquadro sinistro è una visualizzazione albero dei tipi nel `DomainDataDirectory` membro di un archivio. Se si espande il nodo della partizione e si fa clic su un elemento, le proprietà dell'elemento vengono visualizzate nel riquadro superiore destro. Se l'elemento è collegato ad altri elementi, gli elementi aggiuntivi vengono visualizzati nel riquadro in basso a destra. Se si fa doppio clic su un elemento nel riquadro inferiore destro, l'elemento viene evidenziato nel riquadro sinistro.

## <a name="see-also"></a>Vedere anche
 [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
