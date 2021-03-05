---
description: Questa funzione ottiene il numero di versione dell'API del plug-in del controllo del codice sorgente supportata dal plug-in del controllo del codice sorgente.
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a71d3374ffd65e0e7b9a7b2e654885d84e370a9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220599"
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

## <a name="remarks"></a>Commenti
 Se, ad esempio, un plug-in del controllo del codice sorgente supporta la versione 1,3 dell'API del plug-in del controllo del codice sorgente, la funzione restituirà 0x0103.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
