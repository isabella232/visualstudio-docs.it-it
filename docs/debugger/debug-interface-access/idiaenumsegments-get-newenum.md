---
description: Recupera la versione System.Runtime.InteropServices.ComTypes.IEnumVARIANT dell'enumeratore segments.
title: IDiaEnumSegments::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 290f97a34b1564deda79df7976edaf9b95abc953
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630144"
---
# <a name="idiaenumsegmentsget__newenum"></a>IDiaEnumSegments::get__NewEnum
Recupera la versione <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> di questo enumeratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce `IUnknown` l'interfaccia che rappresenta la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
