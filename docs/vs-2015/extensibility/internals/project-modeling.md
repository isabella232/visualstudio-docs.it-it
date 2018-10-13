---
title: Progetto di modellazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 324c870e42a9a9da37036979304e06637364c4d0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229723"
---
# <a name="project-modeling"></a>Definizione di modelli di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 La nidificazione indica che un <xref:EnvDTE.ProjectItem> oggetto può essere <xref:EnvDTE.ProjectItems> raccolta nello stesso momento poiché un `ProjectItems` raccolta può contenere gli oggetti annidati. L'esempio di progetto di base non illustra questo annidamento. Implementando il `Project` dell'oggetto, si partecipa la struttura ad albero che caratterizza la progettazione del modello di automazione generale.  
  
 L'automazione dei progetti segue il percorso nel diagramma seguente.  
  
 ![Oggetti di progetto di Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automazione dei progetti  
  
 Se non si implementa una `Project` dell'oggetto, l'ambiente verrà comunque restituito un oggetto generico `Project` oggetto che contiene solo il nome del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>

