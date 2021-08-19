---
description: Questa funzione imposta le opzioni che controllano il comportamento del plug-in del controllo del codice sorgente.
title: Funzione SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a918dad74fe777842fa22395d80535113792e119
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158333"
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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 nOption

[in] Opzione impostata.

 dwVal

[in] Impostazioni per l'opzione .

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'opzione è stata impostata correttamente.|
|SCC_I_SHARESUBPROJOK|Restituito se `nOption` era `SCC_OPT_SHARESUBPROJ` e il plug-in del controllo del codice sorgente consente all'IDE di impostare la cartella di destinazione.|
|SCC_E_OPNOTSUPPORTED|L'opzione non è stata impostata e non deve essere basata su .|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione per controllare il comportamento del plug-in del controllo del codice sorgente. Il primo parametro, , indica il valore impostato, mentre il secondo, , indica cosa `nOption` `dwVal` fare con tale valore. Il plug-in archivia queste informazioni associate a un in modo che l'IDE deve chiamare questa funzione dopo aver chiamato SccInitialize (ma non necessariamente dopo ogni chiamata a `pvContext``,` [SccOpenProject).](../extensibility/sccopenproject-function.md) [](../extensibility/sccinitialize-function.md)

 Riepilogo delle opzioni e dei relativi valori:

|`nOption`|`dwValue`|Descrizione|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Abilita/disabilita l'accodamento degli eventi in background.|
|`SCC_OPT_USERDATA`|Valore arbitrario|Specifica un valore utente da passare alla funzione di callback [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se l'IDE supporta attualmente l'annullamento di un'operazione.|
|`SCC_OPT_NAMECHANGEPFN`|Puntatore alla funzione di callback [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Imposta un puntatore a una funzione di callback di modifica del nome.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se l'IDE consente l'estrazione manuale dei file (tramite l'interfaccia utente del controllo del codice sorgente) o se devono essere estratti solo tramite il plug-in del controllo del codice sorgente.|
|`SCC_OPT_SHARESUBPROJ`|N/A|Se il plug-in del controllo del codice sorgente consente all'IDE di specificare la cartella del progetto locale, il plug-in restituisce `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Se `nOption` è `SCC_OPT_EVENTQUEUE` , l'IDE disabilita (o abilita nuovamente) l'elaborazione in background. Durante una compilazione, ad esempio, l'IDE potrebbe indicare al plug-in del controllo del codice sorgente di arrestare l'elaborazione inattiva di qualsiasi tipo. Dopo la compilazione, ri enablerebbe l'elaborazione in background per mantenere aggiornata la coda di eventi del plug-in. Corrispondenti al `SCC_OPT_EVENTQUEUE` valore di , sono disponibili due valori possibili per , in modo specifico e `nOption` `dwVal` `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Se il valore di `nOption` è `SCC_OPT_HASCANCELMODE` , l'IDE consente agli utenti di annullare operazioni lunghe. `dwVal`L'impostazione `SCC_OPT_HCM_NO` su (impostazione predefinita) indica che l'IDE non ha alcuna modalità di annullamento. Il plug-in del controllo del codice sorgente deve offrire il proprio pulsante Annulla se vuole che l'utente sia in grado di annullare. `SCC_OPT_HCM_YES` indica che l'IDE consente di annullare un'operazione, pertanto il plug-in SCC non deve visualizzare il proprio pulsante Annulla. Se l'IDE imposta su , è pronto a rispondere ai messaggi e inviati alla funzione `dwVal` `SCC_OPT_HCM_YES` di callback `SCC_MSG_STATUS` `DOCANCEL` `lpTextOutProc` (vedere [LPTEXTOUTPROC).](../extensibility/lptextoutproc.md) Se l'IDE non imposta questa variabile, il plug-in non deve inviare questi due messaggi.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Se nOption è impostato su e sia il plug-in del controllo del codice sorgente che l'IDE lo consentono, il plug-in può effettivamente rinominare o spostare un file durante un'operazione di controllo del `SCC_OPT_NAMECHANGEPFN` codice sorgente. verrà `dwVal` impostato su un puntatore a funzione di tipo [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md) Durante un'operazione di controllo del codice sorgente, il plug-in può chiamare questa funzione, passando tre parametri. Si tratta del nome precedente (con percorso completo) di un file, del nuovo nome (con percorso completo) del file e di un puntatore a informazioni pertinenza dell'IDE. L'IDE invia in questo ultimo puntatore chiamando `SccSetOption` con impostato su , con che punta ai `nOption` `SCC_OPT_USERDATA` `dwVal` dati. Il supporto per questa funzione è facoltativo. Un plug-VSSCI che usa questa funzionalità deve inizializzare il puntatore a funzione e le variabili di dati utente su e non deve chiamare una funzione di ridenominazione a meno che non ne sia stata `NULL` specificata una. Deve anche essere preparato a contenere il valore assegnato o a modificarlo in risposta a una nuova chiamata a `SccSetOption` . Questa operazione non si verifica durante un'operazione di comando del controllo del codice sorgente, ma può verificarsi tra i comandi.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Se nOption è impostato su , l'IDE indica che i file nel progetto attualmente aperto non devono mai essere estratti manualmente tramite l'interfaccia utente del sistema `SCC_OPT_SCCCHECKOUTONLY` di controllo del codice sorgente. Al contrario, i file devono essere estratti solo tramite il plug-in del controllo del codice sorgente sotto il controllo IDE. Se è impostato su , significa che i file devono essere trattati normalmente dal plug-in e possono essere estratti tramite l'interfaccia utente `dwValue` del controllo del codice `SCC_OPT_SCO_NO` sorgente. Se è impostato su , solo il plug-in può estrarre i file e l'interfaccia utente del sistema di controllo del codice sorgente `dwValue` `SCC_OPT_SCO_YES` non deve essere richiamata. Questo si verifica per le situazioni in cui l'IDE potrebbe avere "pseudo-file" che hanno senso estrarre solo tramite l'IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Se è impostato su , l'IDE verifica se il plug-in del controllo del codice sorgente può usare una cartella locale specificata durante `nOption` l'aggiunta di file dal controllo del codice `SCC_OPT_SHARESUBPROJ` sorgente. In questo `dwVal` caso, il valore del parametro non è importante. Se il plug-in consente all'IDE di specificare la cartella di destinazione locale in cui verranno aggiunti i file dal controllo del codice sorgente quando viene chiamato [SccAddFromScc,](../extensibility/sccaddfromscc-function.md) il plug-in deve restituire quando viene chiamata la `SCC_I_SHARESUBPROJOK` `SccSetOption` funzione . L'IDE usa `lplpFileNames` quindi il parametro della funzione per passare la cartella di `SccAddFromScc` destinazione. Il plug-in usa tale cartella di destinazione per inserire i file aggiunti dal controllo del codice sorgente. Se il plug-in non viene restituito quando è impostata l'opzione , l'IDE presuppone che il plug-in sia in grado di aggiungere file solo nella `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` cartella locale corrente.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
