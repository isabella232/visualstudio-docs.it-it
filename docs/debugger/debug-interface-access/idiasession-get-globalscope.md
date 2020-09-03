---
title: IDiaSession::get_globalScope | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_globalScope method
ms.assetid: 75d128a8-3dce-40ed-b392-de3fdda041b7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc1e935ab47fd815c8f132dbeee21e21c9ba6350
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465447"
---
# <a name="idiasessionget_globalscope"></a>IDiaSession::get_globalScope
Recupera un riferimento all'ambito globale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_globalScope ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta l'ambito globale.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)