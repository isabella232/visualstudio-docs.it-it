---
description: Specifica se l'eccezione deve essere passata al programma di cui è in corso il debug al riavvio dell'esecuzione o se l'eccezione deve essere eliminata.
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81af5686cfc2b99dc3bf5d95e2ec283933297e2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084766"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Specifica se l'eccezione deve essere passata al programma di cui è in corso il debug al riavvio dell'esecuzione o se l'eccezione deve essere eliminata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parametri
`fPass`\
in Diverso da zero ( `TRUE` ) se l'eccezione deve essere passata al programma di cui è in corso il debug quando l'esecuzione riprende o zero ( `FALSE` ) se l'eccezione deve essere eliminata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La chiamata a questo metodo non determina l'esecuzione di codice nel programma di cui è in corso il debug. La chiamata consiste semplicemente nell'impostare lo stato per l'esecuzione del codice successiva. Ad esempio, le chiamate al metodo [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) possono restituire `S_OK` con la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` il campo è impostato su `EXCEPTION_STOP_SECOND_CHANCE` .

 L'IDE può ricevere l'evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chiamare il metodo [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . Il motore di debug (DE) deve avere un comportamento predefinito per gestire il caso se il `PassToDebuggee` metodo non viene chiamato.

## <a name="see-also"></a>Vedi anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
