---
title: Architettura di VSPackage di controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c05ae692a364d4e7a81a017d376dd820ade56b73
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322510"
---
# <a name="source-control-vspackage-architecture"></a>Architettura dei pacchetti VSPackage di controllo del codice sorgente
Un pacchetto controllo del codice sorgente è un pacchetto VSPackage che utilizza servizi a cui il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE sono disponibili. In cambio, un pacchetto controllo del codice sorgente fornisce le sue funzionalità come un servizio di controllo del codice sorgente. Inoltre, un pacchetto controllo del codice sorgente è un'alternativa più versatile rispetto a un plug-in per l'integrazione di controllo del codice sorgente nel controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Un controllo del codice sorgente del plug-in che implementa l'API dei plug-in del controllo origine sia supportata da un contratto di tipo strict. Ad esempio, un plug-in non è possibile sostituire il valore predefinito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente (UI). Inoltre, l'API dei plug-in del controllo origine non è abilitato un plug-in implementare il proprio modello di controllo di origine. Un pacchetto controllo del codice sorgente, tuttavia, è possibile superare entrambe queste limitazioni. Un pacchetto controllo del codice sorgente ha il controllo completo l'esperienza di controllo di origine di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente. Inoltre, un pacchetto controllo del codice sorgente è possibile usare il proprio modello di controllo di origine e per la logica e può definire tutte le interfacce utente correlati al controllo origine.

## <a name="source-control-package-components"></a>Componenti del pacchetto controllo del codice sorgente
 Come illustrato nel diagramma dell'architettura, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominato lo Stub di controllo di origine è un pacchetto VSPackage che si integra un pacchetto controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Stub di controllo sorgente gestisce le attività seguenti.

- Fornisce l'interfaccia utente comune che è necessario per la registrazione del pacchetto di controllo del codice sorgente.

- Carica un pacchetto controllo del codice sorgente.

- Imposta un pacchetto controllo del codice sorgente come attivo/inattivo.

  Stub di controllo di origine è simile per il servizio attivo per il pacchetto di controllo del codice sorgente e consente di indirizzare tutte le chiamate in ingresso del servizio dall'IDE di tale pacchetto.

  Il pacchetto di scheda di controllo di origine è un controllo del codice sorgente speciale del pacchetto che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce. Questo pacchetto è il componente centrale per il supporto di origine plug-in del controllo in base l'API dei plug-in del controllo origine. Quando un plug-in del controllo del codice sorgente è attivo del plug-in, lo Stub di controllo di origine invia gli eventi per il pacchetto di scheda di controllo codice sorgente. A sua volta, il pacchetto di scheda di controllo codice sorgente comunica con il plug-in del controllo del codice sorgente mediante l'API dei plug-in del controllo sorgente e fornisce anche un valore predefinito dell'interfaccia utente che è comune per tutti i plug-in controllo codice sorgente.

  Quando un pacchetto controllo del codice sorgente è il pacchetto active, d'altra parte, lo Stub del controllo sorgente comunica direttamente con il pacchetto usando la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfacce pacchetto controllo del codice sorgente. Il pacchetto di controllo del codice sorgente è responsabile dell'hosting di un proprio controllo del codice sorgente dell'interfaccia utente.

  ![Rappresentazione grafica dell'architettura del controllo sorgente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Per un pacchetto controllo del codice sorgente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non fornisce il codice di controllo di origine o a un'API per l'integrazione. Ciò si differenzia l'approccio descritto nella [creazione di un plug-in controllo sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md) in cui il plug-in del controllo del codice sorgente deve implementare un set di funzioni e i callback rigido.

  Come qualsiasi pacchetto VSPackage, un pacchetto controllo del codice sorgente è un oggetto COM che può essere creato usando `CoCreateInstance`. Il pacchetto VSPackage rende disponibile per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Dopo aver creata un'istanza, un pacchetto VSPackage riceve un puntatore di sito e un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia che consente di accedere ai servizi disponibili e interfacce nell'IDE di VSPackage.

  La scrittura di un pacchetto controllo del codice sorgente in base al pacchetto VSPackage richiede competenze di programmazione più avanzate rispetto alla scrittura di un'API dei plug-in del controllo sorgente basate su plug-in.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)