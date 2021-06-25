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
ms.workload:
- vssdk
ms.openlocfilehash: c865931ed52601761f0bd519bf360d584d49ec04
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904113"
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

 nFiles

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di file selezionati.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

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
 Questa funzione consente al chiamante di accedere alla gamma completa di funzionalità del sistema di controllo del codice sorgente tramite uno strumento di amministrazione esterno. Se il sistema di controllo del codice sorgente non ha un'interfaccia utente, il plug-in di controllo del codice sorgente può implementare un'interfaccia per eseguire le funzioni di amministrazione necessarie.

 Questa funzione viene chiamata con un conteggio e una matrice di nomi di file per i file attualmente selezionati. Se lo strumento di amministrazione lo supporta, l'elenco di file può essere usato per preselezionare i file nell'interfaccia di amministrazione. In caso contrario, l'elenco può essere ignorato.

 Questa funzione viene in genere richiamata quando l'utente seleziona **Avvia \<Source Control Server>** dal menu **Controllo del** codice  ->  **sorgente** file. Questa **opzione del** menu Di avvio può essere sempre disabilitata o persino nascosta impostando una voce del Registro di sistema. Per [informazioni dettagliate, vedere Procedura: Installare un plug-in del controllo](../extensibility/internals/how-to-install-a-source-control-plug-in.md) del codice sorgente. Questa funzione viene chiamata solo se [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il bit di funzionalità . Per informazioni dettagliate su questo e altri bit di funzionalità, vedere Flag `SCC_CAP_RUNSCC` [](../extensibility/capability-flags.md) di funzionalità.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Procedura: Installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
