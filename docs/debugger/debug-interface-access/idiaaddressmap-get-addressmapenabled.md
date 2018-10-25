---
title: Get_addressmapenabled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47d0b3ac64724881ab72cb9d9d873bc02f3bec9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938838"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indica se è stato definito un mapping di indirizzi per una determinata sessione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
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