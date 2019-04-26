---
title: Funzione CvIsEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92763e352d04d5aa3e88a68bad7adfcd05897027
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945414"
---
# <a name="cvisenabled-function"></a>Funzione CvIsEnabled
Determina se vi sono sessioni che hanno abilitato il provider ETW specifico.

## <a name="syntax"></a>Sintassi

```C
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
 `category` Categoria.

 `level` Livello di importanza.

 `pProvider` Oggetto provider valido. Non può essere NULL.

## <a name="return-value"></a>Valore restituito
 S_OK se il provider è stato abilitato correttamente. S_FALSE se il provider attualmente è disabilitato. Codice dell'errore nel caso in cui si siano verificati errori. Usare la macro FAILED per verificare la condizione di errore e quindi verificare la presenza di S_OK/S_FALSE.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

## <a name="see-also"></a>Vedere anche
- [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)