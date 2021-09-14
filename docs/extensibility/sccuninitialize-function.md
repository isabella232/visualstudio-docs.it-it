---
description: Questa funzione pulisce tutte le allocazioni o le connessioni aperte create da una chiamata precedente a SccInitialize in preparazione all'arresto del plug-in del controllo del codice sorgente.
title: Funzione SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 56d2365df1e613976943bd8ba33f6d49a32566f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634507"
---
# <a name="sccuninitialize-function"></a>Funzione SccUninitialize
Questa funzione pulisce tutte le allocazioni o le connessioni aperte create da una chiamata precedente a [SccInitialize](../extensibility/sccinitialize-function.md) in preparazione all'arresto del plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Puntatore alla struttura del contesto del plug-in del controllo del codice sorgente creata in [SccInitialize.](../extensibility/sccinitialize-function.md)

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La pulizia è stata completata.|

## <a name="remarks"></a>Commenti
 Il plug-in del controllo del codice sorgente è responsabile della preparazione per l'arresto e della liberazione della memoria allocata dal plug-in per la struttura del contesto. La funzione viene chiamata una volta per ogni istanza specificata di un plug-in. Una chiamata a [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Non è ancora possibile aprire alcun progetto al momento della chiamata a `SccUninitialize` .

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
