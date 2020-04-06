---
title: proprietà PROCESS_INFO_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714018"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Specifica il tipo di informazioni da recuperare per un processo.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Campi
 `PIF_FILE_NAME`\
 Inizializzare/utilizzare `bstrFileName` il campo della [struttura PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

 `PIF_BASE_NAME`\
 Inizializzare/utilizzare `bstrBaseName` il `PROCESS_INFO` campo della struttura.

 `PIF_TITLE`\
 Inizializzare/utilizzare `bstrTitle` il `PROCESS_INFO` campo della struttura.

 `PIF_PROCESS_ID`\
 Inizializzare/utilizzare `ProcessId` il `PROCESS_INFO` campo della struttura.

 `PIF_SESSION_ID`\
 Inizializzare/utilizzare `dwSessionId` il `PROCESS_INFO` campo della struttura.

 `PIF_ATTACHED_SESSION_NAME`\
 Inizializzare/utilizzare `bstrAttachedSessionName` il `PROCESS_INFO` campo della struttura.

 `PIF_CREATION_TIME`\
 Inizializzare/utilizzare `CreationTime` il `PROCESS_INFO` campo della struttura.

 `PIF_FLAGS`\
 Inizializzare/utilizzare `Flags` il `PROCESS_INFO` campo della struttura.

 `PIF_ALL`\
 Compila tutti i campi.

## <a name="remarks"></a>Osservazioni
 Passato al metodo [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) per indicare quali campi della struttura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) devono essere inizializzati.

 Utilizzato anche `Fields` nel `PROCESS_INFO` campo della struttura per indicare quali campi vengono utilizzati e validi.

 Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
