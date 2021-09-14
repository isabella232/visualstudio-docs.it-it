---
description: Specifica quali informazioni su un thread devono essere recuperate.
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c70e331de05b3288e1105832616acb1d3359b049
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634732"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Specifica quali informazioni su un thread devono essere recuperate.

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
 Inizializzare/usare `dwThreadId` il campo della struttura [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Inizializzare/usare `dwSuspendCount` il campo della struttura `THREADPROPERTIE` S.

 `TPF_STATE`\
 Inizializzare/usare `dwThreadState` il campo della struttura `THREADPROPERTIE` S.

 `TPF_PRIORITY`\
 Inizializzare/usare `bstrPriority` il campo della struttura `THREADPROPERTIE` S.

 `TPF_NAME`\
 Inizializzare/usare `bstrName` il campo della struttura `THREADPROPERTIE` S.

 `TPF_LOCATION`\
 Inizializzare/usare `bstrLocation` il campo della struttura `THREADPROPERTIE` S.

 `TPF_ALLFIELDS`\
 Specifica tutti i campi.

## <a name="remarks"></a>Commenti
 Questi valori vengono passati come argomento al [metodo GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) per indicare quali campi della struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) devono essere inizializzati.

 Questi valori vengono usati anche nel `dwFields` membro della struttura per indicare quali campi vengono usati e `THREADPROPERTIES` validi.

 Questi flag possono essere combinati con un bit per `OR` bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
