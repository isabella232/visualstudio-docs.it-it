---
title: Restrizioni sulle lunghezze di stringa | Microsoft Docs
description: Informazioni sui limiti sulle lunghezze delle stringhe utilizzate da varie funzioni imposte dall'API del plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5412e930937d029f803f5c6c2b4ddc9d396d9485
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715522"
---
# <a name="restrictions-on-string-lengths"></a>Restrizioni sulle lunghezze di stringa
L'API del plug-in del controllo del codice sorgente limita le lunghezze delle stringhe utilizzate in diverse funzioni.

## <a name="string-length-values"></a>Valori di lunghezza stringa

|Costante|Valore|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La lunghezza non include la terminazione `null` . Altre costanti con suffisso "_SIZE" invece di "_LEN" includono spazio per la terminazione `null` .

|Costante|Valore|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
