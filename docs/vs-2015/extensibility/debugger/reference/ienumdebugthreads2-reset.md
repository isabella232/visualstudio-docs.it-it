---
title: IEnumDebugThreads2::Reset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c34ed2ecd98af2858af3ac297bf4eb83f3964436
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147704"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reimposta l'enumerazione sul primo elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo che questo metodo viene chiamato, la chiamata successiva per la [successivo](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) metodo restituisce il primo elemento dell'enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
