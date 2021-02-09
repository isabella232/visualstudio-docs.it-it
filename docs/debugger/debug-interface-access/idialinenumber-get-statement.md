---
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
ms.workload:
- multiple
ms.openlocfilehash: 0baad9c254efad1fff772cfae27828e3597d078b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864733"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Recupera un flag che indica che le informazioni sulla riga descrivono l'inizio di un'istruzione, anziché un'espressione, nell'origine del programma.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se queste informazioni sulla riga descrivono l'inizio di un'istruzione nell'origine del programma.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Le istruzioni possono estendersi su più righe. Questo metodo indica se il numero di riga associato contrassegna l'inizio di tale istruzione a più righe.

## <a name="see-also"></a>Vedi anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)