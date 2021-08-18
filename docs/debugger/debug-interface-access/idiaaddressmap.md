---
description: Fornisce il controllo sul modo in cui DIA SDK gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f6e8d8a803f471d6e856da987ea70a1f121bfae5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036620"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Fornisce il controllo sul modo in cui DIA SDK gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.

## <a name="syntax"></a>Sintassi

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDiaAddressMap` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica se è stata stabilita una mappa indirizzi per una sessione specifica.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Specifica se la mappa indirizzi deve essere usata per convertire gli indirizzi dei simboli.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se il calcolo e l'uso di indirizzi virtuali relativi sono abilitati.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Consente al client di abilitare o disabilitare il calcolo degli indirizzi virtuali relativi.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera l'allineamento dell'immagine corrente.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Imposta l'allineamento dell'immagine.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Imposta le intestazioni delle immagini per abilitare la conversione di indirizzi virtuali relativi.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornisce una mappa indirizzi per supportare le traduzioni del layout delle immagini.|

## <a name="remarks"></a>Commenti
 Il controllo fornito da questa interfaccia è incapsulato in due set di dati forniti: intestazioni di immagine e mappe indirizzi. La maggior parte dei client usa il metodo [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) per trovare le informazioni di debug appropriate per un'immagine e il metodo può in genere individuare tutte le intestazioni necessarie e mappare i dati stessi. Tuttavia, alcuni client implementano l'elaborazione specializzata e la ricerca di dati. Tali client usano i metodi dell'interfaccia per fornire il DIA SDK `IDiaAddressMap` con i risultati della ricerca.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è disponibile dall'oggetto sessione DIA. Il client chiama il `QueryInterface` metodo sull'interfaccia dell'oggetto sessione DIA, in genere [IDiaSession](../../debugger/debug-interface-access/idiasession.md), per recuperare l'interfaccia. `IDiaAddressMap`

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
