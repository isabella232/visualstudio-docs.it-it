---
title: IDiaEnumSegments::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca94c078bb2b2598ffbe8e8098ac635cb698288
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744203"
---
# <a name="idiaenumsegmentsget__newenum"></a>IDiaEnumSegments::get__NewEnum
Recupera la versione <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> dell'enumeratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce l'interfaccia `IUnknown` che rappresenta la versione <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> dell'enumeratore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)