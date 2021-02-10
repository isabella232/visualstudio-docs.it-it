---
title: IDebugGenericFieldInstance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06711f7112aaa528b7274867bc133368075d19ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934377"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
Rappresenta un'istanza di un campo per un tipo generico di codice gestito.

## <a name="syntax"></a>Sintassi

```
IDebugGenericFieldInstance : IUnknown
```

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Recupera gli argomenti del parametro di tipo per questa istanza.|
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Restituisce il numero di argomenti del parametro di tipo per questa istanza.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
