---
title: 'IDiaFrameData:: get_functionParent | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218a1df4f700ad33aa0af0aa453de84cbdae1752
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203645"
---
# <a name="idiaframedataget_functionparent"></a>IDiaFrameData::get_functionParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un'interfaccia dati frame per la funzione contenitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_functionParent (   
   IDiaFrameData** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce un oggetto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) per la funzione contenitore.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
