---
description: Determina se il provider è stato abilitato da una sessione.
title: Metodo marker_series::is_enabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b36a76b8d404606b97672a78d8fb467fc998bbf4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626921"
---
# <a name="marker_seriesis_enabled-method"></a>Metodo marker_series::is_enabled
Determina se il provider è stato abilitato da una sessione.

## <a name="syntax"></a>Sintassi

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parametri
 `_Importance` Livello di importanza.

 `_Category` Categoria.

## <a name="return-value"></a>Valore restituito

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedi anche
- [marker_series classe](../profiling/marker-series-class.md)
