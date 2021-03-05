---
description: Recupera la stringa di programma utilizzata per calcolare il set di registri prima della chiamata alla funzione corrente.
title: 'IDiaFrameData:: get_program | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d3e16503d025771b3af34c7f4eee185c2f6aacab
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148493"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Recupera la stringa di programma utilizzata per calcolare il set di registri prima della chiamata alla funzione corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce la stringa di programma.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 La stringa di programma è una sequenza di macro che viene interpretata per poter stabilire il prologo. Ad esempio, una tipica stack frame potrebbe utilizzare la stringa di programma `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Il formato è la notazione polacca inversa, in cui gli operatori seguono gli operandi. `T0` rappresenta una variabile temporanea nello stack. L'esempio segue questa procedura:

1. Spostare il contenuto del registro `ebp` in `T0` .

2. Aggiungere `4` al valore in `T0` per produrre un indirizzo, ottenere il valore da tale indirizzo e archiviare il valore in Register `eip` .

3. Ottenere il valore dall'indirizzo archiviato in `T0` e archiviare il valore in Register `ebp` .

4. Aggiungere `8` al valore in `T0` e archiviare il valore in Register `esp` .

   Si noti che la stringa di programma è specifica della CPU e della convenzione di chiamata impostata per la funzione rappresentata dal stack frame corrente.

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
