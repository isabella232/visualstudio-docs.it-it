---
title: Disattivare gli avvisi di compatibilità per Plug-in controllo codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dc8edcb6ee10be8b020424d8f8c247770a98f27
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324801"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: Disattivare gli avvisi di compatibilità per plug-in controllo codice sorgente
Un utente potrebbero essere visualizzati diversi avvisi di compatibilità durante l'utilizzo di controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Gli avvisi presentati dipendono dalle funzionalità di plug-in del controllo del codice sorgente e possono essere disabilitati come dettagliate qui.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disabilitare l'avviso: "Per garantire l'integrazione del controllo codice sorgente ottimale con Visual Studio"

- Impostare la seguente voce del Registro di sistema (se necessario, aggiungere il valore):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Questo avviso viene visualizzato per tutti non[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-in.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disabilitare l'avviso: "Il provider del controllo del codice sorgente installato non supporta tutte le funzionalità"

- Impostare i valori del Registro di due sistema seguenti (se necessario, aggiungere i valori):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Questo avviso viene visualizzato se il plug-in del controllo del codice sorgente non supportano in modo esplicito reentrancy per più progetti (vale a dire, se è possibile verificare in un solo file e al progetto in un momento).

     È consigliabile per il supporto della reentrancy (`SCC_CAP_REENTRANT` funzionalità); verrà rimuovere questo avviso. Tuttavia, se questo supporto non è possibile, è possono impostare queste voci del Registro di sistema.

## <a name="see-also"></a>Vedere anche
- [Flag funzionalità](../extensibility/capability-flags.md)