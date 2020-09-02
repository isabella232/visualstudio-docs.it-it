---
title: Funzione SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65641803c1fdcb4645bbc20f6cbc845e5d326689
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200057"
---
# <a name="sccismulticheckoutenabled-function"></a>Funzione SccIsMultiCheckoutEnabled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione controlla se il plug-in del controllo del codice sorgente consente più estrazioni in un file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 in Struttura del contesto del plug-in del controllo del codice sorgente.  
  
 pbMultiCheckout  
 out Specifica se sono abilitate più estrazioni per questo progetto (valore diverso da zero indica che sono supportate più estrazioni).  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il controllo è stato completato correttamente.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Osservazioni  
 L'IDE esegue due controlli per determinare se i file possono essere estratti simultaneamente da più di un utente. In primo luogo, il sistema di controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione specificando `SCC_CAP_MULTICHECKOUT` . Successivamente, come secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta più estrazioni. Se per il progetto selezionato sono supportate più estrazioni, il plug-in restituisce un codice di esito positivo e imposta `pbMultiCheckout` su un valore diverso da zero ( `TRUE` ) o `FALSE` .  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
