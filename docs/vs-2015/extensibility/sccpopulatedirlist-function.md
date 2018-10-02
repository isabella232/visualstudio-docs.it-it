---
title: Funzione SccPopulateDirList | Microsoft Docs
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
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358512c94f46971cc91ef3ed065c83ba56e5ad16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519863"
---
# <a name="sccpopulatedirlist-function"></a>Funzione SccPopulateDirList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccPopulateDirList](https://docs.microsoft.com/visualstudio/extensibility/sccpopulatedirlist-function).  
  
Questa funzione determina le directory e, facoltativamente, i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 nDirs  
 [in] Numero di percorsi di directory nella `lpDirPaths` matrice.  
  
 lpDirPaths  
 [in] Matrice di percorsi di directory da esaminare.  
  
 pfnPopulate  
 [in] Funzione di callback da chiamare per ogni nome del file nel percorso di directory e (facoltativamente) `lpDirPaths` (vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 [in] Valore che deve essere passato alla funzione di callback invariato.  
  
 Opzioni  
 [in] Una combinazione di valori che controllano il modo in cui vengono elaborate le directory (vedere la sezione "PopulateDirList flags" [flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione è stata completata.|  
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|  
  
## <a name="remarks"></a>Note  
 Solo le directory e, facoltativamente, i nomi di file che sono effettivamente nel repository del controllo del codice sorgente vengono passati alla funzione di callback.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codici di errore](../extensibility/error-codes.md)

