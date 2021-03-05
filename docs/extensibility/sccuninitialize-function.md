---
description: Questa funzione pulisce tutte le allocazioni o le connessioni aperte create da una precedente chiamata a SccInitialize in preparazione per arrestare il plug-in del controllo del codice sorgente.
title: Funzione SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 187451aba5151c95d8947bd4f5a1419894cc65e7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221327"
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

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La pulizia è stata completata correttamente.|

## <a name="remarks"></a>Commenti
 Il plug-in del controllo del codice sorgente è responsabile della preparazione per l'arresto e della liberazione della memoria allocata dal plug-in per la struttura del contesto. La funzione viene chiamata una volta per ogni istanza specifica di un plug-in. Una chiamata a [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Nessun progetto può ancora essere aperto al momento della chiamata a `SccUninitialize` .

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
