---
description: Recupera la stringa di programma utilizzata per calcolare il set di registri prima della chiamata alla funzione corrente.
title: IDiaFrameData::get_program | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e78315ba7fe4f4de3ae94cafe6d8ffa78ef32065
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036415"
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

[out] Restituisce la stringa di programma.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 La stringa di programma è una sequenza di macro che viene interpretata per stabilire il prologo. Ad esempio, una tipica stack frame potrebbe usare la stringa di programma `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Il formato è la notazione di polacco inverso, in cui gli operatori seguono gli operandi. `T0` rappresenta una variabile temporanea nello stack. L'esempio segue questa procedura:

1. Spostare il contenuto del registro `ebp` in `T0` .

2. Aggiungere al valore in per produrre un indirizzo, ottenere il valore da tale indirizzo e `4` `T0` archiviare il valore nel registro `eip` .

3. Ottenere il valore dall'indirizzo archiviato in `T0` e archiviarlo nel registro `ebp` .

4. Aggiungere `8` al valore in e `T0` archiviare tale valore nel registro `esp` .

   Si noti che la stringa di programma è specifica della CPU e della convenzione di chiamata impostata per la funzione rappresentata dal stack frame.

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
