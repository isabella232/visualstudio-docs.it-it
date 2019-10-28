---
title: IDiaSymbol::get_frontEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b329cd69d010cba4e3667bde0d7b976389037bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740641"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
Recupera il numero della versione secondaria del front-end.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di versione secondario front. end.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Un compilatore è in genere costituito da due elementi primari: il front-end (il parser), che gestisce l'analisi del codice sorgente in un form intermedio e un back-end (Generatore di codice), che converte il modulo intermedio in assembly. Non è insolito che il front-end disponga di una versione diversa da quella del back-end.

 Un numero di versione front-end o back-end è costituito da tre parti: \<major >. \<minor >. \<build >, dove \<major > è il numero di versione principale, \<minor > è il numero di versione secondario e \<build > è il numero di Build. Ad esempio, 13.10.3077.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)