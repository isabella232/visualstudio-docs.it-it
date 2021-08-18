---
description: Recupera gli argomenti dei parametri di tipo per questa istanza.
title: IDebugGenericFieldInstance::GetTypeArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5ec9596b145835fd9667e04d674e6d953bfba5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088549"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
Recupera gli argomenti dei parametri di tipo per questa istanza.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetTypeArguments(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   ULONG32*      pcArgs
);
```

```csharp
int GetTypeArguments(
   uint              cArgs,
   out IDebugField[] ppArgs,
   ref uint          pcArgs
);
```

## <a name="parameters"></a>Parametri
`cArgs`\
[in] Numero di parametri di tipo.

`ppArgs`\
[out] Restituisce una matrice di parametri di tipo.

`pcArgs`\
[in, out] Numero di membri nella `ppArgs` matrice.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
