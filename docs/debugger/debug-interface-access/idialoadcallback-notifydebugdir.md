---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: e5844cc235d604e8433940920eb9244044732d54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855648"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Chiamato quando viene trovata una directory di debug nel file con estensione exe.

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

[in] `TRUE` Se la directory di debug viene letta da un eseguibile, anziché da un file con estensione dbg.

 `cbData`

in Numero di byte di dati nella directory di debug.

 `data[]`

in Matrice compilata con la directory di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Il codice restituito viene in genere ignorato.

## <a name="remarks"></a>Commenti
 Il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) richiama questo callback quando trova una directory di debug durante l'elaborazione del file eseguibile.

 Questo metodo elimina la necessità per il client di decompilare il file eseguibile e/o di debug per supportare le informazioni di debug diverse da quelle presenti nel file con estensione pdb. Con questi dati, il client è in grado di riconoscere il tipo di informazioni di debug disponibili e se risiede nel file eseguibile o nel file con estensione dbg.

 La maggior parte dei client non richiede questo callback perché il `IDiaDataSource::loadDataForExe` metodo apre in modo trasparente i file con estensione PDB e DBG quando necessario per gestire i simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)