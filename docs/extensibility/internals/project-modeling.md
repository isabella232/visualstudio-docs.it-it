---
title: Modellazione del progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706547"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
Il passaggio successivo nel fornire l'automazione per <xref:EnvDTE.Projects> il `ProjectItems` progetto consiste nell'implementare gli oggetti di progetto standard: le e le raccolte; gli `Project` <xref:EnvDTE.ProjectItem> oggetti e; e gli oggetti rimanenti univoci per l'implementazione. Questi oggetti standard sono definiti nel file Dteinternal.h. Un'implementazione degli oggetti standard viene fornita nell'esempio BscPrj. È possibile utilizzare queste classi come modelli per creare oggetti di progetto standard personalizzati affiancati a oggetti di progetto di altri tipi di progetto.

 Un consumer di automazione presume <xref:EnvDTE.Solution>`<UniqueProjName>")` di <xref:EnvDTE.ProjectItems> `n`essere in grado di chiamare (" e ( ) dove n è un numero di indice per ottenere un progetto specifico nella soluzione. Se si effettua questa chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> di automazione, l'ambiente chiama la gerarchia di progetto appropriata, passando VSITEMID_ROOT come parametro ItemID e VSHPROPID_ExtObject come parametro VSHPROPID. `IVsHierarchy::GetProperty`restituisce `IDispatch` un puntatore all'oggetto di automazione che fornisce l'interfaccia di base, `Project` implementata.

 Di seguito è `IVsHierarchy::GetProperty`riportata la sintassi di .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 I progetti supportano la nidificazione e utilizzano le raccolte per creare gruppi di elementi di progetto. La gerarchia ha questo aspetto.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 La nidificazione <xref:EnvDTE.ProjectItem> significa che <xref:EnvDTE.ProjectItems> un oggetto può `ProjectItems` essere insacido contemporaneamente perché una raccolta può contenere gli oggetti annidati. Nell'esempio di progetto di base non viene illustrato questo annidamento. Implementando `Project` l'oggetto, si partecipa alla struttura ad albero che caratterizza la progettazione del modello di automazione generale.

 L'automazione del progetto segue il percorso nel diagramma seguente.

 ![Oggetti progetto di Visual StudioVisual Studio Project Objects](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automazione del progetto

 Se non si `Project` implementa un oggetto, l'ambiente restituirà comunque un oggetto generico `Project` che contiene solo il nome del progetto.

## <a name="see-also"></a>Vedere anche
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
