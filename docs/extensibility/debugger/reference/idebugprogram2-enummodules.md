---
description: Recupera un elenco dei moduli caricati e in esecuzione da questo programma.
title: IDebugProgram2::EnumModules | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c2d24fefab1e948c636f30ed4d7764a5ab83cc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126622"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Recupera un elenco dei moduli caricati e in esecuzione da questo programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce un [oggetto IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) che contiene un elenco dei moduli.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un modulo è una DLL o un assembly ed è in genere elencato nella finestra **di** debug Moduli.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
