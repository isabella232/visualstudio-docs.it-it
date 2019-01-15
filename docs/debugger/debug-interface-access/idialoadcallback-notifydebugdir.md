---
title: Notifydebugdir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fe328d9f77871692f04d13fba533517c3cc12f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958917"
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
 [in] `TRUE` se la directory di debug viene letto da un file eseguibile (anziché un file DBG).  
  
 `cbData`  
 [in] Numero di byte dei dati nella directory di debug.  
  
 `data[]`  
 [in] Matrice che viene compilata con la directory di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Il codice restituito in genere viene ignorato.  
  
## <a name="remarks"></a>Note  
 Il [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo richiama il callback quando viene trovata una directory di debug durante l'elaborazione del file eseguibile.  
  
 Questo metodo rimuove la necessità per il client decodificare il file eseguibile e/o di debug per supportare le informazioni di debug diverso da quello trovato nel file con estensione pdb. Con questi dati, il client in grado di riconoscere il tipo di informazioni di debug disponibili e che si trova all'interno del file eseguibile o il file DBG.  
  
 La maggior parte dei client non sarà necessario questo callback perché le `IDiaDataSource::loadDataForExe` metodo apre in modo trasparente i file con estensione pdb sia DBG quando è necessaria per soddisfare i simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)