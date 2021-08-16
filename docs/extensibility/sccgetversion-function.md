---
description: Questa funzione ottiene il numero di versione dell'API plug-in del controllo del codice sorgente supportata dal plug-in di controllo del codice sorgente.
title: Funzione SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2dd1501e4d9341241b0c07d67571d362ff0fe1dd0bffc489be8cf5c35b4ecd77
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447753"
---
# <a name="sccgetversion-function"></a>Funzione SccGetVersion
Questa funzione ottiene il numero di versione dell'API plug-in del controllo del codice sorgente supportata dal plug-in di controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 Tipo `LONG` di dati che contiene il numero di versione dell'API plug-in del controllo del codice sorgente supportata:

|WORD|Descrizione|
|----------|-----------------|
|HIWORD|Versione principale|
|LOWORD|Versione secondaria|

## <a name="remarks"></a>Commenti
 Ad esempio, se un plug-in del controllo del codice sorgente supporta la versione 1.3 dell'API plug-in del controllo del codice sorgente, questa funzione restituirà 0x0103.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
