---
title: Funzione CvCreateMarkerSeries | Microsoft Docs
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
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24fb577cc08dd92b0179438cb07f14882a8b90bc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285831"
---
# <a name="cvcreatemarkerseries-function"></a>Funzione CvCreateMarkerSeries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea una serie di marcatori per un determinato provider.  
  
## <a name="syntax"></a>Sintassi  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProvider`  
 Oggetto provider preinizializzato tramite CvInitProvider. Non può essere NULL.  
  
 `pSeriesName`  
 Nome della serie di marcatori. Non può essere NULL, ma le stringhe vuote sono consentite.  
  
 `ppMarkerSeries`  
 Indirizzo di una variabile di output in cui viene memorizzato il contesto della serie di marcatori. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando la serie di marcatori viene creata correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)



