---
title: Funzione CvIsEnabled | Microsoft Docs
description: Vedere le informazioni di riferimento per la funzione CvIsEnabled (libreria C) dell'SDK del visualizzatore di concorrenza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4bb2e5bf40c038456853a06b9b43a9ee03d8e051
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084519"
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

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sulla libreria C++](../profiling/cpp-library-reference.md)