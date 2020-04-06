---
title: SccGetCommandOptions (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700825"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions (funzione)SccGetCommandOptions function
Questa funzione richiede all'utente le opzioni avanzate per un determinato comando.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 Icommand

[in] Il comando per il quale sono richieste le opzioni avanzate (vedere [Codice di comando](../extensibility/command-code-enumerator.md) per i valori possibili).

 ppvOpzioni

[in] La struttura dell'opzione `NULL`(può anche essere ).

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo.|
|SCC_I_ADV_SUPPORT|Il plug-in del controllo del codice sorgente supporta le opzioni avanzate per il comando.|
|SCC_I_OPERATIONCANCELED|L'utente ha annullato la finestra di dialogo **Opzioni** del plug-in del controllo del codice sorgente.|
|SCC_E_OPTNOTSUPPORTED|Il plug-in del controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ISCHECKEDOUT|Impossibile eseguire questa operazione su un file attualmente estratto.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 L'IDE chiama questa funzione `ppvOptions` = `NULL` per la prima volta con per determinare se il plug-in controllo del codice sorgente supporta la funzionalità di opzioni avanzate per il comando specificato. Se il plug-in supporta la funzionalità per tale comando, l'IDE chiama nuovamente questa funzione quando l'utente richiede opzioni avanzate (in genere `NULL` implementato come un pulsante **Avanzate** in una finestra di dialogo) e fornisce un puntatore non NULL per `ppvOptions` tale punta a un puntatore. Il plug-in memorizza tutte le opzioni avanzate specificate dall'utente `ppvOptions`in una struttura privata e restituisce un puntatore a tale struttura in . Questa struttura viene quindi passata a tutte le altre funzioni API plug-in `SccGetCommandOptions` del controllo del codice sorgente che devono essere a conoscenza, incluse le chiamate successive alla funzione.

 Un esempio può aiutare a chiarire questa situazione.

 Un utente sceglie il comando **Get** e l'IDE visualizza una finestra di dialogo **Get.** L'IDE `SccGetCommandOptions` chiama `iCommand` la `SCC_COMMAND_GET` funzione `ppvOptions` con `NULL`impostato su e impostato su . Questo viene interpretato dal plug-in controllo del codice sorgente come la domanda, "Avete opzioni avanzate per questo comando?" Se il plug-in restituisce `SCC_I_ADV_SUPPORT`, l'IDE visualizza un pulsante **Avanzate** nella relativa finestra di dialogo **Ottieni** .

 La prima volta che l'utente fa clic sul `SccGetCommandOptions` pulsante **Avanzate,** l'IDE chiama nuovamente la funzione, questa volta con un non-`NULL``ppvOptions` che punta a un `NULL` puntatore. Il plug-in visualizza la propria finestra di dialogo **Opzioni Get** , richiede all'utente informazioni, inserisce tali informazioni nella propria struttura e restituisce un puntatore a tale struttura in `ppvOptions`.

 Se l'utente fa nuovamente clic su **Avanzate** nella `SccGetCommandOptions` stessa finestra `ppvOptions`di dialogo, l'IDE chiama nuovamente la funzione senza modificare , in modo che la struttura venga passata nuovamente al plug-in. Ciò consente al plug-in di reinizializzare la finestra di dialogo in base ai valori impostati in precedenza dall'utente. Il plug-in modifica la struttura sul posto prima della restituzione.

 Infine, quando l'utente fa clic **su OK** nella finestra di dialogo **Get** dell'IDE, l'IDE chiama [sccGet](../extensibility/sccget-function.md), passando la struttura restituita `ppvOptions` che contiene le opzioni avanzate.

> [!NOTE]
> Il `SCC_COMMAND_OPTIONS` comando viene utilizzato quando l'IDE visualizza una finestra di dialogo **Opzioni** che consente all'utente di impostare le preferenze che controllano il funzionamento dell'integrazione. Se il plug-in controllo del codice sorgente desidera fornire la propria finestra di dialogo delle preferenze, è possibile visualizzarlo da un pulsante **Avanzate** nella finestra di dialogo delle preferenze dell'IDE. Il plug-in è l'unico responsabile per ottenere e rendere persistenti queste informazioni; l'IDE non lo utilizza né lo modifica.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di comando](../extensibility/command-code-enumerator.md)
