---
title: Notifydebugdir | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4496a7941de29f4ef500a135559dcd746036f6d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533134"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Notifydebugdir](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-notifydebugdir).  
  
Chiamato quando è stata trovata una directory di debug nel file .exe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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



