---
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700234"
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

## <a name="remarks"></a>Osservazioni
 Il plug-in del controllo del codice sorgente è responsabile della preparazione per l'arresto e della liberazione della memoria allocata dal plug-in per la struttura del contesto. La funzione viene chiamata una volta per ogni istanza specifica di un plug-in. Una chiamata a [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Nessun progetto può ancora essere aperto al momento della chiamata a `SccUninitialize` .

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
