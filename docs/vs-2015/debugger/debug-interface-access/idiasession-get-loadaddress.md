---
title: Get_loadaddress | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b79648e5844f49861ece700f4e3b35ea9b09d958
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950121"
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un indirizzo virtuale (valutazione della vulnerabilità) in cui viene caricato un file .exe o file con estensione dll.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'indirizzo di caricamento restituito è sempre zero, a meno che specificamente impostati utilizzando il [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)



