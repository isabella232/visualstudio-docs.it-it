---
title: Funzione SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2deb30b606de686269e095fffe369a7d56adb453
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836930"
---
# <a name="sccpopulatelist-function"></a>Funzione SccPopulateList
Questa funzione aggiorna un elenco di file per un particolare comando del controllo del codice sorgente e fornisce lo stato del controllo del codice sorgente in tutti i file specificati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>Parametri
 pvContext

in Struttura del contesto del plug-in del controllo del codice sorgente.

 nCommand

in Comando del controllo del codice sorgente che verrà applicato a tutti i file nella `lpFileNames` matrice (vedere il [codice di comando](../extensibility/command-code-enumerator.md) per un elenco di comandi possibili).

 nFile

in Numero di file nella `lpFileNames` matrice.

 lpFileNames

in Matrice di nomi di file noti all'IDE.

 pfnPopulate

in Funzione di callback IDE da chiamare per aggiungere e rimuovere file. per informazioni dettagliate, vedere [POPLISTFUNC](../extensibility/poplistfunc.md) .

 pvCallerData

in Valore che deve essere passato senza modifiche alla funzione di callback.

 lpStatus

[in, out] Matrice per il plug-in del controllo del codice sorgente per restituire i flag di stato per ogni file.

 fOptions

in Flag di comando (vedere la sezione "flag di popolamento" di [flag usata da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per informazioni dettagliate).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione esamina l'elenco dei file per lo stato corrente. Usa la `pfnPopulate` funzione di callback per notificare al chiamante quando un file non corrisponde ai criteri per l'oggetto `nCommand` . Se, ad esempio, il comando è `SCC_COMMAND_CHECKIN` e un file nell'elenco non è estratto, il callback viene usato per informare il chiamante. Occasionalmente, il plug-in del controllo del codice sorgente potrebbe trovare altri file che potrebbero far parte del comando e aggiungerli. Questo consente, ad esempio, a un utente Visual Basic di estrarre un file con estensione bmp utilizzato dal suo progetto ma non viene visualizzato nel file di progetto Visual Basic. Un utente sceglie il comando **Get** nell'IDE. Nell'IDE verrà visualizzato un elenco di tutti i file che ritiene che l'utente possa ottenere, ma prima che venga visualizzato l'elenco, viene `SccPopulateList` chiamata la funzione per assicurarsi che l'elenco da visualizzare sia aggiornato.

## <a name="example"></a>Esempio
 L'IDE compila un elenco di file che ritiene che l'utente possa ottenere. Prima di visualizzare questo elenco, chiama la `SccPopulateList` funzione, assegnando al plug-in del controllo del codice sorgente la possibilità di aggiungere ed eliminare file dall'elenco. Il plug-in modifica l'elenco chiamando la funzione di callback specificata. per ulteriori informazioni, vedere [POPLISTFUNC](../extensibility/poplistfunc.md) .

 Il plug-in continua a chiamare la `pfnPopulate` funzione, che aggiunge ed Elimina i file, fino a quando non viene completata e quindi restituisce dalla `SccPopulateList` funzione. L'IDE può quindi visualizzare l'elenco. La `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. Il plug-in compila lo stato di tutti questi file oltre a utilizzare la funzione di callback.

> [!NOTE]
> Un plug-in del controllo del codice sorgente ha sempre la possibilità di restituire semplicemente immediatamente da questa funzione, lasciando l'elenco così com'è. Se un plug-in implementa questa funzione, può indicare questo problema impostando la `SCC_CAP_POPULATELIST` funzionalità flag nella prima chiamata a [SccInitialize](../extensibility/sccinitialize-function.md). Per impostazione predefinita, il plug-in deve sempre presupporre che tutti gli elementi passati siano file. Tuttavia, se l'IDE imposta il `SCC_PL_DIR` flag nel `fOptions` parametro, tutti gli elementi passati devono essere considerati directory. Il plug-in deve aggiungere tutti i file che appartengono alle directory. L'IDE non passerà mai a una combinazione di file e directory.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [Codice di comando](../extensibility/command-code-enumerator.md)
