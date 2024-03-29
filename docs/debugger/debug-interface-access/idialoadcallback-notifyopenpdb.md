---
description: Chiamato quando viene aperto un file PDB candidato.
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0a3642fa6a3082c03c8b582895d7f423fdc10573
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629621"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Chiamato quando viene aperto un file PDB candidato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Parametri
 `pdbPath`

[in] Percorso completo del file con estensione pdb.

 `resultCode`

[in] Codice che indica l'esito positivo ( `S_OK` ) o l'esito negativo del caricamento applicato a questo file.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Il codice restituito viene in genere ignorato.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
