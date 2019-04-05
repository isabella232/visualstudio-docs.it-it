---
title: CompilandDetails | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c91fbd8a4fc3775272e578df43025bd7052c72ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967354"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Informazioni compilando sono suddiviso tra i simboli con un `SymTagCompiland` tag (dettaglio bassa) e un `SymTagCompilandDetails` tag (livello di dettaglio alto). `SymTagCompilandDetails` richiede il caricamento dei simboli aggiuntivi. Tuttavia, fornisce un'ampia gamma di informazioni del modulo che non è disponibile con un `SymTagCompiland` simbolo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà che sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numero di build di back-end del compilatore.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numero di versione principale di back-end del compilatore.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numero di versione secondaria di back-end del compilatore.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nome del compilatore che ha prodotto questo modulo (solo in DIA SDK 8.0 o versione successiva).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Se la compilazione sono stati abilitati modifica e continuazione.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numero di build front-end del compilatore.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numero di versione principale front-end del compilatore.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numero di versione secondaria front-end del compilatore.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Se questo modulo contiene le informazioni di debug (solo in DIA SDK 8.0 o versione successiva).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Se questo modulo contiene codice gestito (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Se il modulo è stato compilato con il [/GS (controllo sicurezza Buffer)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) opzione del compilatore (solo in DIA SDK 8.0 o versione successiva).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Se è stato convertito compilando dal codice Common Intermediate Language (CIL) in codice nativo.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Se i tipi definiti dall'utente (UDT) sono stati allineati a alcuni specificato il limite di memoria (solo in DIA SDK 8.0 o versione successiva).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Se il modulo è stato compilato con il [/hotpatch (Crea immagine con patch a caldo)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) opzione del compilatore (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Se il modulo è stato compilato con il [/LTCG (generazione di codice in fase di collegamento)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) opzione del compilatore (solo in DIA SDK 8.0 o versione successiva).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE se compilando un modulo di Microsoft Intermediate Language (MSIL) (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Linguaggio del codice sorgente.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per il modulo.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Piattaforma in cui è stato compilato il modulo (uno dei [enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) valori).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandDetails` (uno dei [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori).|  
  
## <a name="remarks"></a>Note  
 I compilatori sono spesso in un formato noto come un compilatore in due passaggi. in alcune versioni del compilatore, ogni passaggio viene gestita da un programma separato. Questi sono conosciuti come i compilatori di front-end e back-end, rispettivamente, di conseguenza le proprietà dei simboli per i numeri di versione back-end e front-end.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilando](../../debugger/debug-interface-access/compiland.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
