---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969769"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legge un blocco di dati dall'immagine del file eseguibile in memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
