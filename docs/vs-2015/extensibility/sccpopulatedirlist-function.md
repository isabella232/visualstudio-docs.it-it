---
title: Funzione SccPopulateDirList | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6078f0fd90855c432b333fd5967367460d0a364e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200018"
---
# <a name="sccpopulatedirlist-function"></a>Funzione SccPopulateDirList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione determina quali directory e, facoltativamente, i file vengono archiviati nel controllo del codice sorgente, dato un elenco di directory da esaminare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccPopulateDirList(  
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
 in Puntatore al contesto del plug-in del controllo del codice sorgente.  
  
 nDirs  
 in Numero di percorsi di directory nella `lpDirPaths` matrice.  
  
 lpDirPaths  
 in Matrice di percorsi di directory da esaminare.  
  
 pfnPopulate  
 in Funzione di callback da chiamare per ogni percorso di directory e (facoltativamente) nomefile in `lpDirPaths` (vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 in Valore che deve essere passato senza modifiche alla funzione di callback.  
  
 fOptions  
 in Combinazione di valori che controllano il modo in cui vengono elaborate le directory. vedere la sezione "flag PopulateDirList" di [flag utilizzata da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione è stata completata.|  
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|  
  
## <a name="remarks"></a>Osservazioni  
 Solo le directory e (facoltativamente) i nomi di file effettivamente presenti nel repository del controllo del codice sorgente vengono passati alla funzione di callback.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag utilizzato da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codici errore](../extensibility/error-codes.md)
