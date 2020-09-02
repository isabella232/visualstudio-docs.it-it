---
title: Funzione SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700671"
---
# <a name="sccgetversion-function"></a>Funzione SccGetVersion
Questa funzione ottiene il numero di versione dell'API del plug-in del controllo del codice sorgente supportata dal plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 `LONG`Tipo di dati che contiene il numero di versione dell'API del plug-in del controllo del codice sorgente supportato:

|WORD|Descrizione|
|----------|-----------------|
|HIWORD|Versione principale|
|LOWORD|Versione secondaria|

## <a name="remarks"></a>Osservazioni
 Se, ad esempio, un plug-in del controllo del codice sorgente supporta la versione 1,3 dell'API del plug-in del controllo del codice sorgente, la funzione restituirà 0x0103.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
