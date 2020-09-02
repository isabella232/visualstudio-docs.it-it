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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150087"
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
 in Specifica l'indirizzo virtuale dei dati da ottenere.  
  
 `cbData`  
 in Dimensioni dei dati in byte da ottenere.  
  
 `pcbData`  
 out Restituisce le dimensioni effettive dei dati in byte ottenuti.  
  
 `pbData`  
 [in, out] Buffer compilato con i dati richiesti. Non può essere `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non è presente pData per l'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 PDATA (la sezione denominata ". pData") di un modulo contiene informazioni sulla gestione delle eccezioni per le funzioni.  
  
 Il chiamante sa la quantità di dati da restituire, in modo che il chiamante non debba richiedere la quantità di dati disponibili. Pertanto, è accettabile che un'implementazione di questo metodo restituisca un errore se il `pbData` parametro è `NULL` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
