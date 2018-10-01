---
title: Idiastackwalkframe | Microsoft Docs
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
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e4bad4128ca89cf90ccf1c361bcc6de11d1d8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527869"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Idiastackwalkframe](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkframe-readmemory).  
  
Legge dall'immagine della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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



