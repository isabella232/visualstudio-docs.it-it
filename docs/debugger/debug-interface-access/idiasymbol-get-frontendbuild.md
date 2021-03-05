---
description: Recupera il numero di build front-end.
title: IDiaSymbol::get_frontEndBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9f12777b41cca5e4bf654318b72bc98e52ccede
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162159"
---
# <a name="idiasymbolget_frontendbuild"></a>IDiaSymbol::get_frontEndBuild
Recupera il numero di build front-end.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_frontEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di build front-end. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un compilatore è in genere costituito da due elementi primari: il front-end (il parser), che gestisce l'analisi del codice sorgente in un form intermedio e un back-end (Generatore di codice), che converte il modulo intermedio in assembly. Non è insolito che il front-end disponga di una versione diversa da quella del back-end.

 Un numero di versione front-end o back-end è costituito da tre parti: \<major> . \<minor> . \<build> , dove \<major> è il numero di versione principale, \<minor> è il numero di versione secondario e \<build> è il numero di Build. Ad esempio, 13.10.3077.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
