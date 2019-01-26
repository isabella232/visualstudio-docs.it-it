---
title: Funzione SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdc86d9b93d25a758e5321832b6bd4d98c171147
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982377"
---
# <a name="sccendbatch-function"></a>Funzione SccEndBatch
Questa funzione si conclude un batch di operazioni di controllo codice sorgente. Questi batch non possono essere annidati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
## <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Batch di operazioni conclude correttamente.|  
|SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Batch di controllo di origine utilizzati per eseguire le stesse operazioni di controllo di origine in più progetti o più contesti. Batch sono utilizzabile per eliminare le finestre di dialogo ridondanti rispetto all'esperienza utente durante un'operazione batch. Il [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e il `SccEndBatch` funzione vengono utilizzati come coppia per indicare l'inizio e alla fine di un'operazione. Non possono essere annidate.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)