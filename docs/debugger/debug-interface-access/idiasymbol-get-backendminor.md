---
description: Recupera il numero di versione secondaria back-end del compilatore.
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
ms.openlocfilehash: 12629d6cbda5a2ebd49e526bab48e9eb9257a28a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036247"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
Recupera il numero di versione secondaria back-end del compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_backEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di versione secondaria back-end. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un compilatore è in genere costituito da due elementi primari: il front-end (parser), che gestisce l'analisi del codice sorgente in un formato intermedio, e un back-end (generatore di codice), che converte il formato intermedio in assembly. Non è insolito che il front-end abbia una versione diversa rispetto al back-end.

 Un numero di versione front-end o back-end è costituito da tre parti: . . , dove è il numero di versione principale, è il numero di versione secondaria e \<major> è il numero di \<minor> \<build> \<major> \<minor> \<build> build. Ad esempio, 13.10.3077.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
