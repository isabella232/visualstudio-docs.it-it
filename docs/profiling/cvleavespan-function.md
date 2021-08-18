---
title: Funzione CvLeaveSpan | Microsoft Docs
description: Vedere le informazioni di riferimento per la funzione CvLeaveSpan (libreria C) dell'SDK del visualizzatore di concorrenza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b5e2e7e275128a46a8f2792cddbbc0c2e6b326c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136169"
---
# <a name="cvleavespan-function"></a>Funzione CvLeaveSpan
Contrassegna la fine della sezione.

## <a name="syntax"></a>Sintassi

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Parametri
 `pSpan` Oggetto span restituito dalla chiamata precedente a CvEnterSpan*. Non può essere NULL.

## <a name="return-value"></a>Valore restituito
 S_OK quando il messaggio è stato scritto correttamente. Codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sulla libreria C++](../profiling/cpp-library-reference.md)