---
title: Funzione SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dba45116c956c1edc1a8ffb691397375345c661
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967206"
---
# <a name="sccuninitialize-function"></a>Funzione SccUninitialize
Questa funzione Elimina tutte le allocazioni o connessioni aperte create da una precedente chiamata ai [SccInitialize](../extensibility/sccinitialize-function.md) in preparazione per il plug-in del controllo del codice sorgente in corso l'arresto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] Il puntatore alla struttura di contesto del plug-in controllo di origine creato nel [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La pulizia completata.|  
  
## <a name="remarks"></a>Note  
 Il plug-in del controllo del codice sorgente è responsabile della preparazione per essere arrestata e per liberare memoria in cui è allocato il plug-in per la struttura scelta. La funzione viene chiamata una volta per ogni istanza specifica di un plug-in. Una chiamata per il [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Nessun progetto può essere ancora aperto al momento della chiamata a `SccUninitialize`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)