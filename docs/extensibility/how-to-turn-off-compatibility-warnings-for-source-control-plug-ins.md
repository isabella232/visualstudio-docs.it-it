---
title: Disattivare gli avvisi per i plug-in del controllo del codice sorgente
description: Un utente può visualizzare diversi avvisi di compatibilità quando usa il controllo del codice sorgente Visual Studio. Informazioni su come disabilitare questi avvisi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc460038971786c2d9d29c30861ada31dbda92d2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050286"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: Disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente

Un utente può visualizzare diversi avvisi di compatibilità quando usa il controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Gli avvisi presentati dipendono dalle funzionalità del plug-in del controllo del codice sorgente e possono essere disabilitati come descritto in dettaglio qui.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disabilitare l'avviso: "Per garantire un'integrazione ottimale del controllo del codice sorgente con Visual Studio"

- Impostare la voce del Registro di sistema seguente aggiungendo il valore, se necessario:

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Questo avviso viene visualizzato per tutti i [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-in non.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disabilitare l'avviso: "Il provider del controllo del codice sorgente installato non supporta tutte le funzionalità"

- Impostare i due valori del Registro di sistema seguenti (aggiungendo i valori se necessario):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Questo avviso viene visualizzato se il plug-in del controllo del codice sorgente non supporta in modo esplicito la reentrancy per più progetti, ovvero se è in grado di archiviare un solo file e progetto alla volta.

     È meglio supportare la reentrancy `SCC_CAP_REENTRANT` (funzionalità). In questo modo questo avviso verrà rimosso. Tuttavia, se questo supporto non è possibile, è possibile impostare queste voci del Registro di sistema.

## <a name="see-also"></a>Vedi anche

- [Flag di funzionalità](../extensibility/capability-flags.md)
