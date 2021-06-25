---
description: Questa funzione richiede all'utente le opzioni avanzate per un determinato comando.
title: Funzione SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7972d874668649b8bb86adc15008880c5fc4152e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903931"
---
# <a name="sccgetcommandoptions-function"></a>Funzione SccGetCommandOptions
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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 Icommand

[in] Comando per il quale sono richieste opzioni avanzate (vedere [Codice di comando](../extensibility/command-code-enumerator.md) per i valori possibili).

 ppvOptions

[in] Struttura dell'opzione (può anche essere `NULL` ).

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata.|
|SCC_I_ADV_SUPPORT|Il plug-in di controllo del codice sorgente supporta le opzioni avanzate per il comando .|
|SCC_I_OPERATIONCANCELED|L'utente ha annullato la finestra di dialogo Opzioni del plug-in **del** controllo del codice sorgente.|
|SCC_E_OPTNOTSUPPORTED|Il plug-in del controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ISCHECKEDOUT|Impossibile eseguire questa operazione su un file attualmente estratto.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione per la prima volta con per determinare se il plug-in del controllo del codice sorgente supporta la funzionalità `ppvOptions` = `NULL` opzioni avanzate per il comando specificato. Se il plug-in supporta la funzionalità per tale comando, l'IDE chiama di nuovo  questa funzione quando l'utente richiede opzioni avanzate (in genere implementate come pulsante Avanzate in una finestra di dialogo) e fornisce un puntatore non NULL per che punta a un `ppvOptions` puntatore. `NULL` Il plug-in archivia tutte le opzioni avanzate specificate dall'utente in una struttura privata e restituisce un puntatore a tale struttura in `ppvOptions` . Questa struttura viene quindi passata a tutte le altre funzioni API plug-in del controllo del codice sorgente che devono essere a loro volta a conoscere, incluse le chiamate successive alla `SccGetCommandOptions` funzione.

 Un esempio può essere utile per chiarire questa situazione.

 Un utente sceglie il **comando Get e** l'IDE visualizza una finestra **di** dialogo Get. L'IDE chiama `SccGetCommandOptions` la funzione con impostato su e impostato su `iCommand` `SCC_COMMAND_GET` `ppvOptions` `NULL` . Questo viene interpretato dal plug-in del controllo del codice sorgente come la domanda "Sono disponibili opzioni avanzate per questo comando?" Se il plug-in restituisce `SCC_I_ADV_SUPPORT` , l'IDE visualizza un **pulsante** Avanzate nella finestra **di dialogo** Ottieni.

 La prima volta che  l'utente fa clic sul pulsante Avanzate, l'IDE chiama nuovamente la funzione , questa volta con un `SccGetCommandOptions` non che punta a un `NULL``ppvOptions` `NULL` puntatore. Il plug-in visualizza  la propria finestra di dialogo Ottieni opzioni, richiede informazioni all'utente, inserisce le informazioni nella propria struttura e restituisce un puntatore a tale struttura in `ppvOptions` .

 Se l'utente **fa** di nuovo clic su Avanzate nella stessa finestra di dialogo, l'IDE chiama di nuovo la funzione senza modificare , in modo che la struttura viene passata nuovamente `SccGetCommandOptions` al `ppvOptions` plug-in. Ciò consente al plug-in di reinizializzare la finestra di dialogo con i valori impostati in precedenza dall'utente. Il plug-in modifica la struttura sul posto prima di restituire .

 Infine, quando l'utente fa clic  su **OK** nella finestra di dialogo Get dell'IDE, l'IDE chiama [SccGet](../extensibility/sccget-function.md), passando la struttura restituita in che contiene `ppvOptions` le opzioni avanzate.

> [!NOTE]
> Il comando viene usato quando l'IDE visualizza una finestra di dialogo Opzioni che consente all'utente di impostare preferenze `SCC_COMMAND_OPTIONS` che controllano il funzionamento dell'integrazione.  Se il plug-in del controllo del codice sorgente vuole specificare la propria finestra di dialogo delle preferenze, può visualizzarlo da un **pulsante** Avanzate nella finestra di dialogo preferenze dell'IDE. Il plug-in è esclusivamente responsabile del recupero e della persistenza di queste informazioni. l'IDE non lo usa né lo modifica.

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di comando](../extensibility/command-code-enumerator.md)
