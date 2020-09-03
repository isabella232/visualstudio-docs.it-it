---
title: IDiaStackWalkFrame::get_registerValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c420266d08550398f33c2e2da9ba1b7bc41b5dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141925"
---
# <a name="idiastackwalkframeget_registervalue"></a>IDiaStackWalkFrame::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il valore di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 in Valore dell'enumerazione [CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumerazione che specifica il registro per il quale ottenere il valore.  
  
 `pRetVal`  
 out Restituisce il valore corrente del registro.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
