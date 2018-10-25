---
title: Funzione SccPopulateList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73cc3886fe486498f7d0fbe89d0b68cf873c9d0b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903569"
---
# <a name="sccpopulatelist-function"></a>Funzione SccPopulateList
Questa funzione aggiorna un elenco di file per un comando di controllo di origine specifica e fornisce lo stato del controllo origine su tutti i file specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 Ncomando  
 [in] Il comando di controllo di origine che verrà applicato a tutti i file di `lpFileNames` matrice (vedere [codice del comando](../extensibility/command-code-enumerator.md) per un elenco di possibili comandi).  
  
 nFile  
 [in] Numero di file nei `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi file noti all'IDE.  
  
 pfnPopulate  
 [in] La funzione di callback dell'IDE da chiamare per aggiungere e rimuovere i file (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 [in] Valore che deve essere passato alla funzione di callback invariato.  
  
 lpStatus  
 [in, out] Matrice per il plug-in per restituire i flag di stato per ogni file di controllo del codice sorgente.  
  
 Opzioni  
 [in] Flag di comando (vedere la sezione "PopulateList flag" [flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per informazioni dettagliate).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione esamina l'elenco dei file per il relativo stato corrente. Usa il `pfnPopulate` funzione di callback per notificare al chiamante quando un file non corrisponde ai criteri per il `nCommand`. Ad esempio, se il comando è `SCC_COMMAND_CHECKIN` e non è estratto un file nell'elenco, quindi il callback viene utilizzato per indicare al chiamante. In alcuni casi, il plug-in del controllo del codice sorgente potrebbero essere presenti altri file che potrebbero essere parte del comando e aggiungerli. In questo modo, ad esempio, un utente di Visual Basic per estrarre un file con estensione bmp viene usato dal progetto la propria, ma non viene visualizzato nel file di progetto Visual Basic. Un utente sceglie il **ottenere** comando nell'IDE. L'IDE verrà visualizzato un elenco di tutti i file che ritiene che l'utente può ottenere, ma prima che l'elenco viene visualizzato, il `SccPopulateList` funzione viene chiamata per verificare che l'elenco deve essere visualizzato sia aggiornato.  
  
## <a name="example"></a>Esempio  
 L'IDE compila un elenco di file che ritiene che l'utente può ottenere. Prima di visualizzare l'elenco, viene chiamato il `SccPopulateList` di funzione, offrendo il controllo del codice sorgente del plug-nella possibilità di aggiungere ed eliminare i file dall'elenco. Il plug-in modifica l'elenco chiamando la funzione di callback specificato (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per altri dettagli).  
  
 Continua il plug-in chiamare il `pfnPopulate` funzione, che aggiunge ed elimina i file, fino a quando non è terminato e lo restituisce il `SccPopulateList` (funzione). L'IDE può quindi visualizzare il relativo elenco. Il `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. Il plug-in compila lo stato di tutti questi file oltre a rendere utilizzo della funzione di callback.  
  
> [!NOTE]
>  Un plug-in del controllo del codice sorgente ha sempre la possibilità di restituire semplicemente immediatamente da questa funzione, senza modificare l'elenco. Se un plug-in viene implementata questa funzione, è possibile che questo impostando il `SCC_CAP_POPULATELIST` dei bit di flag funzionalità nella prima chiamata per il [SccInitialize](../extensibility/sccinitialize-function.md). Per impostazione predefinita, il plug-in deve sempre presupporre che tutti gli elementi passati sono file. Tuttavia, se l'IDE imposta il `SCC_PL_DIR` flag nel `fOptions` parametro, tutti gli elementi passati devono essere considerati le directory. Il plug-in necessario aggiungere tutti i file che appartengono nelle directory. L'IDE non passeranno mai una combinazione di file e directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [Codice di comando](../extensibility/command-code-enumerator.md)