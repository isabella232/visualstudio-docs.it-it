---
title: Get_relativevirtualaddressenabled | Microsoft Docs
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
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d64f41285c0114d78df4035d11a6d92c714717bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532163"
---
# <a name="idiaaddressmapgetrelativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_relativevirtualaddressenabled](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled).  
  
Indica se il calcolo e l'utilizzo di indirizzi virtuali relativi (RVA) è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce `TRUE` se è abilitato il calcolo delle RVA.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 RVA abilitati se i segmenti sono stati inizialmente caricati da un file PDB. L'uso di RVA può essere disabilitato temporaneamente chiamando il [Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) (metodo).  
  
 Inoltre, è possibile stabilire nuove intestazioni di immagine chiamando il [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metodo seguita da una chiamata al `put_relativeVirtualAddressEnabled` metodo per abilitare l'uso del RVA usando le nuove intestazioni di immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



