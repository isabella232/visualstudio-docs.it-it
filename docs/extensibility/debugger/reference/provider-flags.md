---
title: PROVIDER_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8408481efbcaa67ce60d2dbfc9166b5dd0fd5223
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350019"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Specifica le proprietà desiderate devono essere ottenuti da un provider di programma.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="fields"></a>Campi
 `PFLAG_NONE`\
 Nessun flag specificato.

 `PFLAG_REMOTE_PORT`\
 Il chiamante desidera un elenco di programmi in un computer diverso rispetto a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 `PFLAG_DEBUGGEE`\
 Il processo è in corso il debug da questa istanza di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 `PFLAG_ATTACH_TODEBUGGEE`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] è collegato al programma in fase di debug ma non è avviata.

 `PFLAG_REASON_WATCH`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sta controllando l'arrivo degli eventi.

 `PFLAG_GET_PROGRAM_NODES`\
 Chiamante desidera che il `ProgramNodes` campo le [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struttura.

 `PFLAG_GET_IS_DEBUGGER_PRESENT`\
 Chiamante desidera che il `fIsTheDebuggerPresent` campo il `PROVIDER_PROCESS_DATA` struttura.

## <a name="remarks"></a>Note
 Questi flag vengono passati ai metodi seguenti:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)