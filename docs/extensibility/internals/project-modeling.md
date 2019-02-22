---
title: Progetto di modellazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a2ae395d94d76fd2b11de33cc6d5053d8b92432
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633434"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
Il passaggio successivo nella fornitura di automazione per il progetto consiste nell'implementare gli oggetti di progetto standard: la <xref:EnvDTE.Projects> e `ProjectItems` raccolte; gli `Project` e <xref:EnvDTE.ProjectItem> oggetti; e gli oggetti rimanenti univoci per l'implementazione. Questi oggetti standard sono definiti nel file Dteinternal.h. Nell'esempio BscPrj viene fornita un'implementazione degli oggetti standard. È possibile usare queste classi come modelli per creare gli oggetti di progetto standard che ostacolano il settore side-by-side con gli oggetti di progetto da altri tipi di progetto.

 Un consumer di automazione presuppone che sia in grado di chiamare <xref:EnvDTE.Solution>("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> (`n`) dove n è un numero di indice per l'acquisizione di un progetto specifico della soluzione. La chiamata automazione fa sì che l'ambiente chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sulla gerarchia di progetto appropriato, passando VSITEMID_ROOT come il parametro di ItemID e VSHPROPID_ExtObject come parametro VSHPROPID. `IVsHierarchy::GetProperty` Restituisce un `IDispatch` puntatore all'oggetto di automazione fornire le principali `Project` interfaccia, che è stato implementato.

 Di seguito è la sintassi di `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Progetti di adattare l'annidamento e usano le raccolte per creare gruppi di elementi del progetto. La gerarchia è simile al seguente:

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 La nidificazione indica che un <xref:EnvDTE.ProjectItem> oggetto può essere <xref:EnvDTE.ProjectItems> raccolta nello stesso momento poiché un `ProjectItems` raccolta può contenere gli oggetti annidati. L'esempio di progetto di base non illustra questo annidamento. Implementando il `Project` dell'oggetto, si partecipa la struttura ad albero che caratterizza la progettazione del modello di automazione generale.

 L'automazione dei progetti segue il percorso nel diagramma seguente.

 ![Oggetti del progetto Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") automazione dei progetti

 Se non si implementa una `Project` dell'oggetto, l'ambiente verrà comunque restituito un oggetto generico `Project` oggetto che contiene solo il nome del progetto.

## <a name="see-also"></a>Vedere anche
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>