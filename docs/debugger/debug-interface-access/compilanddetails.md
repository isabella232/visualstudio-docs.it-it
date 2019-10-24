---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745410"
---
# <a name="compilanddetails"></a>CompilandDetails
Le informazioni di modulo vengono suddivise tra simboli con tag `SymTagCompiland` (dettagli Bassi) e un tag di `SymTagCompilandDetails` (dettaglio elevato). `SymTagCompilandDetails` richiede il caricamento di simboli aggiuntivi. Fornisce tuttavia una grande quantità di informazioni su modulo che non sono disponibili con un simbolo `SymTagCompiland`.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.

|proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numero di build del back-end del compilatore.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numero di versione principale del back-end del compilatore.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numero di versione secondario del back-end del compilatore.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nome del compilatore che ha generato questo modulo (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` se la funzionalità modifica e continuazione era abilitata durante la compilazione.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numero di build front-end del compilatore.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numero di versione principale front-end del compilatore.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numero di versione secondario front-end del compilatore.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` se il modulo dispone di informazioni di debug (solo in DIA SDK V 8.0 o versione successiva).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` se il modulo contiene codice gestito (solo in DIA SDK v 8.0 o versione successiva).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` se il modulo è stato compilato con l'opzione del compilatore [/GS (controllo di sicurezza del buffer)](/cpp/build/reference/gs-buffer-security-check) (solo in DIA SDK v 8.0 o versione successiva).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` se modulo è stato convertito dal codice Common Intermediate Language (CIL) al codice nativo.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` se i tipi definiti dall'utente (UDT) sono stati allineati a un limite di memoria specificato (solo in DIA SDK V 8.0 o versione successiva).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` se modulo è stato compilato con l'opzione del compilatore [/hotpatch (Create Hotpatchable Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) (solo in DIA SDK v 8.0 o versione successiva).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` se modulo è stato compilato con l'opzione del compilatore [/LTCG (generazione di codice in fase di collegamento)](/cpp/build/reference/ltcg-link-time-code-generation) (solo in DIA SDK v 8.0 o versione successiva).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE se modulo è un modulo MSIL (Microsoft Intermediate Language) (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Linguaggio del codice sorgente.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per modulo.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Piattaforma in cui è stato compilato il modulo (uno dei valori di [enumerazione di CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandDetails` (uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="remarks"></a>Note
 I compilatori spesso sono in un formato noto come compilatore a due passaggi. in alcune versioni del compilatore ogni passaggio viene gestito da un programma separato. Questi sono noti rispettivamente come compilatori front-end e back-end, quindi le proprietà dei simboli per i numeri di versione back-end e front-end.

## <a name="see-also"></a>Vedere anche
- [Compilando](../../debugger/debug-interface-access/compiland.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)