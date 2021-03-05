---
description: Inizializza una nuova istanza della classe marker_series.
title: Costruttore marker_series::marker_series | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88d82c78bc6126f6b3d96b77b39c729c4f452a28
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223979"
---
# <a name="marker_seriesmarker_series-constructor"></a>Costruttore marker_series::marker_series
Inizializza una nuova istanza della classe `marker_series`.

## <a name="syntax"></a>Sintassi

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>Parametri
 `_SeriesName` Nome della serie da creare.

 `_ProviderGuid` GUID del provider della serie.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedi anche
- [classe marker_series](../profiling/marker-series-class.md)
