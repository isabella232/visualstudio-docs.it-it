---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1db5d9b876beecc68345075a624e0368d8115999
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928829"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Recupera o parte di un nome non decorato per C++ decorati nome (collegamento).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `undecoratedOptions`  
 [in] Specifica una combinazione di flag che controllano i valori restituiti. Vedere la sezione Osservazioni per i valori specifici e le operazioni eseguite.  
  
 `pRetVal`  
 [out] Restituisce che il nome non decorato per C++ nome decorato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Osservazioni  
 Il `undecorateOptions` può essere una combinazione dei flag seguenti.  
  
> [!NOTE]
>  I nomi di flag non sono definiti in DIA SDK, pertanto è necessario aggiungere le dichiarazioni nel codice o usare i valori non elaborati.  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Abilita undecoration completo.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Rimuove gli iniziali di caratteri di sottolineatura da parole chiave estese Microsoft.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Disabilita l'espansione delle parole chiave estese Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Disabilita l'espansione del tipo restituito per la dichiarazione primario.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Disabilita l'espansione del modello di dichiarazione.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Disabilita l'espansione dell'identificatore di lingua di dichiarazione.|  
|UNDNAME_RESERVED1|0x0020|RISERVATO.|  
|UNDNAME_RESERVED2|0x0040|RISERVATO.|  
|UNDNAME_NO_THISTYPE|0x0060|Disabilita tutti i modificatori nel `this` tipo.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Disabilita l'espansione di identificatori di accesso per i membri.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Disabilita l'espansione di "throw-firme" per le funzioni e i puntatori a funzioni.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Disabilita l'espansione della `static` o `virtual` membri.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Disabilita l'espansione del modello di Microsoft per tipo definito dall'utente restituisce.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates nomi decorati 32 bit.|  
|UNDNAME_NAME_ONLY|0x1000|Ottiene solo il nome per la dichiarazione di primario. Restituisce semplicemente [ambito::] nome.  Espande i parametri di modello.|  
|UNDNAME_TYPE_ONLY|0x2000|L'input è solo un tipo di codifica; compone un dichiaratore astratto.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|I parametri di modello reali sono disponibili.|  
|UNDNAME_NO_ECSU|0x8000|Elimina enum, classe o struct/unione.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Elimina controllo per i caratteri di identificatore valido.|  
|UNDNAME_NO_PTR64|0x20000|Non include ptr64 nell'output.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)