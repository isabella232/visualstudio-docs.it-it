---
title: Funzione SccBackgroundGet | Microsoft Docs
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
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 162bbc427b48ee10ea3a0b88837cf012f1c3fd07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517446"
---
# <a name="sccbackgroundget-function"></a>Funzione SccBackgroundGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccBackgroundGet](https://docs.microsoft.com/visualstudio/extensibility/sccbackgroundget-function).  
  
Questa funzione recupera dal controllo del codice sorgente ogni dei file specificati senza l'intervento dell'utente.  
  
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
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 nFile  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in, out] Matrice di nomi di file da recuperare.  
  
> [!NOTE]
>  I nomi devono essere completamente qualificati i nomi di file locale.  
  
 dwFlags  
 [in] Flag di comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Un valore univoco associato a questa operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata correttamente.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Uno per il recupero in background è già in corso (il plug-in del controllo del codice sorgente deve restituire questo solo se non supporta operazioni batch simultanei).|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del relativo completamento.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene sempre chiamata su un thread diverso da quello che caricata il plug-in del controllo del codice sorgente. Questa funzione non deve restituire fino al termine; Tuttavia, si può chiamato più volte con più elenchi di file, tutti nello stesso momento.  
  
 L'utilizzo dei `dwFlags` argomento è quello utilizzato per il [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)

