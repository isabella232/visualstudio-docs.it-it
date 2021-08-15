---
description: Determina se le query del Registro di sistema possono essere usate per individuare i percorsi di ricerca dei simboli.
title: IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4a61ab05230b1c2573e38b3de60b2c8d57bd08b1984dfa87f8853ad0ff13471d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345020"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Determina se le query del Registro di sistema possono essere usate per individuare i percorsi di ricerca dei simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Qualsiasi codice restituito diverso da impedisce `S_OK` l'esecuzione di query nel Registro di sistema per i percorsi di ricerca dei simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
