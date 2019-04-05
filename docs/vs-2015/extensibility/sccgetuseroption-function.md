---
title: Funzione SccGetUserOption | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964455"
---
# <a name="sccgetuseroption-function"></a>Funzione SccGetUserOption
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 nOption  
 [in] Opzione da recuperare (per le opzioni possibili, vedere la sezione Osservazioni).  
  
 lpVal  
 [out] Valore associato all'opzione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Opzione è stato recuperato correttamente.|  
|SCC_E_OPNOTSUPPORTED|Opzione non è supportata.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Le opzioni seguenti sono supportate da questo comando:  
  
|Opzione User|Descrizione|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se l'utente desidera estrarre la versione locale dei file. `lpVal` viene assegnato `SCC_USEROPT_COLV_YES` (utente desidera estrarre i file locali) o `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codici di errore](../extensibility/error-codes.md)
