---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d7e43ba54b7efae0d66ace43821e8736663136e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286598"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Termina il programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se possibile, verrà terminato e scaricato dal processo; il programma in caso contrario, il motore di debug (DE) eseguirà le operazioni di pulitura necessarie.  
  
 Questo metodo o la [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) viene chiamato dall'IDE, in genere in risposta all'utente di interrompere il debug di tutti. L'implementazione di questo metodo deve, in teoria, terminare il programma all'interno del processo. In caso contrario, la Germania deve impedire che il programma in esecuzione altri in questo processo ed eseguire la pulizia necessaria. Se il `IDebugProcess2::Terminate` metodo è stato chiamato dall'IDE, l'intero processo verrà terminato un certo momento dopo la `IDebugProgram2::Terminate` viene chiamato il metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

