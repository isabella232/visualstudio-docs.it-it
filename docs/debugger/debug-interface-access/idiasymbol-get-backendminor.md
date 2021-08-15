---
description: Recupera il numero di versione secondaria del back-end del compilatore.
title: IDiaSymbol::get_backEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b48c3a2e5042137ceed4c8655ec2d080c597f99d2c060b3b19a7130f31372564
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312052"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
Recupera il numero di versione secondaria del back-end del compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_backEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di versione secondaria del back-end. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un compilatore è in genere costituito da due elementi principali: il front-end (parser), che gestisce l'analisi del codice sorgente in un formato intermedio, e un back-end (generatore di codice), che converte il formato intermedio in assembly. Non è insolito che il front-end abbia una versione diversa rispetto al back-end.

 Un numero di versione front-end o back-end è costituito da tre parti: . . , dove è il numero di versione principale, è il numero di versione secondaria e \<major> è il numero di \<minor> \<build> \<major> \<minor> \<build> build. Ad esempio, 13.10.3077.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
