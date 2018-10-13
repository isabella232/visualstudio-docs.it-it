---
title: Funzione CvReleaseProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5b644dfdb469d84b90a1a0d7d59651fbad2460b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300781"
---
# <a name="cvreleaseprovider-function"></a>Funzione CvReleaseProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rilascia un provider di marcatori. Il rilascio del provider di marcatori non influisce sulle serie di marcatori del provider create in precedenza. Le serie di marcatori devono essere rilasciate separatamente dalla chiamata CvReleaseMarkerSeries. Il mancato rilascio del provider di marcatori causa una perdita di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProvider`  
 Contesto del provider. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando il provider è stato rilasciato correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)



