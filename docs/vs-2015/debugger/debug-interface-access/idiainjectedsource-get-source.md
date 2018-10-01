---
title: Get_source | Microsoft Docs
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
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a608da39e0d1c77cb149bd3cfda49506ecab893
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519453"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_source](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiainjectedsource-get-source).  
  
Recupera i byte del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Il numero di byte che rappresenta le dimensioni del buffer di dati.  
  
 `pcbData`  
 [out] Restituisce il numero di byte che rappresenta i byte. Se `data` viene `NULL`, quindi `pcbData` è il numero totale di byte di dati disponibili.  
  
 `data[]`  
 [out] Un buffer che deve essere compilato con i byte di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



