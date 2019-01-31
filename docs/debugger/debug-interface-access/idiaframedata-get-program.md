---
title: Get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f356dec92e1553eba0b8704f6d456b4d1fb4326f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916342"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Recupera la stringa nel programma che viene usata per calcolare il set prima della chiamata alla funzione corrente di registri.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la stringa di programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 La stringa nel programma è una sequenza di macro che viene interpretata per stabilire il prologo. Ad esempio, un frame dello stack tipica potrebbe usare la stringa di programma `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Il formato è una notazione polacca inversa, in cui gli operatori seguono gli operandi. `T0` rappresenta una variabile temporanea nello stack. Questo esempio viene eseguita la procedura seguente:  
  
1. Spostare i contenuti di registro `ebp` a `T0`.  
  
2. Aggiungere `4` al valore nella `T0` per produrre un indirizzo, ottenere il valore da tale indirizzo e archiviare il valore nel registro `eip`.  
  
3. Ottenere il valore rispetto all'indirizzo archiviato in `T0` e il valore memorizzato nel registro `ebp`.  
  
4. Aggiungere `8` al valore nella `T0` e il valore memorizzato nel registro `esp`.  
  
   Si noti che la stringa nel programma è specifica per la CPU e la convenzione di chiamata impostato per la funzione rappresentata dallo stack frame corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)