---
description: Determina se la ricerca di un file con estensione pdb è consentita nel percorso in cui si trova .exe file.
title: IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: eb24cbf84c57b7c7db74a992ad9c19361d4d741fc1594ffa94b83979ec9fbbff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345012"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Determina se la ricerca di un file con estensione pdb è consentita nel percorso in cui si trova .exe file.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Qualsiasi codice restituito diverso da per impedire la ricerca di un file con estensione pdb nel percorso in cui si trova `S_OK` .exe file.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
