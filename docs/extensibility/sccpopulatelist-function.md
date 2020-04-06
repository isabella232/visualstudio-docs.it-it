---
title: SccPopulateList (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700536"
---
# <a name="sccpopulatelist-function"></a>Funzione SccPopulateList
Questa funzione aggiorna un elenco di file per un comando di controllo del codice sorgente specifico e fornisce lo stato del controllo del codice sorgente su tutti i file specificato.

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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 nComando

[in] Il comando del controllo del codice sorgente `lpFileNames` che verrà applicato a tutti i file nella matrice (vedere [Codice di comando](../extensibility/command-code-enumerator.md) per un elenco di comandi possibili).

 nFile

[in] Numero di file `lpFileNames` nella matrice.

 LpNomidi File

[in] Matrice di nomi di file noti all'IDE.

 pfnPop

[in] La funzione di callback IDE da chiamare per aggiungere e rimuovere file (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per i dettagli).

 pvCallerData (informazioni in fibra con i dati)

[in] Valore che deve essere passato invariato alla funzione di callback.

 lpStatus (Stato

[in, out] Matrice per il plug-in del controllo del codice sorgente per restituire i flag di stato per ogni file.

 fOpzioni

[in] Flag di comando (vedere la sezione "Flag PopOla" di [Bitflags utilizzati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per informazioni dettagliate).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Questa funzione esamina l'elenco dei file per il suo stato corrente. Utilizza la `pfnPopulate` funzione di callback per notificare al chiamante `nCommand`quando un file non corrisponde ai criteri per l'oggetto . Ad esempio, se `SCC_COMMAND_CHECKIN` il comando è e un file nell'elenco non è estratto, il callback viene utilizzato per informare il chiamante. In alcuni casi, il plug-in controllo del codice sorgente può trovare altri file che potrebbero far parte del comando e aggiungerli. Ciò consente, ad esempio, un utente di Visual Basic per estrarre un file bmp utilizzato dal proprio progetto ma non viene visualizzato nel file di progetto di Visual Basic. Un utente sceglie il comando **Get** nell'IDE. L'IDE visualizzerà un elenco di tutti i file che ritiene che `SccPopulateList` l'utente può ottenere, ma prima che venga visualizzato l'elenco, la funzione viene chiamata per assicurarsi che l'elenco da visualizzare è aggiornato.

## <a name="example"></a>Esempio
 L'IDE crea un elenco di file che pensa che l'utente può ottenere. Prima di visualizzare questo elenco, chiama la `SccPopulateList` funzione, dando al plug-in del controllo del codice sorgente la possibilità di aggiungere ed eliminare file dall'elenco. Il plug-in modifica l'elenco chiamando la funzione di callback specificata (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per ulteriori dettagli).

 Il plug-in continua `pfnPopulate` a chiamare la funzione, che aggiunge ed elimina i `SccPopulateList` file, fino a quando non viene terminata e quindi restituita dalla funzione. L'IDE può quindi visualizzare il relativo elenco. La `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. Il plug-in riempie lo stato di tutti questi file oltre a fare uso della funzione di callback.

> [!NOTE]
> Un plug-in del controllo del codice sorgente ha sempre la possibilità di restituire immediatamente da questa funzione, lasciando l'elenco così com'è. Se un plug-in implementa questa funzione, può `SCC_CAP_POPULATELIST` indicarlo impostando il flag di bit capability nella prima chiamata a [SccInitialize](../extensibility/sccinitialize-function.md). Per impostazione predefinita, il plug-in deve sempre presupporre che tutti gli elementi passati siano file. Tuttavia, se l'IDE imposta il `SCC_PL_DIR` flag nel `fOptions` parametro, tutti gli elementi passati devono essere considerati directory. Il plug-in deve aggiungere tutti i file che appartengono alle directory. L'IDE non passerà mai una combinazione di file e directory.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [Codice di comando](../extensibility/command-code-enumerator.md)
