---
title: Funzione SccGetCommandOptions | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7838ffaccbef6e4bdcde97313f118e7aa13b4d1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519683"
---
# <a name="sccgetcommandoptions-function"></a>Funzione SccGetCommandOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccGetCommandOptions](https://docs.microsoft.com/visualstudio/extensibility/sccgetcommandoptions-function).  
  
Questa funzione richiede all'utente le opzioni avanzate per un determinato comando.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 iCommand  
 [in] Il comando per il quale vengono richieste le opzioni avanzate (vedere [codice del comando](../extensibility/command-code-enumerator.md) per i valori possibili).  
  
 ppvOptions  
 [in] La struttura delle opzioni (può anche essere `NULL`).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_I_ADV_SUPPORT|Il controllo del codice sorgente del plug-in supporta le opzioni avanzate per il comando.|  
|SCC_I_OPERATIONCANCELED|L'utente ha annullato l'origine plug-in controllo **opzioni** nella finestra di dialogo.|  
|SCC_E_OPTNOTSUPPORTED|Il plug-in del controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ISCHECKEDOUT|Non è possibile eseguire questa operazione su un file che è attualmente estratto.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione per la prima volta con `ppvOptions` = `NULL` per determinare se il controllo del codice sorgente del plug-in supporta la funzionalità delle opzioni avanzate per il comando specificato. Se il plug-in supporta la funzionalità per il comando, l'IDE chiama questa funzione nuovamente quando l'utente richiede le opzioni avanzate (in genere implementato come un **avanzate** pulsante in una finestra di dialogo) e fornisce un puntatore non NULL per `ppvOptions` che punta a un `NULL` puntatore. Il plug-in archivia tutte le opzioni avanzate specificate dall'utente in una struttura di private e restituisce un puntatore alla struttura in `ppvOptions`. Questa struttura viene quindi passata a tutte le altre funzioni API dei plug-in del controllo sorgente che occorre conoscere, tra cui le chiamate successive al `SccGetCommandOptions` (funzione).  
  
 Un esempio può aiutare a chiarire questa situazione.  
  
 Un utente sceglie il **ottenere** comando e l'IDE visualizza un **ottenere** nella finestra di dialogo. Le chiamate dell'IDE di `SccGetCommandOptions` utilizzabile con `iCommand` impostata su `SCC_COMMAND_GET` e `ppvOptions` impostato su `NULL`. Ciò viene interpretato dal controllo del codice sorgente del plug-in come la domanda, "Sono le opzioni avanzate per questo comando?" Se il plug-in restituisce `SCC_I_ADV_SUPPORT`, l'IDE visualizza un **avanzate** pulsante nella relativa **ottenere** nella finestra di dialogo.  
  
 La prima volta che l'utente fa clic il **avanzate** pulsante, l'IDE chiama nuovamente il `SccGetCommandOptions` funzione, questa volta con un`NULL``ppvOptions` che punta a un `NULL` puntatore. I plug-in consente di visualizzare la propria **ottenere le opzioni** della finestra di dialogo chiede all'utente informazioni, inserita nella struttura di propria e restituisce un puntatore alla struttura in `ppvOptions`.  
  
 Se l'utente fa clic **avanzate** nuovamente nella finestra di dialogo stessa, l'IDE chiama il `SccGetCommandOptions` funzione nuovamente senza modificare `ppvOptions`, in modo che la struttura viene passata al plug-in. In questo modo il plug-in reinizializzare la finestra di dialogo per i valori che l'utente ha impostato in precedenza. Il plug-in consente di modificare la struttura posto prima della restituzione.  
  
 Infine, quando l'utente fa clic **OK** dell'IDE **ottenere** nella finestra di dialogo, le chiamate IDE di [SccGet](../extensibility/sccget-function.md), passando la struttura restituita `ppvOptions` che contiene il Opzioni avanzate.  
  
> [!NOTE]
>  Il comando `SCC_COMMAND_OPTIONS` viene usato quando l'IDE visualizza un **opzioni** finestra di dialogo che consente all'utente di imposta le preferenze che controllano il funzionamento dell'integrazione. Se il plug-in del controllo del codice sorgente fornire la propria finestra di dialogo Preferenze, può visualizzare da un **avanzate** pulsante nella finestra di dialogo Preferenze dell'IDE. Il plug-in è responsabile esclusivamente per il recupero e il mantenimento di queste informazioni. l'IDE non utilizzarlo o modificarlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di comando](../extensibility/command-code-enumerator.md)

