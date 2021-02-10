---
title: Funzione CvCreateMarkerSeries | Microsoft Docs
description: Vedere le informazioni di riferimento per la funzione SDK del Visualizzatore di concorrenza CvCreateMarkerSeries (libreria C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941034"
---
# <a name="cvcreatemarkerseries-function"></a>Funzione CvCreateMarkerSeries
Crea una serie di marcatori per un determinato provider.

## <a name="syntax"></a>Sintassi

```C
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
 `pProvider` Oggetto provider preinizializzato tramite CvInitProvider. Non può essere NULL.

 `pSeriesName` Nome della serie di marcatori. Non può essere NULL, ma le stringhe vuote sono consentite.

 `ppMarkerSeries` Indirizzo di una variabile di output in cui verrà archiviato il contesto della serie di marcatori. Non può essere NULL.

## <a name="return-value"></a>Valore restituito
 S_OK quando la serie di marcatori viene creata correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Vedi anche
- [Riferimenti alla libreria C++](../profiling/cpp-library-reference.md)