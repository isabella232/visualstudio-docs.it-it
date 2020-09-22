---
title: Funzione SccDirQueryInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839287"
---
# <a name="sccdirqueryinfo-function"></a>Funzione SccDirQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione esamina un elenco di directory complete per lo stato corrente.  
  
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
 in Struttura del contesto del plug-in del controllo del codice sorgente.  
  
 nDirs  
 in Numero di directory selezionate per la query.  
  
 lpDirNames  
 in Matrice di percorsi completi delle directory in cui eseguire la query.  
  
 lpStatus  
 [in, out] Una struttura di matrice per il plug-in del controllo del codice sorgente per restituire i flag di stato (vedere il [codice di stato della directory](../extensibility/directory-status-code-enumerator.md) per informazioni dettagliate).  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La query è stata completata.|  
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Commenti  
 La funzione compila la matrice restituita con una maschera di bit di bit della `SCC_DIRSTATUS` famiglia (vedere il [codice di stato della directory](../extensibility/directory-status-code-enumerator.md)), una voce per ogni directory specificata. La matrice di stato viene allocata dal chiamante.  
  
 L'IDE usa questa funzione prima della ridenominazione di una directory per verificare se la directory è sotto il controllo del codice sorgente eseguendo una query su se è presente un progetto corrispondente. Se la directory non è sotto il controllo del codice sorgente, l'IDE può fornire l'avviso appropriato all'utente.  
  
> [!NOTE]
> Se un plug-in del controllo del codice sorgente sceglie di non implementare uno o più valori di stato, i bit non implementati devono essere impostati su zero.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato directory](../extensibility/directory-status-code-enumerator.md)
