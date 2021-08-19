---
description: Questa funzione aggiorna un elenco di file per un comando di controllo del codice sorgente specifico e fornisce lo stato del controllo del codice sorgente per tutti i file specificati.
title: Funzione SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9cf2474f32e1d1cacb1d5a137f42ae30571c6d15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110033"
---
# <a name="sccpopulatelist-function"></a>Funzione SccPopulateList
Questa funzione aggiorna un elenco di file per un comando di controllo del codice sorgente specifico e fornisce lo stato del controllo del codice sorgente per tutti i file specificati.

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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 nCommand

[in] Comando di controllo del codice sorgente che verrà applicato a tutti i file nella `lpFileNames` matrice (vedere [Codice di comando](../extensibility/command-code-enumerator.md) per un elenco dei comandi possibili).

 nFiles

[in] Numero di file nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di file noti all'IDE.

 pfnPopulate

[in] Funzione di callback IDE da chiamare per aggiungere e rimuovere file (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate).

 pvCallerData

[in] Valore che deve essere passato invariato alla funzione di callback.

 lpStatus

[in, out] Matrice per il plug-in del controllo del codice sorgente per restituire i flag di stato per ogni file.

 fOptions

[in] Flag di comando (per informazioni dettagliate, vedere la sezione "Flag PopulateList" in Flag di bit usati [da](../extensibility/bitflags-used-by-specific-commands.md) comandi specifici).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione esamina l'elenco dei file per verificare lo stato corrente. Usa la funzione `pfnPopulate` di callback per notificare al chiamante quando un file non corrisponde ai criteri per `nCommand` . Ad esempio, se il comando è e un file nell'elenco non è estratto, il callback viene usato `SCC_COMMAND_CHECKIN` per informare il chiamante. In alcuni casi, il plug-in del controllo del codice sorgente può trovare altri file che potrebbero far parte del comando e aggiungerli. In questo modo, ad esempio, un utente di Visual Basic può estrarre un file .bmp usato dal proprio progetto, ma non viene visualizzato nel file Visual Basic progetto. Un utente sceglie il **comando Get** nell'IDE. L'IDE visualizza un elenco di tutti i file che l'utente può ottenere, ma prima che venga visualizzato l'elenco, viene chiamata la funzione per assicurarsi che l'elenco da visualizzare sia `SccPopulateList` aggiornato.

## <a name="example"></a>Esempio
 L'IDE compila un elenco di file che l'utente può ottenere. Prima di visualizzare questo elenco, chiama la funzione , offrendo al plug-in del controllo del codice sorgente la possibilità di `SccPopulateList` aggiungere ed eliminare file dall'elenco. Il plug-in modifica l'elenco chiamando la funzione di callback specificata (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per altri dettagli).

 Il plug-in continua a chiamare la funzione , che aggiunge ed elimina i file, fino a quando non viene completata e `pfnPopulate` quindi viene restituito dalla `SccPopulateList` funzione . L'IDE può quindi visualizzare il relativo elenco. La `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. Il plug-in inserisce lo stato di tutti questi file oltre a usare la funzione di callback .

> [!NOTE]
> Un plug-in del controllo del codice sorgente ha sempre la possibilità di tornare immediatamente da questa funzione, lasciando l'elenco così come è. Se un plug-in implementa questa funzione, può indicare questo valore impostando il flag di bit della funzionalità nella prima chiamata `SCC_CAP_POPULATELIST` a [SccInitialize.](../extensibility/sccinitialize-function.md) Per impostazione predefinita, il plug-in deve sempre presupporre che tutti gli elementi passati siano file. Tuttavia, se l'IDE imposta il flag nel parametro , tutti gli elementi `SCC_PL_DIR` passati devono essere considerati `fOptions` directory. Il plug-in deve aggiungere tutti i file che appartengono alle directory. L'IDE non passerà mai una combinazione di file e directory.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [Codice di comando](../extensibility/command-code-enumerator.md)
