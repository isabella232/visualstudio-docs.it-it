---
title: 'IDebugMemoryContext2:: GetInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e46af3af34a31a1c13c89482b62f319591e483cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164075"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una struttura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) che descrive il contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 in Combinazione di flag dell'enumerazione [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) che indicano i campi della struttura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) da compilare.  
  
 `pInfo`  
 [in, out] `CONTEXT_INFO` Struttura compilata.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
