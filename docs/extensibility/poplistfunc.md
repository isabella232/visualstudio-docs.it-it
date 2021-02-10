---
title: POPLISTFUNC | Microsoft Docs
description: Informazioni sulla funzione di callback POPLISTFUNC, usata dal plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddf641cf309eb5b5352904da2ac07b64b0886f97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967358"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Questo callback viene fornito a [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene usato dal plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory (forniti anche alla `SccPopulateList` funzione).

 Quando un utente sceglie il comando **Get** nell'IDE, l'IDE Visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'elenco esatto di tutti i file che l'utente potrebbe ottenere; Questo elenco è presente solo per il plug-in. Se altri utenti hanno aggiunto file al progetto di controllo del codice sorgente, questi file devono essere visualizzati nell'elenco, ma l'IDE non li conosce. L'IDE compila un elenco dei file che ritiene che l'utente possa ottenere. Prima che questo elenco venga visualizzato dall'utente, viene chiamato il [SccPopulateList](../extensibility/sccpopulatelist-function.md) che `,` fornisce al plug-in del controllo del codice sorgente la possibilità di aggiungere ed eliminare file dall'elenco.

## <a name="signature"></a>Firma
 Il plug-in del controllo del codice sorgente modifica l'elenco chiamando una funzione implementata dall'IDE con il prototipo seguente:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData il `pvCallerData` parametro passato dal chiamante (l'IDE) a [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug-in del controllo del codice sorgente non deve presupporre nulla sul contenuto di questo parametro.

 fAddRemove se `TRUE` , `lpFileName` è un file che deve essere aggiunto all'elenco dei file. Se `FALSE` , `lpFileName` è un file che deve essere eliminato dall'elenco dei file.

 Stato nStatus di `lpFileName` (combinazione dei bit. `SCC_STATUS` per informazioni dettagliate, vedere il [codice di stato dei file](../extensibility/file-status-code-enumerator.md) ).

 lpFileName percorso completo della directory del nome file da aggiungere o eliminare dall'elenco.

## <a name="return-value"></a>Valore restituito

|Valore|Descrizione|
|-----------|-----------------|
|`TRUE`|Il plug-in può continuare a chiamare questa funzione.|
|`FALSE`|Si è verificato un problema sul lato IDE, ad esempio una situazione di memoria insufficiente. Il plug-in deve arrestare l'operazione.|

## <a name="remarks"></a>Commenti
 Per ogni file che il plug-in del controllo del codice sorgente desidera aggiungere o eliminare dall'elenco di file, chiama questa funzione, passando `lpFileName` . Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un file obsoleto da eliminare. Il `nStatus` parametro restituisce lo stato del file. Al termine dell'aggiunta e dell'eliminazione dei file del plug-in SCC, viene restituito dalla chiamata [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

> [!NOTE]
> Il `SCC_CAP_POPULATELIST` bit di funzionalità è necessario per Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Codice di stato file](../extensibility/file-status-code-enumerator.md)
