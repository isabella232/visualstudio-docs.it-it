---
title: Limitazioni sulle lunghezze di stringa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab797f76ec6f6118fe4f86a410dbfcfe1e61aa04
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334181"
---
# <a name="restrictions-on-string-lengths"></a>Limitazioni sulle lunghezze di stringa
L'API dei plug-in del controllo origine limita la lunghezza delle stringhe usate nelle varie funzioni.

## <a name="string-length-values"></a>Valori di lunghezza stringa

|Costante|Value|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La lunghezza non include la terminazione `null`. Altre costanti con suffisso "dimen_sione" anziché "_LEN" include lo spazio per la terminazione `null`.

|Costante|Value|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Vedere anche
- [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)