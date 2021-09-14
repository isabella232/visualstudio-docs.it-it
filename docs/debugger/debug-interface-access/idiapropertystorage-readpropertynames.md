---
description: Recupera i nomi di stringa corrispondenti per gli identificatori di proprietà specificati.
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c49a688fe1ecf9892ec5943934749694e8a839b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629525"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera i nomi di stringa corrispondenti per gli identificatori di proprietà specificati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parametri
 `cpropid`

[in] Numero di ID di proprietà in `rgpropid` .

 `rgpropid`

[in] Matrice di ID di proprietà per cui ottenere i nomi ( `PROPID` è definito in WTypes.h come `ULONG` ).

 `rglpwstrName`

[in, out] Matrice di nomi di proprietà per gli ID di proprietà specificati. La matrice deve essere preallocato per contenere il numero richiesto di nomi di proprietà e deve essere in grado di contenere almeno `cpropid``BSTR` stringhe.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, `S_OK` restituisce ; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 I nomi delle proprietà restituite devono essere liberati (chiamando la `SysFreeString` funzione ) quando non sono più necessari.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
