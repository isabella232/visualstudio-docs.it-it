---
title: 'IDiaFrameData:: get_lengthBlock | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d66e8cd69836a6c2f8ee1052f5f5f7ff789f736
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62552540"
---
# <a name="idiaframedataget_lengthblock"></a>IDiaFrameData::get_lengthBlock
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la lunghezza, in byte, del blocco di codice descritto dal frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_lengthBlock (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce il numero di byte di codice nel frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore restituito da questo metodo viene in genere usato nell'interpretazione di una stringa di programma (vedere il metodo [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) per la definizione di una stringa di programma).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
