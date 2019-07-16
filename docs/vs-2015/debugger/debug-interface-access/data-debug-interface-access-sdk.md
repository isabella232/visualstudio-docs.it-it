---
title: Dati (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a69e1cddec945cd797d91a92d28ba46221a20d10
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197653"
---
# <a name="data-debug-interface-access-sdk"></a>Dati (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tutte le variabili, ad esempio parametri, variabili locali, le variabili globali e i membri della classe sono identificate da `SymTagData` simboli. Valori costanti (`LocIsConstant`) inoltre vengono identificati con questo tipo.  
  
## <a name="properties"></a>Properties  
 Nella tabella seguente vengono illustrate le proprietà che sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|DESCRIZIONE|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Se un campo, quindi uno dei valori del [enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte relativa all'offset della posizione; Per informazioni dettagliate, vedere la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte di sezione di percorso. Per informazioni dettagliate, vedere la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` Se l'indirizzo di tali dati viene fatto riferimento da un altro simbolo.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Posizione di bit del percorso; Per informazioni dettagliate, vedere la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) (non supportato nella versione 8.0 DIA SDK).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Simbolo per la classe, se si tratta di una struttura, unione o campo della classe.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del simbolo classe padre.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` Se i dati è stati generati dal compilatore.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Se i dati vengono contrassegnati come costante.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Uno dei [enumerazione DataKind](../../debugger/debug-interface-access/datakind.md) valori.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` Se i dati sono parte di un tipo di dati aggregati (solo in DIA SDK 8.0 e versioni successive).|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` Se i dati sono è stata suddivisa in un'aggregazione di più simboli (solo in DIA SDK 8.0 e versioni successive).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Lunghezza del campo di bit; Per informazioni dettagliate, vedere la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo di compilando, funzione o del blocco di inclusione.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Uno dei tipi di percorso consentiti; Per informazioni dettagliate, vedere [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della variabile.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset dal contenuto del Registro; Per informazioni dettagliate, vedere la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Registrare l'indicatore di posizione; Per informazioni dettagliate, vedere la [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa dei dati all'interno del blocco.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Ottiene il numero di slot di dati.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagData` (uno dei [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Il token di metadati che rappresentano i dati.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Simbolo per il tipo della variabile.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID del simbolo di tipo della variabile.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se i dati non allineati.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Il valore di dati costanti.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione dei dati all'interno del file eseguibile.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se i dati vengono contrassegnati come volatile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Enumerazione DataKind](../../debugger/debug-interface-access/datakind.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
