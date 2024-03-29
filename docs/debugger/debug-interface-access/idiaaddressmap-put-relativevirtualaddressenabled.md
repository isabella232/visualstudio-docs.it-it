---
description: Consente al client di abilitare o disabilitare il calcolo e l'uso di indirizzi virtuali relativi.
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9cfb2e9b3b77adb5e0b16b896100b5b9eab04596
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630528"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Consente al client di abilitare o disabilitare il calcolo e l'uso di indirizzi virtuali relativi.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametri
 NewVal

[in] Impostare su `TRUE` per abilitare o `FALSE` disabilitare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Gli indirizzi per gli oggetti di debug descritti dalle interfacce DIA e relativi alla base di immagini del file eseguibile possono essere recuperati come indirizzi virtuali relativi.

 L'uso di RVA è abilitato quando i segmenti vengono caricati inizialmente da un file PDB. Per ottenere lo stato corrente dell'uso di RVA, chiamare il [metodo IDiaAddressMap::get_relativeVirtualAddressEnabled.](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)

 Il metodo deve essere chiamato per abilitare gli RVA dopo che una chiamata riuscita al metodo `put_relativeVirtualAddress` [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) ha stabilito nuove intestazioni di immagine.

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
