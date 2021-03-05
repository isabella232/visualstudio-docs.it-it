---
description: Usato per impostare i punti di interruzione del codice in base a una stringa che l'utente può immettere dall'Integrated Development Environment (IDE).
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9508a4a83894757fb47e35d8db7334bfb144ff59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144377"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Usato per impostare i punti di interruzione del codice in base a una stringa che l'utente può immettere dall'Integrated Development Environment (IDE).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Members
`bstrContext`\
Contesto del punto di interruzione all'interno del codice, in genere un metodo o un nome di funzione come visualizzato in uno stack di chiamate.

`bstrCodeExpr`\
Stringa che l'utente digita per descrivere il punto di interruzione del codice.

## <a name="remarks"></a>Commenti
Questa struttura è un membro della struttura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) come parte di un'Unione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
