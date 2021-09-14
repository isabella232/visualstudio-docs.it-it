---
description: Determina se è possibile cercare un file con estensione pdb nella directory di debug originale.
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ed1c3cb17a8f1e3e43f0798bce4c18bd0457370d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629580"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina se è possibile cercare un file con estensione pdb nella directory di debug originale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Qualsiasi codice restituito diverso `S_OK` da impedisce la ricerca di un file con estensione pdb nella directory di debug originale. La directory di debug originale è il percorso del file di simboli compilato nel file eseguibile quando il debug è attivato. Questo percorso non corrisponde necessariamente al percorso in cui si trova il file eseguibile.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
