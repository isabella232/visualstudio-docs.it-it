---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722733"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Scrive un dump in un file.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parametri
`DumpType`\
in Valore dell'enumerazione [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) che specifica il tipo di dump, ad esempio short o Long.

`pszDumpUrl`\
in URL in cui scrivere il dump. In genere, il formato è `file://c:\path\filename.ext` , ma può essere qualsiasi URL valido.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il dump di un programma include in genere i stack frame correnti, lo stack stesso, un elenco dei thread in esecuzione nel programma e possibilmente qualsiasi memoria di proprietà del programma.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
