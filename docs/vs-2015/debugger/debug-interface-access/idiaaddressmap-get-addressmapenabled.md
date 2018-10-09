---
title: Get_addressmapenabled | Microsoft Docs
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
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24ee62fd6cefe858fef8089e1fe37589781f703b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529716"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_addressmapenabled](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled).  
  
Indica se è stato definito un mapping di indirizzi per una determinata sessione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce `TRUE` se è abilitato il mapping degli indirizzi.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Eseguibile postprocessori talvolta aggiornare il file eseguibile. DIA contiene un meccanismo per supportare la traduzione di simboli a cui il nuovo layout.  
  
 Le applicazioni client possono impostare il mapping di indirizzi per una particolare sessione tramite il recupero il [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) interfaccia dal [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia e la chiamata di [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo seguita da una chiamata per il [Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) (metodo). Il `get_addressMapEnabled` restituisce i risultati della chiamata al metodo il `put_addressMapEnabled` (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)


