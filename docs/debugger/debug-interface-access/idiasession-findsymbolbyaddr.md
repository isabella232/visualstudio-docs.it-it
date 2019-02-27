---
title: IDiaSession::findSymbolByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByAddr method
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcbe9e97eb429fa7427ae0e3da4dce77281b40a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625881"
---
# <a name="idiasessionfindsymbolbyaddr"></a>IDiaSession::findSymbolByAddr
Recupera un tipo di simbolo specificato che contiene, o è più vicino, l'indirizzo specificati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findSymbolByAddr ( 
   DWORD        isect,
   DWORD        offset,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametri
 `isect`

[in] Specifica il componente di sezione dell'indirizzo.

 `offset`

[in] Specifica il componente offset dell'indirizzo.

 `symtag`

[in] Tipo di simbolo da trovare. I valori sono ricavati dal [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione.

 `ppSymbol`

[out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperare l'oggetto che rappresenta il simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)