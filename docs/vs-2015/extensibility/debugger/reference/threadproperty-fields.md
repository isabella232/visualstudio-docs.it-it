---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204804"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica le informazioni su un thread da recuperare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 TPF_ID  
 Inizializza/usa il `dwThreadId` campo della struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF_SUSPENDCOUNT  
 Inizializza/usa il `dwSuspendCount` campo della `THREADPROPERTIE` struttura S.  
  
 TPF_STATE  
 Inizializza/usa il `dwThreadState` campo della `THREADPROPERTIE` struttura S.  
  
 TPF_PRIORITY  
 Inizializza/usa il `bstrPriority` campo della `THREADPROPERTIE` struttura S.  
  
 TPF_NAME  
 Inizializza/usa il `bstrName` campo della `THREADPROPERTIE` struttura S.  
  
 TPF_LOCATION  
 Inizializza/usa il `bstrLocation` campo della `THREADPROPERTIE` struttura S.  
  
 TPF_ALLFIELDS  
 Specifica tutti i campi.  
  
## <a name="remarks"></a>Osservazioni  
 Questi valori vengono passati come argomento al metodo [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) per indicare i campi della struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) da inizializzare.  
  
 Questi valori vengono inoltre utilizzati nel `dwFields` membro della `THREADPROPERTIES` struttura per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinati con un bit per bit `OR` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
