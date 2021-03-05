---
description: Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia di frame di percorso stack.
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
ms.workload:
- multiple
ms.openlocfilehash: 483854d0bea61af1bf8bd1f5338770fcc49b37be
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157812"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia di frame di percorso stack.

## <a name="syntax"></a>Sintassi

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parametri
 `frame`

in Oggetto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) che include lo stato dei registri dei frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. La tabella seguente illustra i possibili valori restituiti per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_DIA_INPROLOG|Non è possibile eseguire un stack frame durante il codice di prologo.|
|E_DIA_SYNTAX|Si è verificato un errore di analisi nel programma frame.|
|E_DIA_FRAME_ACCESS|Impossibile accedere ai registri o alla memoria.|
|E_DIA_VALUE|Errore durante il calcolo di un valore (ad esempio, divisione per zero).|

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato durante il debug per rimuovere lo stack. L'oggetto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) viene implementato dall'applicazione client per ricevere aggiornamenti ai registri e per fornire i metodi usati dal `execute` metodo.

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
