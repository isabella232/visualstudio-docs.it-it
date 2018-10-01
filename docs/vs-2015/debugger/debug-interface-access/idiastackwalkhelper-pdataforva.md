---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
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
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6949fba8216bbc1747c9bd1f963a0f1c06bff4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528523"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDiaStackWalkHelper::pdataForVA](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-pdataforva).  
  
Restituisce il blocco di dati PDATA associato all'indirizzo virtuale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `va`  
 [in] Specifica l'indirizzo virtuale dei dati da ottenere.  
  
 `cbData`  
 [in] Le dimensioni dei dati in byte da ottenere.  
  
 `pcbData`  
 [out] Restituisce le dimensioni effettive dei dati in byte che è stato ottenuto.  
  
 `pbData`  
 [in, out] Un buffer che viene compilato con i dati richiesti. Non può essere `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è presente alcun PDATA per l'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 PDATA (della sezione denominata "pdata") di un modulo contiene informazioni sulla gestione delle eccezioni per le funzioni.  
  
 Il chiamante conosca la quantità di dati deve essere restituita in modo che il chiamante non ha necessità di porre per quantità di dati è disponibile. Pertanto, è accettabile per l'implementazione di questo metodo per restituire un errore se il `pbData` parametro è `NULL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)



