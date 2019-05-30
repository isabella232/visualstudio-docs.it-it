---
title: Funzione SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71e34352150143c7db207ed31ea6e879f97ca18
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338499"
---
# <a name="sccuninitialize-function"></a>Funzione SccUninitialize
Questa funzione Elimina tutte le allocazioni o connessioni aperte create da una precedente chiamata ai [SccInitialize](../extensibility/sccinitialize-function.md) in preparazione per il plug-in del controllo del codice sorgente in corso l'arresto.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Il puntatore alla struttura di contesto del plug-in controllo di origine creato nel [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|La pulizia completata.|

## <a name="remarks"></a>Note
 Il plug-in del controllo del codice sorgente è responsabile della preparazione per essere arrestata e per liberare memoria in cui è allocato il plug-in per la struttura scelta. La funzione viene chiamata una volta per ogni istanza specifica di un plug-in. Una chiamata per il [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Nessun progetto può essere ancora aperto al momento della chiamata a `SccUninitialize`.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)