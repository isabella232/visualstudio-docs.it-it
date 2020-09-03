---
title: Disabilitare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710717"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente
Un utente può visualizzare diversi avvisi di compatibilità quando utilizza il controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Gli avvisi presentati dipendono dalle funzionalità del plug-in del controllo del codice sorgente e possono essere disabilitati come descritto in dettaglio qui.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disabilitare l'avviso: "per garantire l'integrazione ottimale del controllo del codice sorgente con Visual Studio"

- Impostare la voce del registro di sistema seguente (aggiungendo il valore, se necessario):

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Questo avviso viene visualizzato per tutti i [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-in.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disabilitare l'avviso: "il provider del controllo del codice sorgente installato non supporta tutte le funzionalità"

- Impostare i due valori del registro di sistema seguenti (aggiungendo i valori se necessario):

     **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Questo avviso viene visualizzato se il plug-in del controllo del codice sorgente non supporta in modo esplicito la rientranza per più progetti, ovvero se può archiviare solo un file e un progetto alla volta.

     È preferibile supportare la rientranza ( `SCC_CAP_REENTRANT` funzionalità); in questo modo verrà rimosso questo avviso. Tuttavia, se il supporto non è possibile, è possibile impostare queste voci del registro di sistema.

## <a name="see-also"></a>Vedere anche
- [Flag funzionalità](../extensibility/capability-flags.md)
