---
title: CV_call_e | Microsoft Docs
description: Ottenere informazioni di riferimento sul tipo CV_call_e di enumerazione, che specifica la convenzione di chiamata per una funzione nell'SDK di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9619796bad01d9aba51026166819e5668743e02d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066677"
---
# <a name="cv_call_e"></a>CV_call_e
Specifica la convenzione di chiamata per una funzione.

> [!NOTE]
> Solo i valori di enumerazione più comuni sono documentati qui. L'enumerazione completa è disponibile nel file di intestazione cvconst.h.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Elementi
CV_CALL_NEAR_C specifica una convenzione di chiamata di funzione usando un push da destra a sinistra. La funzione chiamante cancella lo stack.

CV_CALL_NEAR_FAST specifica una convenzione di chiamata di funzione usando un push da sinistra a destra con registri. La funzione chiamata usa la somma dei byte dei parametri per cancellare lo stack.

CV_CALL_NEAR_STD specifica una convenzione di chiamata di funzione usando una chiamata standard vicina (push da destra a sinistra).

CV_CALL_NEAR_SYS specifica una convenzione di chiamata di funzione usando una chiamata di sistema vicina.

CV_CALL_THISCALL specifica una convenzione di chiamata di funzione usando `this` la chiamata ( `this` puntatore passato nel registro).

CV_CALL_CLRCALL specifica una convenzione di chiamata di funzione usata da Common Language Runtime (CLR) (nota anche come convenzione di chiamata di codice gestito).

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti da una chiamata al [metodo IDiaSymbol::get_callingConvention.](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
