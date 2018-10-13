---
title: Funzione SccEndBatch | Microsoft Docs
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
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ca4e829f4535018c456011654058b6c0ae5dea3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246695"
---
# <a name="sccendbatch-function"></a>Funzione SccEndBatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione si conclude un batch di operazioni di controllo codice sorgente. Questi batch non possono essere annidati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Batch di operazioni conclude correttamente.|  
|SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Batch di controllo di origine utilizzati per eseguire le stesse operazioni di controllo di origine in più progetti o più contesti. Batch sono utilizzabile per eliminare le finestre di dialogo ridondanti rispetto all'esperienza utente durante un'operazione batch. Il [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e il `SccEndBatch` funzione vengono utilizzati come coppia per indicare l'inizio e alla fine di un'operazione. Non possono essere annidate.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)

