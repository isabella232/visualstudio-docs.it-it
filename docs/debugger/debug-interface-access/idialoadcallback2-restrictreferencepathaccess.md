---
title: IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39186cfc8fb3f83986692ebf7c608b895aae7ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839732"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Determina se alla ricerca di un file con estensione PDB è consentita nel percorso in cui si trova il file .exe.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Diverso da qualsiasi codice restituito `S_OK` per impedire alla ricerca di un file con estensione pdb nel percorso in cui si trova il file .exe.

## <a name="see-also"></a>Vedere anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)