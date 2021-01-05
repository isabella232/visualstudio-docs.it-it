---
title: CompilandEnv | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo CompilandEnv (SymTagCompilandEnv) in Visual Studio Debug Interface Access SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandEnv symbol
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e71dd47c75b7cfcef9580119563a7c8f2227268a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728762"
---
# <a name="compilandenv"></a>CompilandEnv
Il compilatore può includere variabili di ambiente aggiuntive con simboli. `SymTagCompilandEnv`Per ognuna di queste variabili è presente un simbolo.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per il modulo padre.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della variabile.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandEnv` uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Contenuto con valori di stringa della variabile ( `VT_BSTR` ).|

## <a name="see-also"></a>Vedi anche
- [Compilando](../../debugger/debug-interface-access/compiland.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)