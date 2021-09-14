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
ms.openlocfilehash: 48e87a968eea1ad35796a495d76584488bdac332
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629639"
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

 Questo metodo elimina la necessità per il client di eseguire il reverse engineer del file eseguibile e/o del file di debug per supportare informazioni di debug diverse da quelle presenti nel file con estensione pdb. Con questi dati, il client può riconoscere il tipo di informazioni di debug disponibili e se si trova nel file eseguibile o nel file con estensione dbg.

 La maggior parte dei client non avrà bisogno di questo callback perché il metodo apre in modo trasparente i file con estensione pdb e dbg quando necessario `IDiaDataSource::loadDataForExe` per la gestione dei simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
