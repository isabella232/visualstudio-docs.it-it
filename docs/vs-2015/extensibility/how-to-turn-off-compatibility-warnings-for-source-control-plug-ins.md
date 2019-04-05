---
title: 'Procedura: Disattivare gli avvisi di compatibilità per Plug-in controllo codice sorgente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9efe961774ef1939cfc95c2efe9146a59e46bc17
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967464"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: Disabilitare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un utente potrebbero essere visualizzati diversi avvisi di compatibilità durante l'utilizzo di controllo del codice sorgente in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Gli avvisi presentati dipendono dalle funzionalità di plug-in del controllo del codice sorgente e possono essere disabilitati come dettagliate qui.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disabilitare l'avviso: "Per garantire ottimali integrazione del controllo sorgente con Visual Studio..."  
  
-   Impostare la seguente voce del Registro di sistema (se necessario, aggiungere il valore):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001  
  
     Questo avviso viene visualizzato per tutti non[!INCLUDE[vsvss](../includes/vsvss-md.md)] plug-in.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disabilitare l'avviso: "Il provider del controllo del codice sorgente installato non supporta tutte le funzionalità..."  
  
-   Impostare i valori del Registro di due sistema seguenti (se necessario, aggiungere i valori):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001  
  
     Questo avviso viene visualizzato se il plug-in del controllo del codice sorgente non supportano in modo esplicito reentrancy per più progetti (vale a dire, se è possibile verificare in un solo file e al progetto in un momento).  
  
     È consigliabile per il supporto della reentrancy (`SCC_CAP_REENTRANT` funzionalità); verrà rimuovere questo avviso. Tuttavia, se questo supporto non è possibile, è possono impostare queste voci del Registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Flag di funzionalità](../extensibility/capability-flags.md)
