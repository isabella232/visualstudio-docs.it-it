---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26539d4217682b4d5357f13e9f9368c81297da78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839745"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina se è corretto cercare un file con estensione pdb nella directory di debug originale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Diverso da qualsiasi codice restituito `S_OK` impedisce alla ricerca di un file con estensione pdb nella directory di debug originale. La directory di debug è il percorso del file di simboli compilato nel file eseguibile quando si attiva il debug. Questo percorso non è necessariamente lo stesso come il percorso in cui è presente il file eseguibile.

## <a name="see-also"></a>Vedere anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)