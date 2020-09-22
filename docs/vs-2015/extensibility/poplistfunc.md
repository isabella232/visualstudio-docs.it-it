---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "90839812"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo callback viene fornito a [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene usato dal plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory (forniti anche alla `SccPopulateList` funzione).  
  
 Quando un utente sceglie il comando **Get** nell'IDE, l'IDE Visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'elenco esatto di tutti i file che l'utente potrebbe ottenere; Questo elenco è presente solo per il plug-in. Se altri utenti hanno aggiunto file al progetto di controllo del codice sorgente, questi file devono essere visualizzati nell'elenco, ma l'IDE non li conosce. L'IDE compila un elenco dei file che ritiene che l'utente possa ottenere. Prima che questo elenco venga visualizzato dall'utente, viene chiamato il [SccPopulateList](../extensibility/sccpopulatelist-function.md) che `,` fornisce al plug-in del controllo del codice sorgente la possibilità di aggiungere ed eliminare file dall'elenco.  
  
## <a name="signature"></a>Firma  
 Il plug-in del controllo del codice sorgente modifica l'elenco chiamando una funzione implementata dall'IDE con il prototipo seguente:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 Il `pvCallerData` parametro passato dal chiamante (l'IDE) a [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug-in del controllo del codice sorgente non deve presupporre nulla sul contenuto di questo parametro.  
  
 fAddRemove  
 Se `TRUE` , `lpFileName` è un file che deve essere aggiunto all'elenco dei file. Se `FALSE` , `lpFileName` è un file che deve essere eliminato dall'elenco dei file.  
  
 nStatus  
 Stato di `lpFileName` (una combinazione dei `SCC_STATUS` bit. per informazioni dettagliate, vedere il [codice di stato del file](../extensibility/file-status-code-enumerator.md) ).  
  
 lpFileName  
 Percorso completo della directory del nome file da aggiungere o eliminare dall'elenco.  
  
## <a name="return-value"></a>Valore restituito  
  
|valore|Descrizione|  
|-----------|-----------------|  
|`TRUE`|Il plug-in può continuare a chiamare questa funzione.|  
|`FALSE`|Si è verificato un problema sul lato IDE, ad esempio una situazione di memoria insufficiente. Il plug-in deve arrestare l'operazione.|  
  
## <a name="remarks"></a>Commenti  
 Per ogni file che il plug-in del controllo del codice sorgente desidera aggiungere o eliminare dall'elenco di file, chiama questa funzione, passando `lpFileName` . Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un file obsoleto da eliminare. Il `nStatus` parametro restituisce lo stato del file. Al termine dell'aggiunta e dell'eliminazione dei file del plug-in SCC, viene restituito dalla chiamata [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
> [!NOTE]
> Il `SCC_CAP_POPULATELIST` bit di funzionalità è necessario per Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)
