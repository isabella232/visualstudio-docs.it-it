---
description: Recupera il numero di versione principale back-end del compilatore.
title: IDiaSymbol::get_backEndMajor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c623f74bfa0e13cf53d3777379ff18936c9242c09b6a4f2e022f12d79230718a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420848"
---
# <a name="idiasymbolget_backendmajor"></a>IDiaSymbol::get_backEndMajor
Recupera il numero di versione principale back-end del compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di versione principale back-end. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un compilatore è in genere costituito da due elementi primari: il front-end (parser), che gestisce l'analisi del codice sorgente in una forma intermedia, e un back-end (generatore di codice), che converte il modulo intermedio in assembly. Non è insolito che il front-end abbia una versione diversa rispetto al back-end.

 Un numero di versione front-end o back-end è costituito da tre parti: . . , dove è il numero di versione principale, è il numero di versione secondaria e \<major> è il numero di \<minor> \<build> \<major> \<minor> \<build> build. Ad esempio, 13.10.3077.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
