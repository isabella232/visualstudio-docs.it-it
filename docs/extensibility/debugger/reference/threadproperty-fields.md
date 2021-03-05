---
description: Specifica le informazioni su un thread da recuperare.
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 698c803304cf5efd3375b6d49e4dedbc4622f4c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221834"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Specifica le informazioni su un thread da recuperare.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="fields"></a>Campi
 `TPF_ID`\
 Inizializza/usa il `dwThreadId` campo della struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .

 `TPF_SUSPENDCOUNT`\
 Inizializza/usa il `dwSuspendCount` campo della `THREADPROPERTIE` struttura S.

 `TPF_STATE`\
 Inizializza/usa il `dwThreadState` campo della `THREADPROPERTIE` struttura S.

 `TPF_PRIORITY`\
 Inizializza/usa il `bstrPriority` campo della `THREADPROPERTIE` struttura S.

 `TPF_NAME`\
 Inizializza/usa il `bstrName` campo della `THREADPROPERTIE` struttura S.

 `TPF_LOCATION`\
 Inizializza/usa il `bstrLocation` campo della `THREADPROPERTIE` struttura S.

 `TPF_ALLFIELDS`\
 Specifica tutti i campi.

## <a name="remarks"></a>Commenti
 Questi valori vengono passati come argomento al metodo [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) per indicare i campi della struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) da inizializzare.

 Questi valori vengono inoltre utilizzati nel `dwFields` membro della `THREADPROPERTIES` struttura per indicare quali campi vengono utilizzati e validi.

 Questi flag possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
