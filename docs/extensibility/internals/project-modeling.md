---
title: Modellazione del progetto | Microsoft Docs
description: Informazioni sugli oggetti di progetto standard necessari per creare l'automazione per il nuovo tipo di progetto e il percorso seguito da automazione del progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 506606291996c94ff10514c6c57f83c6e1133862
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062824"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
Il passaggio successivo per fornire l'automazione per il progetto consiste nell'implementare gli oggetti di progetto standard, ovvero le <xref:EnvDTE.Projects> `ProjectItems` raccolte e, gli `Project` <xref:EnvDTE.ProjectItem> oggetti e e gli oggetti rimanenti specifici dell'implementazione. Questi oggetti standard vengono definiti nel file Dteinternal. h. Nell'esempio BscPrj viene fornita un'implementazione degli oggetti standard. È possibile utilizzare queste classi come modelli per creare oggetti di progetto standard che si trovano affiancati a oggetti di progetto di altri tipi di progetto.

 Un consumer di automazione presume che sia in grado di chiamare <xref:EnvDTE.Solution> (" `<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> ( `n` ) dove n è un numero di indice per ottenere un progetto specifico nella soluzione. Se si effettua questa chiamata di automazione, l'ambiente chiamerà <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sulla gerarchia del progetto appropriata, passando VSITEMID_ROOT come parametro itemId e VSHPROPID_ExtObject come parametro VSHPROPID. `IVsHierarchy::GetProperty` Restituisce un `IDispatch` puntatore all'oggetto di automazione che fornisce l' `Project` interfaccia di base che è stata implementata.

 Di seguito è riportata la sintassi di `IVsHierarchy::GetProperty` .

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

 Annidamento significa che un <xref:EnvDTE.ProjectItem> oggetto può essere <xref:EnvDTE.ProjectItems> raccolta contemporaneamente, perché una `ProjectItems` raccolta può contenere gli oggetti annidati. Nell'esempio di progetto di base non viene illustrato questo annidamento. Implementando l' `Project` oggetto, si partecipa alla struttura ad albero che caratterizza la progettazione del modello di automazione globale.

 L'automazione del progetto segue il percorso del diagramma seguente.

 ![Oggetti di progetto di Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automazione del progetto

 Se non si implementa un `Project` oggetto, l'ambiente restituirà comunque un oggetto generico `Project` che contiene solo il nome del progetto.

## <a name="see-also"></a>Vedi anche
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
