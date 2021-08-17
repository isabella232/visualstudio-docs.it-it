---
description: È stato specificato il tipo di informazioni da recuperare per un processo.
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cdcf987151af31e9f8921bfca3f758b20b818e32
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029177"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
È stato specificato il tipo di informazioni da recuperare per un processo.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PROCESS_INFO_FIELDS { 
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
public enum enum_PROCESS_INFO_FIELDS { 
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
 Inizializzare/usare `bstrFileName` il campo della [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura .

 `PIF_BASE_NAME`\
 Inizializzare/usare `bstrBaseName` il campo della struttura `PROCESS_INFO` .

 `PIF_TITLE`\
 Inizializzare/usare `bstrTitle` il campo della struttura `PROCESS_INFO` .

 `PIF_PROCESS_ID`\
 Inizializzare/usare `ProcessId` il campo della struttura `PROCESS_INFO` .

 `PIF_SESSION_ID`\
 Inizializzare/usare `dwSessionId` il campo della struttura `PROCESS_INFO` .

 `PIF_ATTACHED_SESSION_NAME`\
 Inizializzare/usare `bstrAttachedSessionName` il campo della struttura `PROCESS_INFO` .

 `PIF_CREATION_TIME`\
 Inizializzare/usare `CreationTime` il campo della struttura `PROCESS_INFO` .

 `PIF_FLAGS`\
 Inizializzare/usare `Flags` il campo della struttura `PROCESS_INFO` .

 `PIF_ALL`\
 Compila tutti i campi.

## <a name="remarks"></a>Commenti
 Passato al [metodo GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) per indicare quali campi della [struttura](../../../extensibility/debugger/reference/process-info.md) PROCESS_INFO devono essere inizializzati.

 Usato anche `Fields` nel campo della struttura per indicare quali campi vengono usati e `PROCESS_INFO` validi.

 Questi flag possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
