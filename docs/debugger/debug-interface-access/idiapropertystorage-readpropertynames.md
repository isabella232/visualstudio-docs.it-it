---
description: Recupera i nomi di stringa corrispondenti per gli identificatori di proprietà specificati.
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: cbb6d511a6be9ed408b076162a3d00d22705075a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148143"
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

in Numero di ID di proprietà in `rgpropid` .

 `rgpropid`

in Matrice di ID di proprietà per cui ottenere i nomi ( `PROPID` è definito in Wtypes. h come `ULONG` ).

 `rglpwstrName`

[in, out] Matrice di nomi di proprietà per gli ID di proprietà specificati. La matrice deve essere pre-allocata per contenere il numero richiesto di nomi di proprietà e deve essere in grado di contenere almeno `cpropid``BSTR` stringhe.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 I nomi di proprietà restituiti devono essere liberati (chiamando la `SysFreeString` funzione) quando non sono più necessari.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
