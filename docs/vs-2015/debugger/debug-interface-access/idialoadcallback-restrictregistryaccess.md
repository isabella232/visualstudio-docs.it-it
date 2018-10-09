---
title: Restrictregistryaccess | Microsoft Docs
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
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e609c73bd0ce8ddc5756936b274fdab89c46e0aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528731"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Restrictregistryaccess](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-restrictregistryaccess).  
  
Determina se query del Registro di sistema possono essere utilizzate per individuare i percorsi di ricerca simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT RestrictRegistryAccess();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Diverso da qualsiasi codice restituito `S_OK` impedisce l'esecuzione di query il Registro di sistema per i percorsi di ricerca simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)


