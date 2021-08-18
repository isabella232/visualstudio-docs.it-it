---
description: Recupera un flag che indica che queste informazioni sulla riga descrivono l'inizio di un'istruzione, anziché un'espressione, nell'origine del programma.
title: IDiaLineNumber::get_statement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1af9fd6462f668e23d2a24d6d7db4939322a30e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066551"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Recupera un flag che indica che queste informazioni sulla riga descrivono l'inizio di un'istruzione, anziché un'espressione, nell'origine del programma.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se le informazioni sulla riga descrivono l'inizio di un'istruzione nell'origine del programma.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Le istruzioni possono estendersi su più righe. Questo metodo indica se il numero di riga associato contrassegna l'inizio di tale istruzione su più righe.

## <a name="see-also"></a>Vedi anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
