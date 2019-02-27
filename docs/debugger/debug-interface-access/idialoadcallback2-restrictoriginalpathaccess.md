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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635748"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina se è corretto cercare un file con estensione pdb nella directory di debug originale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Diverso da qualsiasi codice restituito `S_OK` impedisce alla ricerca di un file con estensione pdb nella directory di debug originale. La directory di debug è il percorso del file di simboli compilato nel file eseguibile quando si attiva il debug. Questo percorso non è necessariamente lo stesso come il percorso in cui è presente il file eseguibile.

## <a name="see-also"></a>Vedere anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)