---
title: CompilandDetails | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo CompilandDetails (SymTagCompilandDetails) nell'SDK Visual Studio di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f2817e37d088f8d125b18b4e39051966b690c683
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630725"
---
# <a name="compilanddetails"></a>CompilandDetails
Le informazioni di compilazione sono suddivise tra simboli con `SymTagCompiland` un tag (dettagli minimi) `SymTagCompilandDetails` e un tag (dettagli elevati). `SymTagCompilandDetails` fornisce numerose informazioni sul compilando che non è disponibile con un `SymTagCompiland` simbolo.

## <a name="properties"></a>Proprietà
 La tabella seguente illustra le proprietà valide per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numero di build back-end del compilatore.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numero di versione principale back-end del compilatore.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numero di versione secondaria back-end del compilatore.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nome del compilatore che ha prodotto questo compilando (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` se Modifica e continuazione è stato abilitato durante la compilazione.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numero di build front-end del compilatore.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numero di versione principale front-end del compilatore.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numero di versione secondaria front-end del compilatore.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` se questo compilando contiene informazioni di debug (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` se questo compilando contiene codice gestito (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` se il compilatore è stato compilato con l'opzione del compilatore [/GS (Controllo](/cpp/build/reference/gs-buffer-security-check) di sicurezza del buffer) (solo in DIA SDK V8.0 o versione successiva).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` se il compilatore è stato convertito dal Common Intermediate Language (CIL) al codice nativo.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` se i tipi definiti dall'utente (UDT) sono stati allineati ad alcuni limiti di memoria specificati (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` se compiland è stato compilato con l'opzione del compilatore [/hotpatch (Crea](/cpp/build/reference/hotpatch-create-hotpatchable-image) immagine con hotpatch) (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` se compiland è stato compilato con l'opzione del compilatore [/LTCG (generazione](/cpp/build/reference/ltcg-link-time-code-generation) del codice in fase di collegamento) (solo in DIA SDK V8.0 o versione successiva).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE se compiland è un modulo MSIL (Microsoft Intermediate Language) (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Linguaggio del codice sorgente.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per il compilazione.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Piattaforma in cui è stato compilato il compilando (uno dei CV_CPU_TYPE_e [di enumerazione).](../../debugger/debug-interface-access/cv-cpu-type-e.md)|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandDetails` (uno dei valori [dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|

## <a name="remarks"></a>Commenti
 I compilatori hanno spesso un formato noto come compilatore a due passi. In alcune versioni del compilatore ogni passaggio viene gestito da un programma separato. Questi sono noti rispettivamente come compilatori front-end e back-end, quindi le proprietà dei simboli per i numeri di versione back-end e front-end.

## <a name="see-also"></a>Vedi anche
- [Compilando](../../debugger/debug-interface-access/compiland.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)