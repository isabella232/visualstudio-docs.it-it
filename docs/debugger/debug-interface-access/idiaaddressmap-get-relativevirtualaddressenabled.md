---
description: Indica se il calcolo e l'uso di indirizzi virtuali relativi (RVA) sono abilitati.
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a6c43531706fe1de3163d0bb69c56c66f8133fb9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630545"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Indica se il calcolo e l'uso di indirizzi virtuali relativi (RVA) sono abilitati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce `TRUE` se il calcolo degli RVA è abilitato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Gli RVA sono abilitati se i segmenti sono stati caricati inizialmente da un file PDB. L'uso di RVA può essere temporaneamente disabilitato chiamando il metodo [IDiaAddressMap::p ut_relativeVirtualAddressEnabled.](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)

 È anche possibile stabilire nuove intestazioni di immagine chiamando il metodo [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) seguito da una chiamata al metodo per abilitare l'uso degli RVA usando le nuove intestazioni di `put_relativeVirtualAddressEnabled` immagine.

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
