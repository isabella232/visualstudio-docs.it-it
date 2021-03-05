---
description: Contiene informazioni su un processo.
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5557e4171bdeb51ae1ac954870a85227a8c4c92
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222094"
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

## <a name="members"></a>Members
 `Fields`\
 Combinazione di flag dell'enumerazione [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) che specificano i campi da compilare.

 `bstrFileName`\
 Nome del percorso completo del processo. Equivale a chiamare il metodo [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) con il parametro `GN_FILENAME` .

 `bstrBaseName`\
 Il nome file e l'estensione del processo. Equivale a chiamare il `IDebugProcess2::Getname` metodo con il parametro `GN_BASENAME` .

 `bstrTitle`\
 Titolo del processo, se ne esiste uno. Equivale a chiamare il `IDebugProcess2::Getname` metodo con il parametro `GN_TITLE` .

 `ProcessId`\
 Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) che identifica il processo. Equivale a chiamare il metodo [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .

 `dwSessionId`\
 Identificatore della sessione di debug in cui è in esecuzione il processo.

 `bstrAttachedSessionName`\
 Nome della sessione associata. Equivale a chiamare il metodo [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .

 `CreationTime`\
 Ora di creazione del processo.

 `Flags`\
 Combinazione di flag dell'enumerazione [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) che specificano le proprietà del processo.

## <a name="remarks"></a>Commenti
 Questa struttura viene passata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) dove viene compilata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
