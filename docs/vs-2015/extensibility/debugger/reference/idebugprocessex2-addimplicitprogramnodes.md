---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2552731cf9150e4e86a7ef4bf6d927aaac33cc7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529282"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProcessEx2::AddImplicitProgramNodes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes).  
  
Questo metodo aggiunge un nodo di programma per ogni motore di debug (DE) specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidLaunchingEngine`  
 [in] Il `GUID` di un CRI che deve essere utilizzato per avviare programmi (e si presuppone per aggiungere nodi di un proprio programma).  
  
 `rgguidSpecificEngines`  
 [in] Matrice di `GUID`s di DEs per il programma che verranno aggiunti i nodi.  
  
 `celtSpecificEngines`  
 [in] I numerosi `GUID`s nel `rgguidSpecificEngines` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [I nodi di programma](../../../extensibility/debugger/program-nodes.md) verranno aggiunti per ogni Germania elencati nella `rgguidSpecificEngines`, escluso il motore che esegue l'applicazione (come specificato in `guidLaunchingEngine`), che vengono utilizzati per aggiungere il proprio nodo programma quando avvia un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodi di programma](../../../extensibility/debugger/program-nodes.md)

