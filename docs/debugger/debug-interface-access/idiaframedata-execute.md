---
description: Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia dello stack walk frame.
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6774cd500d4282acaebefe3e2dc1f2edee8f55ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629897"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia dello stack walk frame.

## <a name="syntax"></a>Sintassi

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parametri
 `frame`

[in] Oggetto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) che contiene lo stato dei registri frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati i possibili valori restituiti per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_DIA_INPROLOG|Impossibile eseguire un stack frame nel codice del prologo.|
|E_DIA_SYNTAX|Errore di analisi rilevato nel programma frame.|
|E_DIA_FRAME_ACCESS|Impossibile accedere ai registri o alla memoria.|
|E_DIA_VALUE|Errore nel calcolo di un valore (ad esempio, divisione per zero).|

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato durante il debug per rimuovere lo stack. [L'oggetto IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) viene implementato dall'applicazione client per ricevere aggiornamenti ai registri e fornire i metodi usati dal `execute` metodo .

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
