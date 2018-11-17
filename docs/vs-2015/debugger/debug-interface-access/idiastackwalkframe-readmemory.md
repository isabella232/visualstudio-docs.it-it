---
title: Idiastackwalkframe | Microsoft Docs
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
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56276b03331be1da98a20e27b48b669b3127d8ae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747866"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



