---
description: Indica all'autore del programma che un debugger è presente ed è in esecuzione.
title: IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23c5c59e738eb49c148a873248cd6eae08f04f14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063993"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Indica all'autore del programma che un debugger è presente ed è in esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>Parametri
`fDebuggerPresent`\
[in] Diverso da zero ( `TRUE` ) se è presente un debugger, zero ( ) in caso `FALSE` contrario.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La presenza o l'assenza di un debugger si riflette nei dati restituiti dal metodo [GetProviderProcessData:](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) il valore restituito viene impostato o cancellato da una chiamata precedente al `SetDebuggerPresent` metodo .

## <a name="see-also"></a>Vedi anche
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
