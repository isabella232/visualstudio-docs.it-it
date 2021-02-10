---
title: Funzione SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1f465e6709932cd89794c5c0558d608fadd2a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965200"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions (funzione)
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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 iCommand

in Comando per cui sono richieste le opzioni avanzate. per i valori possibili, vedere il [codice di comando](../extensibility/command-code-enumerator.md) .

 ppvOptions

in La struttura dell'opzione (può anche essere `NULL` ).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo.|
|SCC_I_ADV_SUPPORT|Il plug-in del controllo del codice sorgente supporta le opzioni avanzate per il comando.|
|SCC_I_OPERATIONCANCELED|L'utente ha annullato la finestra di dialogo **Opzioni** del plug-in del controllo del codice sorgente.|
|SCC_E_OPTNOTSUPPORTED|Il plug-in del controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ISCHECKEDOUT|Non è possibile eseguire questa operazione su un file attualmente estratto.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione per la prima volta con `ppvOptions` = `NULL` per determinare se il plug-in del controllo del codice sorgente supporta la funzionalità opzioni avanzate per il comando specificato. Se il plug-in supporta la funzionalità per il comando, l'IDE chiama di nuovo questa funzione quando l'utente richiede opzioni avanzate (in genere implementate come pulsante **Avanzate** in una finestra di dialogo) e fornisce un puntatore non null per `ppvOptions` che punta a un `NULL` puntatore. Il plug-in archivia tutte le opzioni avanzate specificate dall'utente in una struttura privata e restituisce un puntatore a tale struttura in `ppvOptions` . Questa struttura viene quindi passata a tutte le altre funzioni API del plug-in del controllo del codice sorgente che è necessario conoscere, incluse le chiamate successive alla `SccGetCommandOptions` funzione.

 Un esempio può essere utile per chiarire questa situazione.

 Un utente sceglie il comando **Get** e l'IDE Visualizza una finestra di dialogo **Get** . L'IDE chiama la `SccGetCommandOptions` funzione con `iCommand` impostato su `SCC_COMMAND_GET` e `ppvOptions` impostato su `NULL` . Questo comportamento viene interpretato dal plug-in del controllo del codice sorgente come domanda: "sono disponibili opzioni avanzate per questo comando?" Se il plug-in `SCC_I_ADV_SUPPORT` viene restituito, l'IDE Visualizza un pulsante **Avanzate** nella finestra di dialogo **Ottieni** .

 La prima volta che l'utente fa clic sul pulsante **Avanzate** , l'IDE chiama `SccGetCommandOptions` di nuovo la funzione, questa volta con un non- `NULL``ppvOptions` che punta a un `NULL` puntatore. Il plug-in Visualizza la finestra di dialogo **opzioni Get** , chiede all'utente le informazioni, inserisce le informazioni nella relativa struttura e restituisce un puntatore a tale struttura in `ppvOptions` .

 Se l'utente fa nuovamente clic su **Avanzate** nella stessa finestra di dialogo, l'IDE chiama `SccGetCommandOptions` di nuovo la funzione senza modificare `ppvOptions` , in modo che la struttura venga passata di nuovo al plug-in. In questo modo il plug-in consente di reinizializzare la finestra di dialogo sui valori impostati in precedenza dall'utente. Il plug-in modifica la struttura sul posto prima di restituire.

 Infine, quando l'utente fa clic su **OK** nella finestra di dialogo **Get** dell'IDE, l'IDE chiama il [SccGet](../extensibility/sccget-function.md), passando la struttura restituita in `ppvOptions` che contiene le opzioni avanzate.

> [!NOTE]
> Il comando `SCC_COMMAND_OPTIONS` viene usato quando l'IDE Visualizza una finestra di dialogo **Opzioni** che consente all'utente di impostare preferenze che controllano il funzionamento dell'integrazione. Se il plug-in del controllo del codice sorgente desidera fornire la propria finestra di dialogo di preferenze, può visualizzarlo da un pulsante **Avanzate** nella finestra di dialogo Preferenze dell'IDE. Il plug-in è esclusivamente responsabile del recupero e della conservazione delle informazioni. l'IDE non lo utilizza né lo modifica.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice comando](../extensibility/command-code-enumerator.md)
