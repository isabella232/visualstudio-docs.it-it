---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d1b2cd284611956be58c677f849236b246269fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745836"
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
  
 Valutazione della vulnerabilità  
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



