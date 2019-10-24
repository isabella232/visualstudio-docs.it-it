---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743095"
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

[in] `TRUE` se la directory di debug viene letta da un eseguibile, anziché da un file con estensione dbg.

 `cbData`

in Numero di byte di dati nella directory di debug.

 `data[]`

in Matrice compilata con la directory di debug.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Il codice restituito viene in genere ignorato.

## <a name="remarks"></a>Note
 Il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) richiama questo callback quando trova una directory di debug durante l'elaborazione del file eseguibile.

 Questo metodo elimina la necessità per il client di decompilare il file eseguibile e/o di debug per supportare le informazioni di debug diverse da quelle presenti nel file con estensione pdb. Con questi dati, il client è in grado di riconoscere il tipo di informazioni di debug disponibili e se risiede nel file eseguibile o nel file con estensione dbg.

 La maggior parte dei client non necessita di questo callback perché il metodo `IDiaDataSource::loadDataForExe` apre in modo trasparente i file con estensione PDB e DBG quando necessario per gestire i simboli.

## <a name="see-also"></a>Vedere anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)