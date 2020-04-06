---
title: Informazioni di base sull'integrazione con il controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705241"
---
# <a name="source-control-integration-essentials"></a>Nozioni fondamentali sull'integrazione del controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due tipi di integrazione del controllo del codice sorgente: un plug-in del controllo del codice sorgente che fornisce funzionalità di base e viene compilato utilizzando l'API del plug-in del controllo del codice sorgente (precedentemente noto come l'API MSSCCI) e una soluzione di integrazione del controllo del codice sorgente basata su VSPackage che fornisce funzionalità più affidabili.

## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente
 Un plug-in del controllo del codice sorgente viene scritto come una DLL che implementa l'API del plug-in del controllo del codice sorgente. La funzionalità di registrazione e integrazione del controllo del codice sorgente viene fornita tramite l'API. Questo approccio è più facile da implementare rispetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a un controllo del codice sorgente VSPackage e utilizza l'interfaccia utente (UI) per la maggior parte delle operazioni di controllo del codice sorgente.

 Per implementare un plug-in del controllo del codice sorgente utilizzando l'API plug-in controllo del codice sorgente, attenersi alla seguente procedura:

1. Creare una DLL che implementa le funzioni specificate nei [plug-in](../../extensibility/source-control-plug-ins.md)del controllo del codice sorgente .

2. Registrare la DLL creando le voci del Registro di sistema appropriate, come descritto in [Procedura: installare un plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)del controllo del codice sorgente .

3. Creare un'interfaccia utente di supporto e visualizzarlo quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiesto dal pacchetto dell'adattatore del controllo del codice sorgente (il componente che gestisce la funzionalità del controllo del codice sorgente tramite i plug-in del controllo del codice sorgente).

   Per ulteriori informazioni, vedere [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Controllo del codice sorgente VSPackage
 Un controllo del codice sorgente VSPackage implementazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente di sviluppare una sostituzione personalizzata per l'interfaccia utente del controllo del codice sorgente. Questo approccio fornisce il controllo completo sull'integrazione del controllo del codice sorgente, ma richiede di fornire gli elementi dell'interfaccia utente e implementare le interfacce del controllo del codice sorgente che altrimenti verrebbero fornite nell'approccio del plug-in.

 Per implementare un controllo del codice sorgente VSPackage, è necessario:To implement a source control VSPackage, you must:

1. Creare e registrare il proprio controllo del codice sorgente VSPackage, come descritto in [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Sostituire l'interfaccia utente predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata. Vedere [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Specificare i glifi da utilizzare e gestire gli eventi del glifo di **Esplora soluzioni.** Consultate [Controllo glifi.](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Gestire gli eventi Modifica query e Salvataggio query, come illustrato in Salvataggio query di [modifica query](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Per ulteriori informazioni, vedere [creazione di un controllo del codice sorgente VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica](../../extensibility/internals/source-control-integration-overview.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
