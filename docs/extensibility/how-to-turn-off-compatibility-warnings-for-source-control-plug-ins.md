---
title: Disattivazione degli avvisi di compatibilità per i plug-in del controllo del codice sorgente Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710717"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgenteHow to: Turn compatibility warnings for source control plug-ins
Un utente può visualizzare diversi avvisi di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]compatibilità quando utilizza il controllo del codice sorgente in . Gli avvisi presentati dipendono dalle funzionalità del plug-in del controllo del codice sorgente e possono essere disabilitati come descritto di seguito.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disattivare l'avviso: "Per garantire un'integrazione ottimale del controllo del codice sorgente con Visual Studio"

- Impostare la seguente voce del Registro di sistema (aggiungendo il valore se necessario):

   **HKEY_CURRENT_USER Software Microsoft VisualStudio 8.0 SourceControl DontDisplayCheckDotNETCompatible : dword:00000001**

   Questo avviso viene visualizzato per[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] tutti i plug-in non.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disattivare l'avviso: "Il provider del controllo del codice sorgente installato non supporta tutte le funzionalità"

- Impostare i due valori del Registro di sistema seguenti (aggiungendo i valori se necessario):

     **HKEY_CURRENT_USER Software Microsoft VisualStudio 8.0 SourceControl WarnedOldMSSCCIProvider - dword:00000000**

    **HKEY_CURRENT_USER'indirizzo software Microsoft VisualStudio 8.0SourceControl UseOldSCC - dword:00000001**

     Questo avviso viene visualizzato se il plug-in del controllo del codice sorgente non supporta in modo esplicito la reentrancy per più progetti,vale a dire, se è possibile archiviare un solo file e progetto alla volta.

     È consigliabile supportare la`SCC_CAP_REENTRANT` reentrancy (funzionalità); in questo modo rimuoverà questo avviso. Tuttavia, se questo supporto non è possibile, queste voci del Registro di sistema possono essere impostate.

## <a name="see-also"></a>Vedere anche
- [Flag di capacità](../extensibility/capability-flags.md)
