---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
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
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eac934aa599d8b6ac3ff0b8779002620013f246a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517347"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProgramPublisher2::UnpublishProgram](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram).  
  
Rende non disponibile per eseguire il debug di un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDebuggeeInterface`  
 [in] Un `IUnknown` interfaccia al programma. Questo è lo stesso valore fornito per il [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (metodo) e identifica in modo univoco il programma viene rimosso (vale a dire, viene usato come un cookie).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per rendere disponibile un programma per i motori di debug e gestione del debug della sessione, usare il [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)

