---
title: Concetti di base sull'integrazione del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcce3d8fdcc1c99c9b91bfebec572033ff3beb1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723471"
---
# <a name="source-control-integration-essentials"></a>Nozioni fondamentali sull'integrazione del controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di integrazione del controllo del codice sorgente: un plug-in del controllo del codice sorgente che fornisce funzionalità di base e viene compilato tramite l'API del plug-in del controllo del codice sorgente (precedentemente nota come API MSSCCI) e una soluzione di integrazione del controllo del codice sorgente basata su VSPackage che fornisce funzionalità più affidabili.

## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente
 Un plug-in del controllo del codice sorgente viene scritto come DLL che implementa l'API del plug-in del controllo del codice sorgente. La funzionalità di integrazione del controllo del codice sorgente e di registrazione viene fornita tramite l'API. Questo approccio è più semplice da implementare rispetto a un pacchetto VSPackage del controllo del codice sorgente e usa l'interfaccia utente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per la maggior parte delle operazioni di controllo del codice sorgente.

 Per implementare un plug-in del controllo del codice sorgente tramite l'API del plug-in del controllo del codice sorgente, attenersi alla seguente procedura:

1. Creare una DLL che implementi le funzioni specificate nei [plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).

2. Registrare la DLL rendendo le voci del registro di sistema appropriate, come descritto in [procedura: installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Creare un'interfaccia utente di supporto e visualizzarla quando richiesto dal pacchetto di adattatori del controllo del codice sorgente (il componente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che gestisce la funzionalità del controllo del codice sorgente tramite i plug-in del controllo del codice sorgente).

   Per ulteriori informazioni, vedere [creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>VSPackage del controllo del codice sorgente
 Un'implementazione di VSPackage del controllo del codice sorgente consente di sviluppare una sostituzione personalizzata per la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente. Questo approccio fornisce il controllo completo sull'integrazione del controllo del codice sorgente, ma è necessario fornire gli elementi dell'interfaccia utente e implementare le interfacce del controllo del codice sorgente che altrimenti verrebbero fornite nell'approccio del plug-in.

 Per implementare un pacchetto VSPackage del controllo del codice sorgente, è necessario:

1. Creare e registrare il pacchetto VSPackage del controllo del codice sorgente, come descritto in [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Sostituire l'interfaccia utente predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata. Vedere [interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Specificare i glifi da usare e gestire **Esplora soluzioni** eventi del glifo. Vedere il [controllo Glyph](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Gestire gli eventi di modifica della query e di salvataggio delle query, come illustrato in [query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Per altre informazioni, vedere [creazione di un pacchetto VSPackage del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica](../../extensibility/internals/source-control-integration-overview.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)