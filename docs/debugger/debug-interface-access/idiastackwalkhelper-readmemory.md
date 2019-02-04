---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 229aace046dfebd75786dfa5c14998d9498b98b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967102"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Legge un blocco di dati dall'immagine del file eseguibile in memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `type`  
 [in] Un valore compreso il [enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) enumerazione che specifica il tipo di memoria da leggere.  
  
 va  
 [in] Indirizzo virtuale dell'immagine da cui iniziare la lettura.  
  
 `cbData`  
 [in] Le dimensioni del buffer di dati in byte.  
  
 `pcbData`  
 [out] Restituisce il numero di byte effettivamente letti. Se `pbData` è `NULL`, il valore è il numero totale di byte di dati disponibili.  
  
 `pbData`  
 [in, out] Un buffer che viene compilato con la memoria di lettura.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)