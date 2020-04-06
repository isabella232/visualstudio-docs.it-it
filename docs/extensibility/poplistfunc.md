---
title: Proprietà POPLISTFUNC . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702067"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Questo callback viene fornito per il [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene utilizzato dal plug-in controllo del codice `SccPopulateList` sorgente per aggiornare un elenco di file o directory (fornito anche alla funzione).

 Quando un utente sceglie il comando **Get** nell'IDE, l'IDE visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'elenco esatto di tutti i file che l'utente potrebbe ottenere; solo il plug-in ha questo elenco. Se altri utenti hanno aggiunto file al progetto di controllo del codice sorgente, questi file devono essere visualizzati nell'elenco, ma l'IDE non ne è a conoscenza. L'IDE crea un elenco dei file che ritiene che l'utente può ottenere. Prima di visualizzare questo elenco all'utente, chiama il [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` dando il plug-in controllo del codice sorgente la possibilità di aggiungere ed eliminare file dall'elenco.

## <a name="signature"></a>Firma
 Il plug-in del controllo del codice sorgente modifica l'elenco chiamando una funzione implementata dall'IDE con il prototipo seguente:The source control plug-in modifies the list by calling an IDE-implemented function with the following prototype:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData `pvCallerData` Il parametro passato dal chiamante (idE) a [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug-in del controllo del codice sorgente non deve presupporre nulla sul contenuto di questo parametro.

 fAddRemove `TRUE`If `lpFileName` è un file che deve essere aggiunto all'elenco dei file. Se `FALSE` `lpFileName` , è un file che deve essere eliminato dall'elenco dei file.

 nStatus Status `lpFileName` di (una `SCC_STATUS` combinazione dei bit; vedere [File Status Code](../extensibility/file-status-code-enumerator.md) per i dettagli).

 lpFileName Percorso completo della directory del nome file da aggiungere o eliminare dall'elenco.

## <a name="return-value"></a>Valore restituito

|valore|Descrizione|
|-----------|-----------------|
|`TRUE`|Il plug-in può continuare a chiamare questa funzione.|
|`FALSE`|Si è verificato un problema sul lato IDE (ad esempio una situazione di memoria insufficiente). Il plug-in deve interrompere il funzionamento.|

## <a name="remarks"></a>Osservazioni
 Per ogni file che il plug-in del controllo del codice sorgente desidera aggiungere o `lpFileName`eliminare dall'elenco dei file, chiama questa funzione, passando il file . Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un vecchio file da eliminare. Il `nStatus` parametro fornisce lo stato del file. Quando il plug-in SCC ha terminato l'aggiunta e l'eliminazione di file, restituisce dalla chiamata [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Il `SCC_CAP_POPULATELIST` bit di funzionalità è necessario per Visual Studio.The capability bit is required for Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Callback functions implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Codice di stato del file](../extensibility/file-status-code-enumerator.md)
