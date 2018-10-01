---
title: Funzione SccDirQueryInfo | Microsoft Docs
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
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d737f45a337f2b43243641ce898cc2ef1d3a82de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528542"
---
# <a name="sccdirqueryinfo-function"></a>Funzione SccDirQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccDirQueryInfo](https://docs.microsoft.com/visualstudio/extensibility/sccdirqueryinfo-function).  
  
Questa funzione esamina un elenco di directory completo per il relativo stato corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 nDirs  
 [in] Il numero di directory selezionati per essere eseguita una query.  
  
 lpDirNames  
 [in] Matrice di percorsi completi delle directory in cui eseguire una query.  
  
 lpStatus  
 [in, out] Una struttura di matrice per il controllo del codice sorgente del plug-in per restituire i flag di stato (vedere [il codice di stato Directory](../extensibility/directory-status-code-enumerator.md) per informazioni dettagliate).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La query è riuscita.|  
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 La funzione riempie la matrice restituita con una maschera di bit di bit dal `SCC_DIRSTATUS` famiglia (vedere [codice di stato Directory](../extensibility/directory-status-code-enumerator.md)), una voce per ogni directory di base. La matrice di stato viene allocata dal chiamante.  
  
 L'IDE Usa questa funzione prima della ridenominazione di una directory per controllare se la directory è incluso nel controllo sorgente eseguendo una query se dispone di un progetto corrispondente. Se la directory non è incluso nel controllo del codice sorgente, l'IDE può fornire l'avviso appropriato all'utente.  
  
> [!NOTE]
>  Se un plug-in del controllo del codice sorgente sceglie di non implementare uno o più dei valori di stato, non è implementata bits deve essere impostato su zero.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato directory](../extensibility/directory-status-code-enumerator.md)

