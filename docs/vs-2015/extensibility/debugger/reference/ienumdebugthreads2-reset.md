---
title: IEnumDebugThreads2::Reset | Microsoft Docs
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
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e7d4ecfe8251ba454c8c67cc6bd1094a3383679
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810944"
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

