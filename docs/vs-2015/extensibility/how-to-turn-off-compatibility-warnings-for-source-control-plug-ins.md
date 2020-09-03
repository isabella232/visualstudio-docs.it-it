---
title: 'Procedura: disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente | Microsoft Docs'
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
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204056"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: Disabilitare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un utente può visualizzare diversi avvisi di compatibilità quando utilizza il controllo del codice sorgente in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Gli avvisi presentati dipendono dalle funzionalità del plug-in del controllo del codice sorgente e possono essere disabilitati come descritto in dettaglio qui.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disabilitare l'avviso: "per garantire l'integrazione ottimale del controllo del codice sorgente con Visual Studio..."  
  
- Impostare la voce del registro di sistema seguente (aggiungendo il valore, se necessario):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Questo avviso viene visualizzato per tutti i [!INCLUDE[vsvss](../includes/vsvss-md.md)] plug-in.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disabilitare l'avviso: "il provider del controllo del codice sorgente installato non supporta tutte le funzionalità..."  
  
- Impostare i due valori del registro di sistema seguenti (aggiungendo i valori se necessario):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Questo avviso viene visualizzato se il plug-in del controllo del codice sorgente non supporta in modo esplicito la rientranza per più progetti, ovvero se può archiviare solo un file e un progetto alla volta.  
  
     È preferibile supportare la rientranza ( `SCC_CAP_REENTRANT` funzionalità); in questo modo verrà rimosso questo avviso. Tuttavia, se il supporto non è possibile, è possibile impostare queste voci del registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Flag di funzionalità](../extensibility/capability-flags.md)
