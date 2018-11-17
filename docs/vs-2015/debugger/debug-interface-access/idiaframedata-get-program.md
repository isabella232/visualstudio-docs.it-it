---
title: Get_program | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a393b4768de11e34e14126da6979a185513d4ac0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800848"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la stringa nel programma che viene usata per calcolare il set prima della chiamata alla funzione corrente di registri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la stringa di programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 La stringa nel programma è una sequenza di macro che viene interpretata per stabilire il prologo. Ad esempio, un frame dello stack tipica potrebbe usare la stringa di programma `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Il formato è una notazione polacca inversa, in cui gli operatori seguono gli operandi. `T0` rappresenta una variabile temporanea nello stack. Questo esempio viene eseguita la procedura seguente:  
  
1. Spostare i contenuti di registro `ebp` a `T0`.  
  
2. Aggiungere `4` al valore nella `T0` per produrre un indirizzo, ottenere il valore da tale indirizzo e archiviare il valore nel registro `eip`.  
  
3. Ottenere il valore rispetto all'indirizzo archiviato in `T0` e il valore memorizzato nel registro `ebp`.  
  
4. Aggiungere `8` al valore nella `T0` e il valore memorizzato nel registro `esp`.  
  
   Si noti che la stringa nel programma è specifica per la CPU e la convenzione di chiamata impostato per la funzione rappresentata dallo stack frame corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



