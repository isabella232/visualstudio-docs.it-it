---
title: Exe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe2930e0947bf0fa69408dc81c19d058d6cdd870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164267"
---
# <a name="exe"></a>Exe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exe è l'unico simbolo senza un elemento padre lessicale o di classe, perché rappresenta l'ambito globale del file con estensione exe o dll. È presente un solo simbolo con il `SymTagExe` tag per ogni file. Il metodo [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) restituisce il simbolo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Tempo di questo eseguibile.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` del file eseguibile.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` Se il file di simboli associato a questo eseguibile contiene tipi C (solo in DIA SDK versione 8.0 o successiva).|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` Se i simboli privati sono stati rimossi dal file di simboli associato a questo eseguibile (solo in DIA SDK versione 8.0 o successiva).|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Valore che indica la CPU di destinazione (uno dei valori di [enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome del file con estensione exe.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Firma del file eseguibile.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Percorso completo del file con estensione PDB o DBG del file con estensione exe.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagExe` uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
