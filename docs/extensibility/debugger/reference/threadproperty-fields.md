---
title: THREADPROPERTY_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713403"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Specifica quali informazioni su un thread deve essere recuperato.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="fields"></a>Campi
 `TPF_ID`\
 Inizializzare/utilizzare `dwThreadId` il campo della struttura [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Inizializzare/utilizzare `dwSuspendCount` il `THREADPROPERTIE`campo della struttura S.

 `TPF_STATE`\
 Inizializzare/utilizzare `dwThreadState` il `THREADPROPERTIE`campo della struttura S.

 `TPF_PRIORITY`\
 Inizializzare/utilizzare `bstrPriority` il `THREADPROPERTIE`campo della struttura S.

 `TPF_NAME`\
 Inizializzare/utilizzare `bstrName` il `THREADPROPERTIE`campo della struttura S.

 `TPF_LOCATION`\
 Inizializzare/utilizzare `bstrLocation` il `THREADPROPERTIE`campo della struttura S.

 `TPF_ALLFIELDS`\
 Specifica tutti i campi.

## <a name="remarks"></a>Osservazioni
 Questi valori vengono passati come argomento al metodo [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) per indicare quali campi della struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) devono essere inizializzati.

 Questi valori vengono `dwFields` utilizzati `THREADPROPERTIES` anche nel membro della struttura per indicare quali campi vengono utilizzati e validi.

 Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
