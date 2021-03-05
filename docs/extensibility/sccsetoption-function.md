---
description: Questa funzione imposta le opzioni che controllano il comportamento del plug-in del controllo del codice sorgente.
title: Funzione SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e25647eb8d2e5796665f072af6df43b2f585c7b0
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221379"
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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 nOption

in Opzione da impostare.

 dwVal

in Impostazioni per l'opzione.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'opzione è stata impostata correttamente.|
|SCC_I_SHARESUBPROJOK|Restituito se `nOption` è `SCC_OPT_SHARESUBPROJ` e il plug-in del controllo del codice sorgente consente all'IDE di impostare la cartella di destinazione.|
|SCC_E_OPNOTSUPPORTED|L'opzione non è stata impostata e non deve essere basata su.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione per controllare il comportamento del plug-in del controllo del codice sorgente. Il primo parametro, `nOption` , indica il valore che viene impostato, mentre il secondo, `dwVal` , indica le operazioni da eseguire con tale valore. Il plug-in archivia queste informazioni associate a un oggetto in `pvContext``,` modo che l'IDE debba chiamare questa funzione dopo la chiamata a [SccInitialize](../extensibility/sccinitialize-function.md) (ma non necessariamente dopo ogni chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Riepilogo delle opzioni e dei relativi valori:

|`nOption`|`dwValue`|Descrizione|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Abilita/Disabilita l'accodamento degli eventi in background.|
|`SCC_OPT_USERDATA`|Valore arbitrario|Specifica un valore utente da passare alla funzione di callback [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) .|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se l'IDE supporta attualmente l'annullamento di un'operazione.|
|`SCC_OPT_NAMECHANGEPFN`|Puntatore alla funzione di callback [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Imposta un puntatore a una funzione di callback di modifica del nome.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se l'IDE consente l'estrazione manuale dei file (tramite l'interfaccia utente del controllo del codice sorgente) o se devono essere estratti solo tramite il plug-in del controllo del codice sorgente.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Se il plug-in del controllo del codice sorgente consente all'IDE di specificare la cartella del progetto locale, viene restituito il plug-in `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Se `nOption` è `SCC_OPT_EVENTQUEUE` , l'IDE sta disabilitando o riattivando l'elaborazione in background. Ad esempio, durante una compilazione, l'IDE potrebbe indicare al plug-in del controllo del codice sorgente di arrestare l'elaborazione inattiva di qualsiasi tipo. Dopo la compilazione, l'elaborazione in background verrà riabilitata per rendere aggiornata la coda degli eventi del plug-in. Corrispondente al `SCC_OPT_EVENTQUEUE` valore di `nOption` , sono disponibili due valori possibili per `dwVal` , ovvero `SCC_OPT_EQ_ENABLE` e `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Se il valore di `nOption` è `SCC_OPT_HASCANCELMODE` , l'IDE consente agli utenti di annullare le operazioni lunghe. `dwVal`L'impostazione di su `SCC_OPT_HCM_NO` (impostazione predefinita) indica che l'IDE non dispone della modalità di annullamento. Il plug-in del controllo del codice sorgente deve fornire il proprio pulsante Annulla se desidera che l'utente sia in grado di annullare. `SCC_OPT_HCM_YES` indica che l'IDE fornisce la possibilità di annullare un'operazione, in modo che il plug-in SCC non debba visualizzare il proprio pulsante Annulla. Se l'IDE imposta `dwVal` su `SCC_OPT_HCM_YES` , è pronto a rispondere ai `SCC_MSG_STATUS` messaggi e `DOCANCEL` inviati alla funzione di `lpTextOutProc` callback (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Se l'IDE non imposta questa variabile, il plug-in non deve inviare questi due messaggi.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Se nOption è impostato su `SCC_OPT_NAMECHANGEPFN` e il plug-in del controllo del codice sorgente e l'IDE lo consentono, il plug-in può effettivamente rinominare o spostare un file durante un'operazione del controllo del codice sorgente. `dwVal`Verrà impostato su un puntatore a funzione di tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante un'operazione di controllo del codice sorgente, il plug-in può chiamare questa funzione, passando tre parametri. Si tratta del nome precedente (con percorso completo) di un file, del nuovo nome (con percorso completo) del file e di un puntatore alle informazioni rilevate nell'IDE. L'IDE invia in questo ultimo puntatore chiamando `SccSetOption` con `nOption` impostato su `SCC_OPT_USERDATA` , con `dwVal` il riferimento ai dati. Il supporto per questa funzione è facoltativo. Un plug-in VSSCI che usa questa capacità deve inizializzare il puntatore a funzione e le variabili di dati utente su `NULL` e non deve chiamare una funzione Rename a meno che non ne sia stato assegnato uno. Deve anche essere preparato per contenere il valore assegnato o per modificarlo in risposta a una nuova chiamata a `SccSetOption` . Questo problema non si verificherà durante un'operazione di comando del controllo del codice sorgente, ma potrebbe verificarsi tra i comandi.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Se nOption è impostato su `SCC_OPT_SCCCHECKOUTONLY` , l'IDE indica che i file nel progetto attualmente aperto non devono essere mai estratti manualmente tramite l'interfaccia utente del sistema di controllo del codice sorgente. Al contrario, i file devono essere estratti solo tramite il plug-in del controllo del codice sorgente nel controllo IDE. Se `dwValue` è impostato su `SCC_OPT_SCO_NO` , significa che i file devono essere gestiti normalmente dal plug-in e possono essere estratti tramite l'interfaccia utente del controllo del codice sorgente. Se `dwValue` è impostato su `SCC_OPT_SCO_YES` , solo il plug-in è autorizzato a estrarre i file e l'interfaccia utente del sistema di controllo del codice sorgente non deve essere richiamata. Questo si verifica per le situazioni in cui l'IDE potrebbe avere "pseudo-file", che hanno senso solo nell'IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Se `nOption` è impostato su `SCC_OPT_SHARESUBPROJ` , l'IDE sta verificando se il plug-in del controllo del codice sorgente può utilizzare una cartella locale specificata durante l'aggiunta di file dal controllo del codice sorgente. Il valore del parametro non è `dwVal` importante in questo caso. Se il plug-in consente all'IDE di specificare la cartella di destinazione locale in cui verranno aggiunti i file dal controllo del codice sorgente quando viene chiamato [SccAddFromScc](../extensibility/sccaddfromscc-function.md) , il plug-in deve restituire `SCC_I_SHARESUBPROJOK` quando `SccSetOption` viene chiamata la funzione. L'IDE usa quindi il `lplpFileNames` parametro della `SccAddFromScc` funzione per passare la cartella di destinazione. Il plug-in utilizza tale cartella di destinazione per inserire i file aggiunti dal controllo del codice sorgente. Se il plug-in non restituisce `SCC_I_SHARESUBPROJOK` quando l' `SCC_OPT_SHARESUBPROJ` opzione è impostata, l'IDE presuppone che il plug-in sia in grado di aggiungere file solo nella cartella locale corrente.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
