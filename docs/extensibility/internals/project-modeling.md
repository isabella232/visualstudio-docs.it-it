---
title: Modellazione del progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725566"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
Il passaggio successivo per fornire l'automazione per il progetto consiste nell'implementare gli oggetti di progetto standard: le raccolte <xref:EnvDTE.Projects> e `ProjectItems`; oggetti `Project` e <xref:EnvDTE.ProjectItem>; e gli oggetti rimanenti specifici dell'implementazione. Questi oggetti standard vengono definiti nel file Dteinternal. h. Nell'esempio BscPrj viene fornita un'implementazione degli oggetti standard. È possibile utilizzare queste classi come modelli per creare oggetti di progetto standard che si trovano affiancati a oggetti di progetto di altri tipi di progetto.

 Un consumer di automazione presume che sia in grado di chiamare <xref:EnvDTE.Solution> ("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> (`n`) dove n è un numero di indice per ottenere un progetto specifico nella soluzione. Se si effettua questa chiamata di automazione, l'ambiente chiamerà <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sulla gerarchia del progetto appropriata, passando VSITEMID_ROOT come parametro ItemID e VSHPROPID_ExtObject come parametro VSHPROPID. `IVsHierarchy::GetProperty` restituisce un puntatore `IDispatch` all'oggetto di automazione che fornisce l'interfaccia di `Project` principale, che è stata implementata.

 Di seguito è riportata la sintassi di `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 I progetti supportano la nidificazione e l'utilizzo di raccolte per creare gruppi di elementi di progetto. La gerarchia ha un aspetto simile al seguente.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Annidamento significa che un oggetto <xref:EnvDTE.ProjectItem> può essere <xref:EnvDTE.ProjectItems> raccolta contemporaneamente perché una raccolta `ProjectItems` può contenere gli oggetti annidati. Nell'esempio di progetto di base non viene illustrato questo annidamento. Implementando l'oggetto `Project`, si partecipa alla struttura ad albero che caratterizza la progettazione del modello di automazione globale.

 L'automazione del progetto segue il percorso del diagramma seguente.

 ![Oggetti di progetto di Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automazione del progetto

 Se non si implementa un oggetto `Project`, l'ambiente restituirà comunque un oggetto `Project` generico che contiene solo il nome del progetto.

## <a name="see-also"></a>Vedere anche
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>