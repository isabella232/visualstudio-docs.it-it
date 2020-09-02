---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 970a188b5d72353dbb3ccf64fd74f3354f1ba888
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151946"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Determina se è corretto cercare un file con estensione PDB nella directory di debug originale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Qualsiasi codice restituito diverso da `S_OK` impedisce la ricerca di un file con estensione PDB nella directory di debug originale. La directory di debug originale è il percorso del file di simboli compilato nell'eseguibile quando il debug è attivato. Questo percorso non corrisponde necessariamente al percorso in cui è presente il file eseguibile.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
