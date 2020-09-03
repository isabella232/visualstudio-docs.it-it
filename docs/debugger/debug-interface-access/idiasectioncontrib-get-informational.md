---
title: IDiaSectionContrib::get_informational | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d804ef0caa2f6fed3ef33e64f97e51fd81e466ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466252"
---
# <a name="idiasectioncontribget_informational"></a>IDiaSectionContrib::get_informational
Recupera un flag che indica se una sezione contiene commenti o informazioni simili.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_informational(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se la sezione contiene commenti o altre informazioni; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 In genere la sezione. Directive contiene informazioni.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)