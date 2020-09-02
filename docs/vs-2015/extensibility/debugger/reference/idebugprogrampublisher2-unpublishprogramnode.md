---
title: 'IDebugProgramPublisher2:: UnpublishProgramNode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fed7f35b87ec3e4a761b7adc33876affe778d9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423134"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rimuove un nodo di programma specificato dalla disponibilità ai motori di debug (DEs) e alla gestione del debug della sessione (SDM).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT UnpublishProgramNode(  
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int UnpublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProgramNode`  
 in Oggetto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresenta il nodo del programma da rimuovere.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Una volta rimossa, il nodo del programma non è più disponibile per la query per le informazioni sul programma.  
  
 Per rendere disponibile un nodo di programma, chiamare il metodo [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
