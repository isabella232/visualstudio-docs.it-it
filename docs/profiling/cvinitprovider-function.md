---
title: Funzione CvInitProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a97be63cd782397e984fd8dbce7da844efa07540
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552667"
---
# <a name="cvinitprovider-function"></a>Funzione CvInitProvider
Inizializza il provider di marcatori. Deve essere chiamata prima di qualsiasi altra funzione SDK del visualizzatore di concorrenza.

## <a name="syntax"></a>Sintassi

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametri
 `pGuid` GUID del provider. Non può essere NULL.

 `ppProvider` Indirizzo di una variabile di output in cui verrà archiviato il contesto del provider. Non può essere NULL.

## <a name="return-value"></a>Valore restituito
 S_OK quando il provider è stato inizializzato correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

## <a name="see-also"></a>Vedere anche
- [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)