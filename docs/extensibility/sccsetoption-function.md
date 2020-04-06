---
title: SccSetOption (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700315"
---
# <a name="sccsetoption-function"></a>Funzione SccSetOption
Questa funzione imposta le opzioni che controllano il comportamento del plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 nOpzione

[in] Opzione che viene impostata.

 dwVal

[in] Impostazioni per l'opzione.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'opzione è stata impostata correttamente.|
|SCC_I_SHARESUBPROJOK|Restituito se `nOption` `SCC_OPT_SHARESUBPROJ` was e il plug-in del controllo del codice sorgente consente all'IDE di impostare la cartella di destinazione.|
|SCC_E_OPNOTSUPPORTED|L'opzione non è stata impostata e non deve essere invocata.|

## <a name="remarks"></a>Osservazioni
 L'IDE chiama questa funzione per controllare il comportamento del plug-in del controllo del codice sorgente. Il primo `nOption`parametro, , indica il valore che `dwVal`viene impostato, mentre il secondo, , indica cosa fare con tale valore. Il plug-in archivia queste `pvContext``,` informazioni associate a un modo l'IDE deve chiamare questa funzione dopo aver chiamato il [SccInitialize](../extensibility/sccinitialize-function.md) (ma non necessariamente dopo ogni chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Riepilogo delle opzioni e dei relativi valori:

|`nOption`|`dwValue`|Descrizione|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Abilita/disabilita l'accodamento degli eventi in background.|
|`SCC_OPT_USERDATA`|Valore arbitrario|Specifica un valore utente da passare alla funzione di callback [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se l'IDE supporta attualmente l'annullamento di un'operazione.|
|`SCC_OPT_NAMECHANGEPFN`|Puntatore alla funzione di callback [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Imposta un puntatore a una funzione di callback di modifica del nome.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se l'IDE consente l'estrazione manuale dei file (tramite l'interfaccia utente del controllo del codice sorgente) o se devono essere estratti solo tramite il plug-in del controllo del codice sorgente.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Se il plug-in del controllo del codice sorgente consente all'IDE di specificare la cartella del progetto locale, il plug-in restituisce `SCC_I_SHARESUBPROJOK`.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Se `nOption` `SCC_OPT_EVENTQUEUE`è , l'IDE disabilita (o riabilita) l'elaborazione in background. Ad esempio, durante una compilazione, l'IDE potrebbe indicare al plug-in del controllo del codice sorgente per interrompere l'elaborazione inmodale di qualsiasi tipo. Dopo la compilazione, sarebbe riattivare l'elaborazione in background per mantenere aggiornata la coda degli eventi del plug-in. Corrispondente al `SCC_OPT_EVENTQUEUE` valore `nOption`di , sono `dwVal`disponibili due `SCC_OPT_EQ_ENABLE` valori `SCC_OPT_EQ_DISABLE`possibili per , ovvero e .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Se il `nOption` valore `SCC_OPT_HASCANCELMODE`di è , l'IDE consente agli utenti di annullare le operazioni long. L'impostazione su `dwVal` `SCC_OPT_HCM_NO` (impostazione predefinita) indica che l'IDE non dispone di alcuna modalità di annullamento. Il plug-in del controllo del codice sorgente deve offrire il proprio pulsante Annulla se desidera che l'utente sia in grado di annullare. `SCC_OPT_HCM_YES`indica che l'IDE offre la possibilità di annullare un'operazione, pertanto il plug-in SCC non è necessario visualizzare il proprio pulsante Annulla. Se l'IDE è `dwVal` impostato su `SCC_MSG_STATUS` `DOCANCEL` `lpTextOutProc` `SCC_OPT_HCM_YES`, viene preparato per rispondere e i messaggi inviati alla funzione di callback (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Se l'IDE non imposta questa variabile, il plug-in non deve inviare questi due messaggi.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Se nOption è `SCC_OPT_NAMECHANGEPFN`impostato su e sia il plug-in del controllo del codice sorgente che l'IDE lo consentono, il plug-in può effettivamente rinominare o spostare un file durante un'operazione del controllo del codice sorgente. L'oggetto `dwVal` verrà impostato su un puntatore a funzione di tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante un'operazione di controllo del codice sorgente, il plug-in può chiamare questa funzione, passando tre parametri. Questi sono il nome precedente (con percorso completo) di un file, il nuovo nome (con percorso completo) di tale file e un puntatore a informazioni che ha rilevanza per l'IDE. L'IDE invia l'ultimo `SccSetOption` `nOption` puntatore `SCC_OPT_USERDATA`chiamando `dwVal` con impostato su , con puntamento ai dati. Il supporto per questa funzione è facoltativo. Un plug-in VSSCI che utilizza questa funzionalità deve `NULL`inizializzare il puntatore a funzione e le variabili dei dati utente in , e non deve chiamare una funzione di ridenominazione a meno che non ne sia stata data una. Dovrebbe inoltre essere pronta a detenere il valore che gli è `SccSetOption`stato dato o a modificarlo in risposta a una nuova chiamata a . Ciò non avverrà nel mezzo di un'operazione di comando del controllo del codice sorgente, ma può verificarsi tra i comandi.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Se nOption è `SCC_OPT_SCCCHECKOUTONLY`impostato su , l'IDE indica che i file nel progetto attualmente aperto non devono mai essere estratti manualmente tramite l'interfaccia utente del sistema di controllo del codice sorgente. Al contrario, i file devono essere estratti solo tramite il plug-in del controllo del codice sorgente in controllo IDE. Se `dwValue` è `SCC_OPT_SCO_NO`impostato su , significa che i file devono essere trattati normalmente dal plug-in e possono essere estratti tramite l'interfaccia utente del controllo del codice sorgente. Se `dwValue` è `SCC_OPT_SCO_YES`impostato su , solo il plug-in può estrarre i file e l'interfaccia utente del sistema di controllo del codice sorgente non deve essere richiamata. Questo è per le situazioni in cui l'IDE potrebbe avere "pseudo-file" che hanno senso per estrarre solo attraverso l'IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Se`nOption` è `SCC_OPT_SHARESUBPROJ`impostato su , l'IDE sta verificando se il plug-in del controllo del codice sorgente può utilizzare una cartella locale specificata quando si aggiungono file dal controllo del codice sorgente. In questo `dwVal` caso, il valore del parametro non è rilevante. Se il plug-in consente all'IDE di specificare la cartella di destinazione locale in cui i file verranno aggiunti `SCC_I_SHARESUBPROJOK` dal `SccSetOption` controllo del codice sorgente quando viene chiamato [SccAddFromScc,](../extensibility/sccaddfromscc-function.md) il plug-in deve restituire quando viene chiamata la funzione. L'IDE utilizza `lplpFileNames` quindi `SccAddFromScc` il parametro della funzione per passare nella cartella di destinazione. Il plug-in utilizza tale cartella di destinazione per inserire i file aggiunti dal controllo del codice sorgente. Se il plug-in `SCC_I_SHARESUBPROJOK` non `SCC_OPT_SHARESUBPROJ` restituisce quando l'opzione è impostata, l'IDE presuppone che il plug-in è in grado di aggiungere file solo nella cartella locale corrente.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
