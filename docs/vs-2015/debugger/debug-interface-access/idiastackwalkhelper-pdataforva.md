---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954249"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è presente alcun PDATA per l'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 PDATA (della sezione denominata "pdata") di un modulo contiene informazioni sulla gestione delle eccezioni per le funzioni.  
  
 Il chiamante conosca la quantità di dati deve essere restituita in modo che il chiamante non ha necessità di porre per quantità di dati è disponibile. Pertanto, è accettabile per l'implementazione di questo metodo per restituire un errore se il `pbData` parametro è `NULL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
