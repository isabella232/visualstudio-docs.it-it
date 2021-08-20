---
title: PopLISTFUNC | Microsoft Docs
description: Informazioni sulla funzione di callback POPLISTFUNC, usata dal plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dbed07b0ae1e12e6b449e9fccf30e1a2ec27293b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158515"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Questo callback viene fornito a [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene usato dal plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory (fornito anche alla `SccPopulateList` funzione ).

 Quando un utente sceglie il **comando Get nell'IDE,** l'IDE visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'elenco esatto di tutti i file che l'utente potrebbe ottenere; solo il plug-in ha questo elenco. Se altri utenti hanno aggiunto file al progetto di controllo del codice sorgente, questi file dovrebbero essere visualizzati nell'elenco, ma l'IDE non li conosce. L'IDE compila un elenco dei file che l'utente può ottenere. Prima di visualizzare questo elenco all'utente, chiama [SccPopulateList,](../extensibility/sccpopulatelist-function.md) offrendo al plug-in del controllo del codice sorgente la possibilità di aggiungere ed eliminare file `,` dall'elenco.

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
 pvCallerData Parametro `pvCallerData` passato dal chiamante (IDE) a [SccPopulateList.](../extensibility/sccpopulatelist-function.md) Il plug-in del controllo del codice sorgente non deve presupporre nulla sul contenuto di questo parametro.

 fAddRemove Se `TRUE` , è un file che deve essere aggiunto `lpFileName` all'elenco di file. Se `FALSE` , è un file che deve essere eliminato `lpFileName` dall'elenco di file.

 nStatus Status di `lpFileName` (una combinazione dei bit. Per `SCC_STATUS` informazioni dettagliate, vedere [Codice di stato](../extensibility/file-status-code-enumerator.md) del file).

 lpFileName Percorso completo della directory del nome file da aggiungere o eliminare dall'elenco.

## <a name="return-value"></a>Valore restituito

|Valore|Descrizione|
|-----------|-----------------|
|`TRUE`|Il plug-in può continuare a chiamare questa funzione.|
|`FALSE`|Si è verificato un problema sul lato IDE, ad esempio una situazione di memoria insufficiente. Il plug-in deve arrestare l'operazione.|

## <a name="remarks"></a>Commenti
 Per ogni file che il plug-in del controllo del codice sorgente vuole aggiungere o eliminare dall'elenco di file, chiama questa funzione, passando `lpFileName` . Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un file precedente da eliminare. Il `nStatus` parametro indica lo stato del file. Quando il plug-in SCC ha terminato l'aggiunta e l'eliminazione di file, viene restituito dalla [chiamata SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Il `SCC_CAP_POPULATELIST` bit di funzionalità è necessario per Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Codice di stato del file](../extensibility/file-status-code-enumerator.md)
