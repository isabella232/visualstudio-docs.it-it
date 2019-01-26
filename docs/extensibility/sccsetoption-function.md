---
title: Funzione SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa71b9397a1f8af11f65558e024d2611d96aa47e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961270"
---
# <a name="sccsetoption-function"></a>Funzione SccSetOption
La funzione imposta le opzioni che controllano il comportamento del controllo del codice sorgente del plug-in.  
  
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
 [in] La struttura del contesto plug-in del controllo origine.  
  
 nOption  
 [in] L'opzione da impostare.  
  
 dwVal  
 [in] Impostazioni per l'opzione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'opzione è stata impostata.|  
|SCC_I_SHARESUBPROJOK|Restituito se `nOption` era `SCC_OPT_SHARESUBPROJ` e il controllo del codice sorgente del plug-in consente l'IDE impostare la cartella di destinazione.|  
|SCC_E_OPNOTSUPPORTED|L'opzione non è stata impostata e non è affidabile.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione per controllare il comportamento del controllo del codice sorgente del plug-in. Il primo parametro, `nOption`, indica il valore da impostare, mentre il secondo, `dwVal`, indica che cosa fare con tale valore. Il plug-in archivia le informazioni associate una `pvContext``,` in modo che l'IDE deve chiamare questa funzione dopo la chiamata di [SccInitialize](../extensibility/sccinitialize-function.md) (ma non necessariamente dopo ogni chiamata ai [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Riepilogo delle opzioni e i relativi valori:  
  
|`nOption`|`dwValue`|Descrizione|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Attiva/Disattiva sfondo accodamento degli eventi.|  
|`SCC_OPT_USERDATA`|Valore arbitrario|Specifica un valore di utente da passare per il [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funzione di callback.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se l'IDE supporta attualmente un'operazione di annullamento.|  
|`SCC_OPT_NAMECHANGEPFN`|Puntatore per il [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funzione di callback|Imposta un puntatore a una funzione di callback modifica del nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se l'IDE consente il controllo all'esterno i file manualmente (tramite l'interfaccia utente del controllo origine) o se si deve essere estratta solo tramite il plug-in del controllo del codice sorgente.|  
|`SCC_OPT_SHARESUBPROJ`|N/D|Se il controllo del codice sorgente del plug-in consente l'IDE specificare la cartella di progetto locale, il plug-in restituisce `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Se `nOption` è `SCC_OPT_EVENTQUEUE`, l'IDE è la disabilitazione (o la riabilitazione) l'elaborazione in background. Ad esempio, durante una compilazione, l'IDE potrebbe indicare il controllo del codice sorgente del plug-in per arrestare l'elaborazione su inattivo di alcun tipo. Dopo la compilazione, potrebbe abilitare nuovamente l'elaborazione in background per mantenere aggiornato coda di eventi del plug-in. Corrispondente per il `SCC_OPT_EVENTQUEUE` valore del `nOption`, sono presenti due valori possibili per `dwVal`, vale a dire, `SCC_OPT_EQ_ENABLE` e `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Se il valore per `nOption` è `SCC_OPT_HASCANCELMODE`, l'IDE consente agli utenti di annullare l'esecuzione di operazioni lunghe. L'impostazione `dwVal` a `SCC_OPT_HCM_NO` (predefinito) indica che l'IDE è disponibile alcuna modalità di annullamento. Il plug-in del controllo del codice sorgente deve offrire il proprio pulsante Annulla se vuole che l'utente sia in grado di annullare. `SCC_OPT_HCM_YES` indica che l'IDE offre la possibilità di annullare un'operazione, in modo che il plug-in del controllo del codice sorgente non è necessario visualizzare il proprio pulsante Annulla. Se l'IDE imposta `dwVal` al `SCC_OPT_HCM_YES`, si è preparato a rispondere alle `SCC_MSG_STATUS` e `DOCANCEL` i messaggi inviati al `lpTextOutProc` funzione di callback (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Se l'IDE non imposta questa variabile, il plug-in non devono inviare questi due messaggi.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Se nOption è impostato su `SCC_OPT_NAMECHANGEPFN`, sia l'origine e plug-in controllo e l'IDE lo consentono, il plug-in può effettivamente rinominare o spostare un file durante un'operazione di controllo del codice sorgente. Il `dwVal` verrà impostato su un puntatore a funzione di tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante un'operazione di controllo del codice sorgente, il plug-in può chiamare questa funzione, passando i tre parametri. Questi sono il nome precedente (con percorso completo) di un file, il nuovo nome (con percorso completo) del file e un puntatore alle informazioni che sono pertinente per l'IDE. Invia l'IDE in questo ultimo puntatore chiamando `SccSetOption` con `nOption` impostata su `SCC_OPT_USERDATA`, con `dwVal` che punta ai dati. Supporto per questa funzione è facoltativo. Un plug VSSCI-che usa questa possibilità deve inizializzare relative variabili di dati utente e puntatore funzione a `NULL`, e non deve chiamare una funzione di ridenominazione, a meno che non lo è stato assegnato uno. Deve inoltre essere preparata per contenere il valore specificato o modificarla in risposta a una nuova chiamata a `SccSetOption`. Non si verificherà all'interno di un'operazione di comando di controllo codice sorgente, ma può capitare tra i comandi.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Se nOption è impostato su `SCC_OPT_SCCCHECKOUTONLY`, l'IDE è che indica che i file nel progetto attualmente aperto non dovrebbero mai essere estratto manualmente tramite l'interfaccia utente del sistema di controllo di origine. Al contrario, i file devono essere estratti solo tramite il controllo del codice sorgente del plug-nel controllo dell'IDE. Se `dwValue` è impostata su `SCC_OPT_SCO_NO`, significa che i file devono essere considerati normalmente il plug-in e possono essere estratta tramite il controllo del codice sorgente dell'interfaccia utente. Se `dwValue` è impostata su `SCC_OPT_SCO_YES`, quindi solo il plug-in è consentita per estrarre i file e interfaccia utente del sistema di controllo di origine non deve essere richiamato. Ciò è utile nelle situazioni in cui l'IDE potrebbe essere "pseudo-files" che hanno un significato da estrarre solo tramite l'IDE.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Se`nOption` è impostata su `SCC_OPT_SHARESUBPROJ`, l'IDE viene verificata l'esistenza di plug-in del controllo del codice sorgente è possibile usare una cartella locale specificata quando si aggiungono file dal controllo del codice sorgente. Il valore della `dwVal` parametro non è importante in questo caso. Se il plug-in consente l'IDE specificare la cartella di destinazione locale in cui verranno aggiunti i file di origine controllare quando il [SccAddFromScc](../extensibility/sccaddfromscc-function.md) viene chiamato, il plug-in deve restituire `SCC_I_SHARESUBPROJOK` quando il `SccSetOption` è (funzione) viene chiamato. L'IDE Usa quindi il `lplpFileNames` parametro il `SccAddFromScc` funzione passare nella cartella di destinazione. Il plug-in Usa tale cartella di destinazione per inserire i file aggiunti dal controllo del codice sorgente. Se il plug-in non restituisce `SCC_I_SHARESUBPROJOK` quando il `SCC_OPT_SHARESUBPROJ` opzione è impostata, l'IDE si presuppone che il plug-in è in grado di aggiungere file solo nella cartella locale corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)