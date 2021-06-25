---
description: Questa funzione aggiorna un elenco di file per un determinato comando di controllo del codice sorgente e fornisce lo stato del controllo del codice sorgente per tutti i file specificati.
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
ms.workload:
- vssdk
ms.openlocfilehash: b386c576b48e14b6118f62d451c42ac20f048b45
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902345"
---
# <a name="sccpopulatelist-function"></a>Funzione SccPopulateList
Questa funzione aggiorna un elenco di file per un determinato comando di controllo del codice sorgente e fornisce lo stato del controllo del codice sorgente per tutti i file specificati.

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

 nComando

[in] Comando del controllo del codice sorgente che verrà applicato a tutti i file nella `lpFileNames` matrice (vedere [Codice di comando](../extensibility/command-code-enumerator.md) per un elenco dei comandi possibili).

 nFile

[in] Numero di file nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di file noti all'IDE.

 pfnPopulate

[in] Funzione di callback IDE da chiamare per aggiungere e rimuovere file (per informazioni dettagliate, [vedere POPLISTFUNC).](../extensibility/poplistfunc.md)

 pvCallerData

[in] Valore da passare invariato alla funzione di callback.

 lpStatus

[in, out] Matrice per il plug-in di controllo del codice sorgente per restituire i flag di stato per ogni file.

 fOpzioni

[in] Flag di comando (per informazioni dettagliate, vedere la sezione "Flag PopulateList" di [Bitflags Usati da comandi](../extensibility/bitflags-used-by-specific-commands.md) specifici).

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione esamina l'elenco di file per il relativo stato corrente. Usa la funzione di callback per inviare una notifica al chiamante quando `pfnPopulate` un file non corrisponde ai criteri per `nCommand` . Ad esempio, se il comando è e un file nell'elenco non è estratto, il callback viene usato `SCC_COMMAND_CHECKIN` per informare il chiamante. In alcuni casi, il plug-in del controllo del codice sorgente può trovare altri file che potrebbero far parte del comando e aggiungerli. Ciò consente, ad esempio, a un utente Visual Basic di estrarre un file .bmp usato dal proprio progetto, ma non viene visualizzato nel file di Visual Basic progetto. Un utente sceglie il **comando Get** nell'IDE. L'IDE visualizza un elenco di tutti i file che l'utente può ottenere, ma prima che venga visualizzato l'elenco, viene chiamata la funzione per assicurarsi che l'elenco da visualizzare sia `SccPopulateList` aggiornato.

## <a name="example"></a>Esempio
 L'IDE compila un elenco di file che l'utente può ottenere. Prima di visualizzare questo elenco, chiama la funzione , offrendo al plug-in del controllo del codice sorgente la possibilità di aggiungere ed `SccPopulateList` eliminare file dall'elenco. Il plug-in modifica l'elenco chiamando la funzione di callback specificata (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per altri dettagli).

 Il plug-in continua a chiamare la funzione , che aggiunge ed elimina i file, fino a quando non viene completata e `pfnPopulate` quindi viene restituita dalla `SccPopulateList` funzione. L'IDE può quindi visualizzare il relativo elenco. La `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. Il plug-in compila lo stato di tutti questi file, oltre a usare la funzione di callback.

> [!NOTE]
> Un plug-in del controllo del codice sorgente ha sempre la possibilità di tornare immediatamente da questa funzione, lasciando l'elenco così come è. Se un plug-in implementa questa funzione, può indicarlo impostando il flag di bit della funzionalità nella prima chiamata `SCC_CAP_POPULATELIST` a [SccInitialize](../extensibility/sccinitialize-function.md). Per impostazione predefinita, il plug-in deve sempre presupporre che tutti gli elementi passati siano file. Tuttavia, se l'IDE imposta il flag nel parametro , tutti gli elementi passati devono `SCC_PL_DIR` `fOptions` essere considerati directory. Il plug-in deve aggiungere tutti i file che appartengono alle directory. L'IDE non passerà mai una combinazione di file e directory.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
- [Codice di comando](../extensibility/command-code-enumerator.md)
