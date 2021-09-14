---
description: Recupera la parte di sezione di un percorso di indirizzi.
title: IDiaSymbol::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6e90d81f857aa0088288a1d54db72e3d5de86787
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709969"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Recupera la parte di sezione di un percorso di indirizzi. Utilizzare quando [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsStatic` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce la parte di sezione di un percorso di indirizzi.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Per i membri statici che si trovano in una DLL esterna, la sezione restituita da questo metodo può essere 0 perché questo metodo si basa su come ottenere l'indirizzo virtuale del membro. Gli indirizzi virtuali sono validi solo se il [metodo IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) nell'interfaccia [IDiaSession](../../debugger/debug-interface-access/idiasession.md) è stato chiamato con un parametro diverso da zero che specifica l'indirizzo di caricamento della DLL.

 Per ottenere la parte offset di un indirizzo, chiamare il [metodo IDiaSymbol::get_addressOffset.](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
