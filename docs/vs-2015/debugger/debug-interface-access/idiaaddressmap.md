---
title: IDiaAddressMap | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd3f624e7b6889b64d81e06792404ff20839b03e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528071"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDiaAddressMap](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap).  
  
Consente di controllare come il DIA SDK calcola virtuali e relativi indirizzi virtuali per gli oggetti di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaAddressMap`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica se è stato definito un mapping di indirizzi per una determinata sessione.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Specifica se la mappa indirizzi deve essere utilizzata per convertire gli indirizzi di simboli.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se il calcolo e l'utilizzo di indirizzi virtuali relativi è abilitata.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Consente al client abilitare o disabilitare il calcolo di indirizzi virtuali relativi.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera l'allineamento dell'immagine corrente.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Imposta l'allineamento dell'immagine.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Set di intestazioni per abilitare la conversione degli indirizzi virtuale relativi dell'immagine.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornisce un mapping di indirizzi per supportare le traduzioni di layout di immagine.|  
  
## <a name="remarks"></a>Note  
 Il controllo specificato da questa interfaccia è incapsulato in due set di dati è fornire: esegue il mapping di indirizzi o un'immagine di intestazioni. La maggior parte dei client utilizzano le [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo per trovare le informazioni di debug appropriati per un'immagine e il metodo può in genere individuare tutti i dati di intestazioni e le mappe necessari se stesso. Alcuni client tuttavia implementare l'elaborazione specializzata e la ricerca di dati. Tali client utilizzano i metodi del `IDiaAddressMap` interfaccia per fornire il DIA SDK con i risultati della ricerca.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è disponibile dall'oggetto sessione DIA. Il client chiama il `QueryInterface` metodo DIA sessione oggetto interfaccia, in genere [IDiaSession](../../debugger/debug-interface-access/idiasession.md)per recuperare il `IDiaAddressMap` interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)


