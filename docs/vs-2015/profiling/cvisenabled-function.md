---
title: Funzione CvIsEnabled | Microsoft Docs
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
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4349d42309482622ae57ba27bb3e675bbdd6a403
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222469"
---
# <a name="cvisenabled-function"></a>Funzione CvIsEnabled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Determina se vi sono sessioni che hanno abilitato il provider ETW specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `category`  
 Categoria.  
  
 `level`  
 Livello di importanza.  
  
 `pProvider`  
 Oggetto provider valido. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il provider è stato abilitato correttamente. S_FALSE se il provider attualmente è disabilitato. Codice dell'errore nel caso in cui si siano verificati errori. Usare la macro FAILED per verificare la condizione di errore e quindi verificare la presenza di S_OK/S_FALSE.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)



