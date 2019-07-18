---
title: Funzione CvInitProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5a8a9e70c85563e95037c754c59b6077ed21f28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188810"
---
# <a name="cvinitprovider-function"></a>Funzione CvInitProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inizializza il provider di marcatori. Deve essere chiamata prima di qualsiasi altra funzione SDK del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pGuid`  
 GUID del provider. Non può essere NULL.  
  
 `ppProvider`  
 Indirizzo di una variabile di output in cui verrà archiviato il contesto del provider. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando il provider è stato inizializzato correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)
