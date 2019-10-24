---
title: Funzione SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721473"
---
# <a name="sccgetversion-function"></a>Funzione SccGetVersion
Questa funzione ottiene il numero di versione dell'API del plug-in del controllo del codice sorgente supportata dal plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametri
 Nessuna.

## <a name="return-value"></a>Valore restituito
 Un `LONG` tipo di dati che contiene il numero di versione dell'API del plug-in del controllo del codice sorgente supportato:

|WORD|Descrizione|
|----------|-----------------|
|HIWORD|Versione principale|
|LOWORD|Versione secondaria|

## <a name="remarks"></a>Note
 Se, ad esempio, un plug-in del controllo del codice sorgente supporta la versione 1,3 dell'API del plug-in del controllo del codice sorgente, la funzione restituirà 0x0103.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)