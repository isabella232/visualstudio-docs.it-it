---
title: Get_allocatesbasepointer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 90a32930c51caad61e07b0e6fdfe5b164a5515bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954581"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che indica se il puntatore di base viene allocato per il codice in questo intervallo di indirizzi. Metodo deprecato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se viene allocato un base puntatore; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questa proprietà deve essere usata solo dal codice che in precedenza l'accesso FPO_DATA o quando la stringa viene restituita dal [Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) metodo `NULL`. In caso contrario, la stringa nel programma contiene tutte le informazioni necessarie per il calcolo dei valori di registro precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
