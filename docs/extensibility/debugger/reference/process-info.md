---
title: proprietà PROCESS_INFO . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713877"
---
# <a name="process_info"></a>PROCESS_INFO
Contiene informazioni su un processo.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Membri
 `Fields`\
 Combinazione di flag dell'enumerazione [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) che specificano i campi da compilare.

 `bstrFileName`\
 Nome del percorso completo del processo. Equivale a chiamare il metodo `GN_FILENAME` [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) con il parametro .

 `bstrBaseName`\
 Il nome file e l'estensione del processo. Equivale a `IDebugProcess2::Getname` chiamare il `GN_BASENAME`metodo con il parametro .

 `bstrTitle`\
 Titolo del processo, se presente. Equivale a `IDebugProcess2::Getname` chiamare il `GN_TITLE`metodo con il parametro .

 `ProcessId`\
 Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) che identifica il processo. Equivalente alla chiamata al metodo [GetPhysicalProcessId.](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

 `dwSessionId`\
 Identificatore della sessione di debug in cui è in esecuzione il processo.

 `bstrAttachedSessionName`\
 Nome della sessione allegato. Equivalente alla chiamata al metodo [GetAttachedSessionName.](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

 `CreationTime`\
 Ora di creazione del processo.

 `Flags`\
 Combinazione di flag dell'enumerazione [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) che specificano le proprietà del processo.

## <a name="remarks"></a>Osservazioni
 Questa struttura viene passata al [metodo GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) in cui viene compilata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
