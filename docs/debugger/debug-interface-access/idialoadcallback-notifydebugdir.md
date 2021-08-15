---
description: Chiamato quando è stata trovata una directory di debug nel file .exe.
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1d7db4245a96ac77327e8251d1c3df312819a2423b05108e66610022f2c83065
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121326016"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Chiamato quando è stata trovata una directory di debug nel file .exe.

## <a name="syntax"></a>Sintassi

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parametri
 `fExecutable`

[in] `TRUE` se la directory di debug viene letta da un file eseguibile (anziché da un file con estensione dbg).

 `cbData`

[in] Numero di byte di dati nella directory di debug.

 `data[]`

[in] Matrice compilata con la directory di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Il codice restituito viene in genere ignorato.

## <a name="remarks"></a>Commenti
 Il [metodo IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) richiama questo callback quando trova una directory di debug durante l'elaborazione del file eseguibile.

 Questo metodo elimina la necessità che il client inverti il file eseguibile e/o di debug per supportare informazioni di debug diverse da quelle trovate nel file con estensione pdb. Con questi dati, il client può riconoscere il tipo di informazioni di debug disponibili e se si trova nel file eseguibile o nel file con estensione dbg.

 La maggior parte dei client non avrà bisogno di questo callback perché il metodo apre in modo trasparente i file con estensione pdb e dbg quando necessario `IDiaDataSource::loadDataForExe` per la gestione dei simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
