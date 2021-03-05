---
description: Questa interfaccia rappresenta l'indirizzo di un elemento.
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f49107e4d06fa828d059ebd9916ca254882ff0a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154964"
---
# <a name="idebugaddress"></a>IDebugAddress
Questa interfaccia rappresenta l'indirizzo di un elemento. Viene restituito dal gestore di simboli.

## <a name="syntax"></a>Sintassi

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia per rappresentare un indirizzo di un oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Molti metodi su molte interfacce restituiscono questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera una struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) che descrive un oggetto e la relativa posizione.|

## <a name="remarks"></a>Commenti
 Il provider di simboli restituisce questa interfaccia per rappresentare un oggetto e la relativa posizione all'interno di un ambito specifico (ad esempio, funzione, metodo o classe). Questa interfaccia viene restituita da e passata a diversi metodi del provider di simboli e dell'analizzatore di espressioni. In genere, il provider di simboli è l'unica entità che deve interpretare il contenuto di questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
