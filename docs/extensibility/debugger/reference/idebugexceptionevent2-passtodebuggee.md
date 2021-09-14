---
description: Specifica se l'eccezione deve essere passata al programma in fase di debug alla ripresa dell'esecuzione o se l'eccezione deve essere eliminata.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd9360bfc5647c5edd244818f64570c6ca5554f7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710304"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Specifica se l'eccezione deve essere passata al programma in fase di debug alla ripresa dell'esecuzione o se l'eccezione deve essere eliminata.

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
[in] Diverso da zero ( ) se l'eccezione deve essere passata al programma in fase di debug alla ripresa dell'esecuzione oppure zero ( ) se l'eccezione `TRUE` `FALSE` deve essere eliminata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La chiamata a questo metodo non causa effettivamente l'esecuzione di codice nel programma di cui viene eseguito il debug. La chiamata è semplicemente per impostare lo stato per la successiva esecuzione del codice. Ad esempio, le chiamate al [metodo CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) possono restituire con EXCEPTION_INFO `S_OK` . [](../../../extensibility/debugger/reference/exception-info.md)`dwState` campo impostato su `EXCEPTION_STOP_SECOND_CHANCE` .

 L'IDE può ricevere [l'evento IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chiamare il [metodo Continue.](../../../extensibility/debugger/reference/idebugprogram2-continue.md) Il motore di debug deve avere un comportamento predefinito per gestire il caso se `PassToDebuggee` il metodo non viene chiamato.

## <a name="see-also"></a>Vedi anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
