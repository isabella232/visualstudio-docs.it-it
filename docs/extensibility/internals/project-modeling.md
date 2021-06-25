---
title: Modello di progetto | Microsoft Docs
description: Informazioni sugli oggetti di progetto standard necessari per creare l'automazione per il nuovo tipo di progetto e sul percorso seguito dall'automazione del progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90271fcc43c627f2eb7dbb2f318427ad0d9839e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899680"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
Il passaggio successivo per fornire l'automazione per il progetto consiste nell'implementare gli oggetti di progetto standard: le raccolte e , gli oggetti e e gli oggetti rimanenti univoci per <xref:EnvDTE.Projects> `ProjectItems` `Project` <xref:EnvDTE.ProjectItem> l'implementazione. Questi oggetti standard sono definiti nel file Dteinternal.h. Nell'esempio BscPrj viene fornita un'implementazione degli oggetti standard. È possibile usare queste classi come modelli per creare oggetti di progetto standard che si distinguono side-by-side con gli oggetti di progetto di altri tipi di progetto.

 Un consumer di automazione presuppone di essere in grado di chiamare (" e ( ) dove n è un numero di indice per ottenere <xref:EnvDTE.Solution> un progetto specifico nella `<UniqueProjName>")` <xref:EnvDTE.ProjectItems> `n` soluzione. Se si effettua questa chiamata di automazione, l'ambiente chiama la gerarchia del progetto appropriata, passando VSITEMID_ROOT come parametro ItemID e VSHPROPID_ExtObject <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> come parametro VSHPROPID. `IVsHierarchy::GetProperty` restituisce un `IDispatch` puntatore all'oggetto di automazione che fornisce l'interfaccia `Project` di base implementata.

 Di seguito è riportata la sintassi di `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 I progetti supportano l'annidamento e usano raccolte per creare gruppi di elementi di progetto. La gerarchia è simile alla seguente.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 L'annidamento significa <xref:EnvDTE.ProjectItem> che un oggetto può essere insieme <xref:EnvDTE.ProjectItems> contemporaneamente perché una raccolta può `ProjectItems` contenere gli oggetti annidati. L'esempio basic project non illustra questa nidificazione. Implementando l'oggetto , si partecipa alla struttura ad albero che caratterizza `Project` la progettazione del modello di automazione complessivo.

 L'automazione del progetto segue il percorso nel diagramma seguente.

 ![Visual Studio di progetto](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automazione del progetto

 Se non si implementa un oggetto , l'ambiente restituirà comunque un oggetto generico che contiene solo `Project` `Project` il nome del progetto.

## <a name="see-also"></a>Vedere anche
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
