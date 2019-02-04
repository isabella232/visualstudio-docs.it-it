---
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b1f58f31484084bff502d9ad6a019089ecfec8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992521"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Legge dall'immagine della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `type`  
 [in] Uno dei [enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) valori di enumerazione che specifica il tipo di memoria per accedere.  
  
 `va`  
 [in] Percorso di indirizzo virtuale nell'immagine per iniziare la lettura.  
  
 `cbData`  
 [in] Dimensioni del buffer di dati, in byte.  
  
 `pcbData`  
 [out] Restituisce il numero di byte restituiti. Se `data` viene `NULL`, quindi `pcbData` contiene il numero totale di byte di dati disponibili.  
  
 `data`  
 [out] Un buffer che deve essere compilato con i dati dalla posizione specificata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)