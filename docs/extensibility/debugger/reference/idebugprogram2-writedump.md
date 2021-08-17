---
description: Scrive un dump in un file.
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1cbe4f60032be54f3b76d1b9f98701b0a5e52c00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030074"
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
[in] Valore [dell'enumerazione DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) che specifica il tipo di dump, ad esempio short o long.

`pszDumpUrl`\
[in] URL in cui scrivere il dump. In genere, il formato è `file://c:\path\filename.ext` , ma può essere qualsiasi URL valido.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un dump del programma include in genere il stack frame corrente, lo stack stesso, un elenco dei thread in esecuzione nel programma ed eventualmente qualsiasi memoria di proprietà del programma.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
