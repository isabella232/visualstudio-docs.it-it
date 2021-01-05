---
title: Personalizzata (Debug Interface Access SDK) | Microsoft Docs
description: Trovare informazioni di riferimento sui tipi di simboli personalizzati (identificati con il tag SymTagCustom) in Visual Studio Debug Interface Access SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4bec65f766eee8bdf2c4ca34a2a801f26b7d69c
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728734"
---
# <a name="custom-debug-interface-access-sdk"></a>Custom (Debug Interface Access SDK)
Alcuni compilatori introducono simboli non identificati da uno dei tipi di simboli lessicali standard. Questi simboli sono identificati da un `SymTagCustom` tag.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Matrice di dati associati al simbolo.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCustom` uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .|

## <a name="see-also"></a>Vedi anche
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)