---
title: Proprietà IDebugMethodField::EnumParameters . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727192"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crea un enumeratore per i parametri del metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametri
`ppParams`\
[fuori] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di parametri per il metodo; in caso contrario, restituisce un valore null se non sono presenti parametri.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti parametri. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta diversi tipi di parametri. Chiamare il [getKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metodo su ogni oggetto per determinare esattamente il tipo di parametro rappresentato dall'oggetto.

 Un parametro include sia il nome della variabile che il tipo. Il primo parametro di un metodo di classe è in genere il puntatore "this".

 Se sono necessari solo i tipi dei parametri, chiamare il [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
