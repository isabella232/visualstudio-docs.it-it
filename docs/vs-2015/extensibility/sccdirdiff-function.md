---
title: Funzione SccDirDiff | Microsoft Docs
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
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d2c45773a9d45c69cfed4f773bc5cdfcfa1c305
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791189"
---
# <a name="sccdirdiff-function"></a>Funzione SccDirDiff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione consente di visualizzare le differenze tra la directory corrente del disco di client e il progetto corrispondente nel controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 lpDirName  
 [in] Percorso completo nella directory locale per cui si desidera mostrare una differenza visual.  
  
 dwFlags  
 [in] Flag di comando (vedere la sezione Osservazioni sezione).  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La directory su disco è lo stesso nome di progetto nel controllo del codice sorgente.|  
|SCC_I_FILESDIFFER|La directory su disco è diversa dal progetto nel controllo del codice sorgente.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTCONTROLLED|La directory non è incluso nel controllo del codice sorgente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
|SCC_E_FILENOTEXIST|Directory locale non è stata trovata.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene utilizzata per indicare il controllo del codice sorgente del plug-in da visualizzare all'utente un elenco delle modifiche apportate a una directory specificata. Il plug-in verrà visualizzata la relativa finestra, in un formato di propria scelta, per visualizzare le differenze tra la directory dell'utente su disco e il progetto corrispondente nel controllo della versione.  
  
 Se un confronto di plug-in supporta delle directory affatto, deve supportare il confronto delle directory in base a nome del file anche se non sono supportate le opzioni "diff veloce".  
  
|`dwFlags`|Interpretazione|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Confronto tra maiuscole e minuscole (possono essere usate per diff veloce o oggetto visivo).|  
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (possono essere usate per quick-diff o oggetto visivo).|  
|SCC_DIFF_QD_CONTENTS|Se supportato dal controllo del codice sorgente del plug-in, in modo invisibile confronta la directory, byte per byte.|  
|SCC_DIFF_QD_CHECKSUM|Se supportato dal plug-in, in modo invisibile Confronta alla directory tramite un checksum o, se non è supportato, esegue il fallback a SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Se supportato dal plug-in, in modo invisibile Confronta alla directory tramite il timestamp oppure, se non è supportato, esegue il fallback su SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Questa funzione Usa gli stessi flag di comando come il [SccDiff](../extensibility/sccdiff-function.md). Tuttavia, un plug-in del controllo del codice sorgente può scegliere di non supportare l'operazione "diff veloce" per le directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)

