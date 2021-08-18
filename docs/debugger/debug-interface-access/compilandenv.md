---
title: CompilandEnv | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo CompilandEnv (SymTagCompilandEnv) nell'SDK Visual Studio di accesso all'interfaccia di debug.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 445df8efc8663bff91c37f7fc6f34c12c99b402d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036735"
---
# <a name="compilandenv"></a>CompilandEnv
Il compilatore può includere variabili di ambiente aggiuntive con simboli. Esiste un simbolo `SymTagCompilandEnv` per ognuna di queste variabili.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per il compilando padre.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della variabile.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandEnv` (uno dei [valori dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Contenuto con valori stringa della variabile ( `VT_BSTR` ).|

## <a name="see-also"></a>Vedi anche
- [Compilando](../../debugger/debug-interface-access/compiland.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)