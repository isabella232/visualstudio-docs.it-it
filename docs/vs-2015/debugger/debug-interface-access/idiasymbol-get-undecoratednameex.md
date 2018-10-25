---
title: Get_undecoratednameex | Microsoft Docs
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
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a57f44f440daacb0cb24cc7e6b89475d9f3ad754
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893663"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o parte di un nome non decorato per C++ decorati nome (collegamento).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
## <a name="remarks"></a>Note  
 Il `undecorateOptions` può essere una combinazione dei flag seguenti.  
  
> [!NOTE]
>  I nomi di flag non sono definiti in DIA SDK, pertanto è necessario aggiungere le dichiarazioni nel codice o usare i valori non elaborati.  
  
|Flag|Valore|Descrizione|  
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
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000.|Elimina controllo per i caratteri di identificatore valido.|  
|UNDNAME_NO_PTR64|0x20000|Non include ptr64 nell'output.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



