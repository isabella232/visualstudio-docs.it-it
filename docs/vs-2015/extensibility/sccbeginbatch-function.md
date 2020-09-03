---
title: Funzione SccBeginBatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189556"
---
# <a name="sccbeginbatch-function"></a>Funzione SccBeginBatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione avvia una sequenza di batch di operazioni del controllo del codice sorgente. Il [SccEndBatch](../extensibility/sccendbatch-function.md) verrà chiamato per terminare il batch. Questi batch non possono essere annidati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 No.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il batch di operazioni è stato avviato correttamente.|  
|SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Osservazioni  
 I batch del controllo del codice sorgente vengono usati per eseguire le stesse operazioni in più progetti o in più contesti. I batch possono essere usati per eliminare le finestre di dialogo per progetto ridondanti dall'esperienza utente durante un'operazione in batch. La `SccBeginBatch` funzione e [SccEndBatch](../extensibility/sccendbatch-function.md) vengono usati come coppia di funzioni per indicare l'inizio e la fine di un'operazione. Non possono essere annidati. `SccBeginBatch` imposta un flag che indica che è in corso un'operazione batch.  
  
 Mentre è attiva un'operazione batch, il plug-in del controllo del codice sorgente deve presentare al massimo una finestra di dialogo per qualsiasi domanda all'utente e applicare la risposta da tale finestra di dialogo in tutte le operazioni successive.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
