---
title: Funzione CvLeaveSpan | Microsoft Docs
description: Vedere le informazioni di riferimento per la funzione SDK del Visualizzatore di concorrenza CvLeaveSpan (libreria C).
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1dcd98a8233f8080d03650c3989805ee9ec7289
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686584"
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
- [Riferimenti alla libreria C++](../profiling/cpp-library-reference.md)