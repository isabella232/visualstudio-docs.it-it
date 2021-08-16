---
title: Project Modello di | Microsoft Docs
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7edc9fe6e4703315356d5289f0054d2aacdbe76c9e752c4b8608e8e58f32e38e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359215"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
Il passaggio successivo per fornire l'automazione per il progetto consiste nell'implementare gli oggetti di progetto standard: le raccolte e , gli oggetti e e gli oggetti rimanenti univoci per <xref:EnvDTE.Projects> `ProjectItems` `Project` <xref:EnvDTE.ProjectItem> l'implementazione. Questi oggetti standard sono definiti nel file Dteinternal.h. Un'implementazione degli oggetti standard viene fornita nell'esempio BscPrj. È possibile usare queste classi come modelli per creare oggetti di progetto standard affiancati agli oggetti di progetto di altri tipi di progetto.

 Un consumer di automazione presuppone di essere in grado di chiamare (" e ( ) dove n è un numero di indice per ottenere <xref:EnvDTE.Solution> un progetto specifico nella `<UniqueProjName>")` <xref:EnvDTE.ProjectItems> `n` soluzione. Se si effettua questa chiamata di automazione, l'ambiente chiama nella gerarchia di progetto appropriata, passando VSITEMID_ROOT come parametro ItemID e VSHPROPID_ExtObject <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> come parametro VSHPROPID. `IVsHierarchy::GetProperty` restituisce un `IDispatch` puntatore all'oggetto di automazione che fornisce l'interfaccia di base `Project` implementata.

 Di seguito è riportata la sintassi di `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 I progetti supportano l'annidamento e usano le raccolte per creare gruppi di elementi di progetto. La gerarchia è simile alla seguente.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 L'annidamento <xref:EnvDTE.ProjectItem> indica che un oggetto può essere raccolta <xref:EnvDTE.ProjectItems> contemporaneamente perché una raccolta può `ProjectItems` contenere gli oggetti annidati. L'esempio basic Project non illustra questo annidamento. Implementando l'oggetto , si partecipa alla struttura ad albero che caratterizza la `Project` progettazione del modello di automazione complessivo.

 L'automazione del progetto segue il percorso nel diagramma seguente.

 ![Visual Studio Project oggetti Project](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") automazione

 Se non si implementa un oggetto , l'ambiente restituirà comunque un oggetto generico che contiene solo `Project` `Project` il nome del progetto.

## <a name="see-also"></a>Vedi anche
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
