---
title: 'IDebugMethodField:: EnumParameters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c164fa08f4195d685bf7dd2faa120ff030e44c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837723"
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
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di parametri per il metodo. in caso contrario, restituisce un valore null se non sono presenti parametri.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti parametri. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Ogni elemento è un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta tipi diversi di parametri. Chiamare il metodo [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) su ogni oggetto per determinare esattamente il tipo di parametro rappresentato dall'oggetto.

 Un parametro include il nome della variabile e il relativo tipo. Il primo parametro di un metodo di classe è in genere il puntatore "This".

 Se sono necessari solo i tipi di parametri, chiamare il metodo [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
