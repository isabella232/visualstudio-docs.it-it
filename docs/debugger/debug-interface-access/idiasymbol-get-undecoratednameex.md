---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3d34c362a64107bff94e271c01b57d45d09cf8d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862549"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Recupera parte o tutto un nome non decorato per un nome in C++ decorato (collegamento).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Parametri
 `undecoratedOptions`

in Specifica una combinazione di flag che controllano ciò che viene restituito. Vedere la sezione Osservazioni per i valori specifici e le relative operazioni.

 `pRetVal`

out Restituisce il nome non decorato per un nome decorato C++.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 `undecorateOptions`Può essere una combinazione dei flag seguenti.

> [!NOTE]
> I nomi dei flag non sono definiti nella DIA SDK, quindi è necessario aggiungere le dichiarazioni al codice o usare i valori non elaborati.

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Abilita la dedecorazione completa.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Rimuove i caratteri di sottolineatura iniziali dalle parole chiave estese Microsoft.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Disabilita l'espansione delle parole chiave estese Microsoft.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Disabilita l'espansione del tipo restituito per la dichiarazione primaria.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Disabilita l'espansione del modello di dichiarazione.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Disabilita l'espansione dell'identificatore del linguaggio di dichiarazione.|
|UNDNAME_RESERVED1|0x0020|RISERVATO.|
|UNDNAME_RESERVED2|0x0040|RISERVATO.|
|UNDNAME_NO_THISTYPE|0x0060|Disabilita tutti i modificatori del `this` tipo.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Disabilita l'espansione degli identificatori di accesso per i membri.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Disabilita l'espansione di "Throw-Signatures" per le funzioni e i puntatori alle funzioni.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Disabilita l'espansione dei `static` membri o `virtual` .|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Disabilita l'espansione del modello Microsoft per i ritorni UDT.|
|UNDNAME_32_BIT_DECODE|0x0800|Non decora i nomi decorati a 32 bit.|
|UNDNAME_NAME_ONLY|0x1000|Ottiene solo il nome della dichiarazione primaria; restituisce solo il nome [Scope::].  Espande i parametri del modello.|
|UNDNAME_TYPE_ONLY|0x2000|L'input è semplicemente una codifica di tipo; compone un dichiaratore astratto.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Sono disponibili i parametri del modello reale.|
|UNDNAME_NO_ECSU|0x8000|Disattiva enum/class/struct/union.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Disattiva il controllo della presenza di caratteri identificatore validi.|
|UNDNAME_NO_PTR64|0x20000|Non include ptr64 nell'output.|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)