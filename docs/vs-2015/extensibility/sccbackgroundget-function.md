---
title: Funzione SccBackgroundGet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 118d8458fd9581a87baea08452d0011d4d66c9a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839544"
---
# <a name="sccbackgroundget-function"></a>Funzione SccBackgroundGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione recupera dal controllo del codice sorgente ognuno dei file specificati senza alcuna interazione da parte dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 in Puntatore al contesto del plug-in del controllo del codice sorgente.  
  
 nFile  
 in Numero di file specificati nella `lpFileNames` matrice.  
  
 lpFileNames  
 [in, out] Matrice di nomi di file da recuperare.  
  
> [!NOTE]
> I nomi devono essere nomi di file locali completi.  
  
 dwFlags  
 in Flag di comando ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).  
  
 dwBackgroundOperationID  
 in Valore univoco associato a questa operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata correttamente.|  
|SCC_E_BACKGROUNDGETINPROGRESS|È già in corso un recupero in background (il plug-in del controllo del codice sorgente deve restituire questo valore solo se non supporta le operazioni batch simultanee).|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
  
## <a name="remarks"></a>Commenti  
 Questa funzione viene sempre chiamata su un thread diverso da quello che ha caricato il plug-in del controllo del codice sorgente. Non è previsto che la funzione restituisca fino a quando non viene eseguita. Tuttavia, può essere chiamato più volte con più elenchi di file, nello stesso momento.  
  
 L'uso dell' `dwFlags` argomento è identico a quello di [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
