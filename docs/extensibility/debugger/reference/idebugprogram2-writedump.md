---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90d9d680ca83967f9f651269e186670fb90a771d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343626"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Scrive un dump di un file.

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
[in] Un valore compreso il [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumerazione che specifica il tipo di dump, ad esempio, short o long.

`pszDumpUrl`\
[in] URL di scrittura del dump. Si tratta in genere sotto forma di `file://c:\path\filename.ext`, ma può essere qualsiasi URL valido.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Un dump del programma in genere includerà lo stack frame corrente, lo stesso stack, un elenco dei thread in esecuzione nel programma e possibilmente memoria che possiede il programma.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)