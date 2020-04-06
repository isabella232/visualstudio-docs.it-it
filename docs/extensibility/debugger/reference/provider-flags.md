---
title: proprietà PROVIDER_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2333b62f21aa7b2b2bc70bddb50cbb3983cedf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713812"
---
# <a name="provider_flags"></a>PROVIDER_FLAGS
Specifica le proprietà desiderate da ottenere da un provider di programmi.

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
 Il chiamante desidera un elenco [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]di programmi su un computer diverso da .

 `PFLAG_DEBUGGEE`\
 È in corso il debug del [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]processo da questa istanza di .

 `PFLAG_ATTACH_TODEBUGGEE`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]è collegato al programma in fase di debug ma non l'ha avviato.

 `PFLAG_REASON_WATCH`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]sta guardando per gli eventi.

 `PFLAG_GET_PROGRAM_NODES`\
 Il chiamante vuole il `ProgramNodes` campo della struttura [PROVIDER_PROCESS_DATA.](../../../extensibility/debugger/reference/provider-process-data.md)

 `PFLAG_GET_IS_DEBUGGER_PRESENT`\
 Il chiamante vuole il `fIsTheDebuggerPresent` campo della `PROVIDER_PROCESS_DATA` struttura.

## <a name="remarks"></a>Osservazioni
 Questi flag vengono passati ai seguenti metodi:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Questi valori possono essere combinati `OR`con un file bit per bit.

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
