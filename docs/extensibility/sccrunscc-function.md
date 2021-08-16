---
description: Questa funzione richiama lo strumento di amministrazione del controllo del codice sorgente.
title: Funzione SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 277bfe2aa6c49a8d93307ce93d46b6fff6156f4f9c4fc008f6e5bb8e25212a6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413947"
---
# <a name="sccrunscc-function"></a>Funzione SccRunScc
Questa funzione richiama lo strumento di amministrazione del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFile

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di file selezionati.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Lo strumento di amministrazione del controllo del codice sorgente è stato richiamato correttamente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema di controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione.|
|SCC_E_CONNECTIONFAILURE|Impossibile connettersi al sistema di controllo del codice sorgente.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è in controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione consente al chiamante di accedere all'intera gamma di funzionalità del sistema di controllo del codice sorgente tramite uno strumento di amministrazione esterno. Se il sistema di controllo del codice sorgente non ha un'interfaccia utente, il plug-in di controllo del codice sorgente può implementare un'interfaccia per eseguire le funzioni di amministrazione necessarie.

 Questa funzione viene chiamata con un conteggio e una matrice di nomi di file per i file attualmente selezionati. Se lo strumento di amministrazione lo supporta, l'elenco di file può essere usato per preselezionare i file nell'interfaccia di amministrazione. In caso contrario, l'elenco può essere ignorato.

 Questa funzione viene in genere richiamata quando l'utente seleziona **Avvia \<Source Control Server>** dal menu **Controllo del** codice  ->  **sorgente** file. Questa **opzione del** menu Di avvio può essere sempre disabilitata o persino nascosta impostando una voce del Registro di sistema. Per [informazioni dettagliate, vedere Procedura: Installare un plug-in del controllo](../extensibility/internals/how-to-install-a-source-control-plug-in.md) del codice sorgente. Questa funzione viene chiamata solo se [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il bit di funzionalità (vedere Flag di funzionalità per informazioni dettagliate su questo e `SCC_CAP_RUNSCC` altri bit di [](../extensibility/capability-flags.md) funzionalità).

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Procedura: Installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
