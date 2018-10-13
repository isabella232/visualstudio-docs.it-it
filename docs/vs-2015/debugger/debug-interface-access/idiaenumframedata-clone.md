---
title: Idiaenumframedata | Microsoft Docs
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
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33ec31ff57edd238bd92c78655709cea9088d512
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232765"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 ppenum  
 [out] Restituisce un [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) oggetto che contiene un duplicato dell'enumeratore. Il frame di dati non sono duplicato, solo l'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)



