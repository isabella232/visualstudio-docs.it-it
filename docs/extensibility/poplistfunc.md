---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83e54cf1b0e6f15b1a6c5dc0af379a8b88bd77f4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434230"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Questo callback viene fornito per il [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene usato per il plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory (anche fornito al `SccPopulateList` (funzione)).

 Quando un utente sceglie il **ottenere** comando nell'IDE, l'IDE visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'elenco esatto di tutti i file che è possibile che venga visualizzato all'utente; solo il plug-in dispone di questo elenco. Se altri utenti aggiunti file al progetto di controllo del codice sorgente, questi file dovrebbero essere visualizzati nell'elenco, ma l'IDE non saperlo. L'IDE compila un elenco dei file che ritiene che l'utente può ottenere. Prima di visualizzare l'elenco all'utente, chiama il [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` offrendo il plug-in del controllo del codice sorgente possibilità di aggiungere ed eliminare i file dall'elenco.

## <a name="signature"></a>Signature
 Il plug-in del controllo del codice sorgente consente di modificare l'elenco chiamando una funzione dell'IDE implementate con il seguente prototipo:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData il `pvCallerData` parametro passato dal chiamante (IDE) per il [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug-in del controllo del codice sorgente deve presupporre niente sul contenuto di questo parametro.

 fAddRemove se `TRUE`, `lpFileName` è un file che deve essere aggiunti all'elenco dei file. Se `FALSE`, `lpFileName` è un file che deve essere eliminato dall'elenco dei file.

 nStatus lo stato del `lpFileName` (una combinazione del `SCC_STATUS` bits, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md) per informazioni dettagliate).

 percorso completo della directory lpFileName del nome del file per aggiungere o eliminare dall'elenco.

## <a name="return-value"></a>Valore restituito

|Value|Descrizione|
|-----------|-----------------|
|`TRUE`|Il plug-in possono continuare a chiamare questa funzione.|
|`FALSE`|Si è verificato un problema sul lato dell'IDE (ad esempio di situazione di memoria insufficiente). Il plug-in deve arrestare l'operazione.|

## <a name="remarks"></a>Note
 Per ogni file che deve essere il plug-in del controllo del codice sorgente da aggiungere o eliminare dall'elenco dei file, chiama questa funzione, passando il `lpFileName`. Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un vecchio file da eliminare. Il `nStatus` parametro fornisce lo stato del file. Quando il plug-in del controllo del codice sorgente ha terminato l'aggiunta ed eliminazione di file, restituisce il [SccPopulateList](../extensibility/sccpopulatelist-function.md) chiamare.

> [!NOTE]
> Il `SCC_CAP_POPULATELIST` bit funzionalità è necessaria per Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Codice di stato file](../extensibility/file-status-code-enumerator.md)