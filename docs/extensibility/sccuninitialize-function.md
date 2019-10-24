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
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720126"
---
# <a name="sccuninitialize-function"></a>Funzione SccUninitialize
Questa funzione pulisce tutte le allocazioni o le connessioni aperte create da una precedente chiamata a [SccInitialize](../extensibility/sccinitialize-function.md) in preparazione per arrestare il plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametri
 pvContext

in Puntatore alla struttura del contesto del plug-in del controllo del codice sorgente creato in [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|La pulizia è stata completata correttamente.|

## <a name="remarks"></a>Note
 Il plug-in del controllo del codice sorgente è responsabile della preparazione per l'arresto e della liberazione della memoria allocata dal plug-in per la struttura del contesto. La funzione viene chiamata una volta per ogni istanza specifica di un plug-in. Una chiamata a [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Al momento della chiamata a `SccUninitialize` non è ancora possibile aprire alcun progetto.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)