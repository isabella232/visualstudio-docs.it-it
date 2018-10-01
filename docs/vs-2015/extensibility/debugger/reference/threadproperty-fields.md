---
title: THREADPROPERTY_FIELDS | Microsoft Docs
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
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 861a7d51b69f72938750a3210c29b8ac560af016
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519584"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [THREADPROPERTY_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/threadproperty-fields).  
  
Specifica le informazioni su un thread deve essere recuperato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
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
public enum enum_THREADPROPERTY_FIELDS {   
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
 Initialize/usare la `dwThreadId` campo le [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struttura.  
  
 TPF_SUSPENDCOUNT  
 Initialize/usare la `dwSuspendCount` campo il `THREADPROPERTIE`struttura S.  
  
 TPF_STATE  
 Initialize/usare la `dwThreadState` campo il `THREADPROPERTIE`struttura S.  
  
 TPF_PRIORITY  
 Initialize/usare la `bstrPriority` campo il `THREADPROPERTIE`struttura S.  
  
 TPF_NAME  
 Initialize/usare la `bstrName` campo il `THREADPROPERTIE`struttura S.  
  
 TPF_LOCATION  
 Initialize/usare la `bstrLocation` campo il `THREADPROPERTIE`struttura S.  
  
 TPF_ALLFIELDS  
 Specifica tutti i campi.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati come argomento per il [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodo per indicare quali campi della [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struttura devono essere inizializzate.  
  
 Questi valori possono essere usati anche nelle `dwFields` membro del `THREADPROPERTIES` struttura per indicare quali campi vengono usati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)

