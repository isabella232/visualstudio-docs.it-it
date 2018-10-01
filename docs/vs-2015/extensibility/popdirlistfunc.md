---
title: POPDIRLISTFUNC | Microsoft Docs
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
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed4cb154b1b1f74a6b0b6e64063a826b80364dd3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529407"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [POPDIRLISTFUNC](https://docs.microsoft.com/visualstudio/extensibility/popdirlistfunc).  
  
Si tratta di una funzione di callback specificata per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funzione per aggiornare un insieme di directory e, facoltativamente, i nomi di file per scoprire che si trovano sotto controllo del codice sorgente.  
  
 Il `POPDIRLISTFUNC` callback deve essere chiamato solo per le directory e i nomi di file (nell'elenco specificato per il `SccPopulateDirList` (funzione)) inclusi effettivamente nel controllo del codice sorgente.  
  
## <a name="signature"></a>Signature  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 [in] Valore di utente passato [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bOpzioni cartella  
 [in] `TRUE` se il nome in `lpDirectoryOrFileName` è una directory; in caso contrario, il nome è un nome di file.  
  
 lpDirectoryOrFileName  
 [in] Percorso locale completo a un nome di file o directory che si trova sotto controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Nell'IDE viene restituito un codice di errore appropriato:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Continuare l'elaborazione.|  
|SCC_I_OPERATIONCANCELED|Arrestare l'elaborazione.|  
|SCC_E_xxx|Qualsiasi errore di controllo di origine appropriato deve arrestare l'elaborazione.|  
  
## <a name="remarks"></a>Note  
 Se il `fOptions` parametro del `SccPopulateDirList` funzione contiene il `SCC_PDL_INCLUDEFILES` flag, quindi l'elenco conterrà probabilmente i nomi di file, nonché i nomi di directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codici di errore](../extensibility/error-codes.md)

