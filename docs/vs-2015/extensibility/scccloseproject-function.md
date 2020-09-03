---
title: Funzione SccCloseProject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156144"
---
# <a name="scccloseproject-function"></a>Funzione SccCloseProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione chiude un progetto, contrassegnando la fine di una sessione specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 Struttura del contesto del plug-in del controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il progetto è stato chiuso correttamente.|  
|SCC_E_PROJNOTOPEN|Nessun progetto attualmente aperto.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Osservazioni  
 [SccOpenProject](../extensibility/sccopenproject-function.md) viene sempre chiamato prima della funzione. Una chiamata a questa funzione è seguita da una chiamata alla `SccOpenProject` funzione o a [SccUninitialize](../extensibility/sccuninitialize-function.md), che termina la connessione al sistema di controllo del codice sorgente completamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
