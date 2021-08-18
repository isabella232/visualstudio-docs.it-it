---
description: Recupera il nome del file oggetto.
title: IDiaSymbol::get_objectFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 636f0d3f2fcd827a32a5e683f4465c97d03d2d06
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121353"
---
# <a name="idiasymbolget_objectfilename"></a>IDiaSymbol::get_objectFileName
Recupera il nome del file oggetto.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_objectFilename(
   BSTR *pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Puntatore a un oggetto `BSTR` che contiene il nome del file oggetto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
