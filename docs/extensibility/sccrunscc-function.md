---
title: Funzione SccRunScc . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700404"
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 nFile

[in] Numero di file `lpFileNames` specificati nella matrice.

 LpNomidi File

[in] Matrice di nomi di file selezionati.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Lo strumento di amministrazione del controllo del codice sorgente è stato richiamato correttamente.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema di controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa.|
|SCC_E_CONNECTIONFAILURE|Impossibile connettersi al sistema di controllo del codice sorgente.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è nel controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Questa funzione consente al chiamante di accedere all'intera gamma di funzionalità del sistema di controllo del codice sorgente tramite uno strumento di amministrazione esterno. Se il sistema di controllo del codice sorgente non dispone di alcuna interfaccia utente, il plug-in del controllo del codice sorgente può implementare un'interfaccia per eseguire le funzioni di amministrazione necessarie.

 Questa funzione viene chiamata con un conteggio e una matrice di nomi di file per i file attualmente selezionati. Se lo strumento di amministrazione lo supporta, l'elenco dei file può essere utilizzato per preselezionare i file nell'interfaccia di amministrazione; in caso contrario, l'elenco può essere ignorato.

 Questa funzione viene in genere richiamata quando l'utente seleziona il **>Avvia \<** server controllo del codice sorgente dal menu**Controllo del codice sorgente** **file** -> . Questa opzione del menu **di avvio** può essere sempre disabilitata o persino nascosta impostando una voce del Registro di sistema. Per informazioni dettagliate, vedere [Procedura: installare un plug-in del controllo](../extensibility/internals/how-to-install-a-source-control-plug-in.md) del codice sorgente. Questa funzione viene chiamata solo se `SCC_CAP_RUNSCC` [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il bit di funzionalità (vedere Flag di [capability](../extensibility/capability-flags.md) per informazioni dettagliate su questo e altri bit di funzionalità).

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Procedura: Installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
