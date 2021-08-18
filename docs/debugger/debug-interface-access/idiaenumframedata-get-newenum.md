---
description: Recupera la versione System.Runtime.InteropServices.ComTypes.IEnumVARIANT dell'enumeratore di dati del frame.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 90cdae350c90722cf98611a270c35753cd12197a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134601"
---
# <a name="idiaenumframedataget__newenum"></a>IDiaEnumFrameData::get__NewEnum
Recupera la versione <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> di questo enumeratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce `IUnknown` l'interfaccia che rappresenta <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> la versione di questo enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
