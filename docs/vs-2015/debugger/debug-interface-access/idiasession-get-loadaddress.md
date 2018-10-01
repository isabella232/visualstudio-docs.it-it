---
title: Get_loadaddress | Microsoft Docs
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
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbd8b4af8ad7f5495704588d7e2c0fff0d2caca7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517867"
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_loadaddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-get-loadaddress).  
  
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



