---
title: Funzione CvWriteAlert | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9e1fc900e2fc5413817784e229b1047371f6816
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528220"
---
# <a name="cvwritealert-function"></a>Funzione CvWriteAlert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione CvWriteAlert](https://docs.microsoft.com/visualstudio/profiling/cvwritealert-function).  
  
Scrive un avviso nel file di traccia del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Parametri  
 `argList`  
 Elenco di argomenti.  
  
 `pMarkerSeries`  
 Contesto della serie di marcatori valido. Non può essere NULL.  
  
 `pMessage`  
 Stringa di formato del messaggio. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando il messaggio è stato scritto correttamente. Codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
 **Unicode:** CvWriteAlertW, CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA, CvWriteAlertVA  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)



