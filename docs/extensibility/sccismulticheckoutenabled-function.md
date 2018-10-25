---
title: Funzione SccIsMultiCheckoutEnabled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4a71f839c2129bcfb699188dec09b02b18d4cd1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920118"
---
# <a name="sccismulticheckoutenabled-function"></a>Funzione SccIsMultiCheckoutEnabled
Questa funzione controlla se il plug-in del controllo del codice sorgente consente le estrazioni multiple in un file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 pbMultiCheckout  
 [out] Specifica se le estrazioni multiple sono abilitate per questo progetto (diverso da zero indica che le estrazioni multiple sono supportate).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il controllo è riuscito.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Nell'IDE viene due controlli per determinare se i file possono essere estratti contemporaneamente da più di un utente. In primo luogo, il controllo del codice sorgente deve supportare estrazioni multiple. Il plug-in del controllo del codice sorgente possa specificare questa funzionalità durante l'inizializzazione, specificando il `SCC_CAP_MULTICHECKOUT`. Successivamente, come un secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta le estrazioni multiple. Se le estrazioni multiple sono supportate per il progetto selezionato, i plug-in restituisce un esito positivo del codice e imposta `pbMultiCheckout` diverso da zero a (`TRUE`) o `FALSE`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)