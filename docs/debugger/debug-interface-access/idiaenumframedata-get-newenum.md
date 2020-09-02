---
title: IDiaEnumFrameData::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24bcd0772af8954ae198400734d87df1dad45abc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468336"
---
# <a name="idiaenumframedataget__newenum"></a>IDiaEnumFrameData::get__NewEnum
Recupera la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione dell'enumeratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce l' `IUnknown` interfaccia che rappresenta la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione dell'enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)