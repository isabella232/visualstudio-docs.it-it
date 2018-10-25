---
title: Get_crc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f99c48af26f2b40969ec818743ec8f4d220f8404
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900618"
---
# <a name="idiainjectedsourcegetcrc"></a>IDiaInjectedSource::get_crc
Recupera un controllo di ridondanza ciclico (CRC) calcolato a partire dal byte del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_crc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il CRC calcolato dai byte del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)