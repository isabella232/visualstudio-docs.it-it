---
title: Funzione SccInitialize | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9febcc2eecea4533f1c37a0068e2d94ab66ff2af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750715"
---
# <a name="sccinitialize-function"></a>Funzione SccInitialize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione inizializza il plug-in del controllo del codice sorgente e fornisce le funzionalità e i limiti per l'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppvContext`  
 [in] Il plug-in del controllo del codice sorgente è possibile inserire un puntatore alla relativa struttura scelta qui.  
  
 `hWnd`  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 `lpCallerName`  
 [in] Il nome del programma di chiamata del plug-in controllo del codice sorgente.  
  
 `lpSccName`  
 [in, out] Il buffer in cui il plug-in del controllo del codice sorgente inserisce il proprio nome (non deve superare `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Restituisce il controllo del codice sorgente flag funzionalità del plug-in.  
  
 `lpAuxPathLabel`  
 [in, out] Il buffer in cui il plug-in del controllo del codice sorgente inserisce una stringa che descrive la `lpAuxProjPath` restituito dal parametro il [SccOpenProject](../extensibility/sccopenproject-function.md) e il [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (non deve superare `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Restituisce la lunghezza massima consentita per un commento di estrazione.  
  
 `pnCommentLen`  
 [out] Restituisce la lunghezza massima consentita per gli altri commenti.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|È stata completata l'inizializzazione di controllo di origine.|  
|SCC_E_INITIALIZEFAILED|Nelze inicializovat sistema.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire l'operazione specificata.|  
|SCC_E_NONSPECFICERROR|Errore non specifico. controllo del codice sorgente non è stato inizializzato.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione quando viene caricato prima di tutto il plug-in del controllo del codice sorgente. In questo modo l'IDE da passare alcune informazioni, ad esempio il nome del chiamante, il plug-in. L'IDE inoltre consente di ottenere determinate informazioni, quali la lunghezza massima consentita per i commenti e le funzionalità del plug-in.  
  
 Il `ppvContext` punta a un `NULL` puntatore. Il plug-in del controllo del codice sorgente può allocare una struttura per il proprio uso e archiviare un puntatore alla struttura in `ppvContext`. L'IDE passerà questo puntatore su ogni altra funzione API VSSCI, consentendo il plug-in per avere informazioni di contesto disponibili senza dover ricorrere a un archivio globale e per supportare più istanze di plug-in. Questa struttura deve essere deallocata quando il [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.  
  
 Il `lpCallerName` e `lpSccName` i parametri consentono l'IDE e il plug-in del controllo del codice sorgente per lo scambio di nomi. Questi nomi possono essere usati semplicemente per distinguere tra più istanze, o possono essere effettivamente visualizzate nei menu o finestre di dialogo.  
  
 Il `lpAuxPathLabel` parametro è una stringa utilizzata come un commento per identificare il percorso del progetto ausiliari che viene archiviato nel file di soluzione e passato al controllo del codice sorgente del plug-in una chiamata ai [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../includes/vsvss-md.md)] Usa la stringa "progetto di Visual SourceSafe:"; altri plug-in del controllo sorgente dovrebbero evitare di usare tale stringa.  
  
 Il `lpSccCaps` parametro fornisce il controllo del codice sorgente del plug-in una posizione in cui archiviare i flag di bit che indicano le funzionalità del plug-in. (Per un elenco completo dei flag di bit di funzionalità, vedere [flag di funzionalità](../extensibility/capability-flags.md)). Ad esempio, se i piani di plug-in per scrivere i risultati in una funzione di callback fornito dal chiamante, il plug-in verrebbe impostato la funzionalità di bit SCC_CAP_TEXTOUT. Ciò potrebbe segnalare l'IDE per creare una finestra per i risultati di controllo di versione.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Flag di funzionalità](../extensibility/capability-flags.md)

