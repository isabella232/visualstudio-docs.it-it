---
title: Architettura VSPackage del controllo del codice sorgente | Microsoft Docs
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
ms.openlocfilehash: 9484aabd0080b0a44d75a8a5f6d90d9217d74b8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723356"
---
# <a name="source-control-vspackage-architecture"></a>Architettura dei pacchetti VSPackage di controllo del codice sorgente
Un pacchetto di controllo del codice sorgente è un VSPackage che usa i servizi forniti dall'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. In restituzione, un pacchetto di controllo del codice sorgente fornisce le funzionalità come servizio di controllo del codice sorgente. Inoltre, un pacchetto di controllo del codice sorgente è un'alternativa più versatile rispetto a un plug-in del controllo del codice sorgente per l'integrazione del controllo del codice sorgente in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Un plug-in del controllo del codice sorgente che implementa l'API del plug-in del controllo del codice sorgente è rispettato da un contratto rigoroso. Ad esempio, un plug-in non può sostituire l'interfaccia utente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] predefinita. Inoltre, l'API del plug-in del controllo del codice sorgente non consente a un plug-in di implementare il proprio modello di controllo del codice sorgente. Un pacchetto di controllo del codice sorgente, tuttavia, si limita a entrambe le limitazioni. Un pacchetto di controllo del codice sorgente ha il controllo completo sull'esperienza del controllo del codice sorgente di un utente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Inoltre, un pacchetto di controllo del codice sorgente può utilizzare la propria logica e il proprio modello di controllo del codice sorgente e può definire tutte le interfacce utente correlate al controllo del codice sorgente.

## <a name="source-control-package-components"></a>Componenti del pacchetto di controllo del codice sorgente
 Come illustrato nel diagramma dell'architettura, un componente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] denominato stub del controllo del codice sorgente è un VSPackage che integra un pacchetto di controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Lo stub del controllo del codice sorgente gestisce le seguenti attività.

- Fornisce l'interfaccia utente comune necessaria per la registrazione del pacchetto del controllo del codice sorgente.

- Carica un pacchetto di controllo del codice sorgente.

- Imposta un pacchetto di controllo del codice sorgente come attivo/inattivo.

  Lo stub del controllo del codice sorgente Cerca il servizio attivo per il pacchetto del controllo del codice sorgente e instrada tutte le chiamate al servizio in ingresso dall'IDE al pacchetto.

  Il pacchetto dell'adattatore del controllo del codice sorgente è un pacchetto di controllo del codice sorgente speciale fornito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Questo pacchetto è il componente centrale per supportare i plug-in del controllo del codice sorgente basati sull'API del plug-in del controllo del codice sorgente. Quando un plug-in del controllo del codice sorgente è il plug-in attivo, lo stub del controllo del codice sorgente invia gli eventi al pacchetto dell'adattatore del controllo del codice sorgente. Il pacchetto dell'adattatore del controllo del codice sorgente comunica a sua volta con il plug-in del controllo del codice sorgente tramite l'API del plug-in del controllo del codice sorgente e fornisce anche un'interfaccia utente predefinita comune per tutti i plug-in del controllo del codice sorgente.

  Quando un pacchetto di controllo del codice sorgente è il pacchetto attivo, d'altra parte, lo stub del controllo del codice sorgente comunica direttamente con il pacchetto usando le interfacce del pacchetto del controllo del codice sorgente [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Il pacchetto del controllo del codice sorgente è responsabile dell'hosting della propria interfaccia utente del controllo del codice sorgente.

  ![Rappresentazione grafica dell'architettura del controllo del codice sorgente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Per un pacchetto di controllo del codice sorgente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non fornisce codice del controllo del codice sorgente o un'API per l'integrazione. Questo approccio viene invece illustrato in [creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md) in cui il plug-in del controllo del codice sorgente deve implementare un set rigido di funzioni e callback.

  Analogamente a qualsiasi VSPackage, un pacchetto di controllo del codice sorgente è un oggetto COM che può essere creato utilizzando `CoCreateInstance`. Il pacchetto VSPackage rende disponibile l'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Quando un'istanza di è stata creata, un pacchetto VSPackage riceve un puntatore del sito e un'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> che fornisce all'accesso VSPackage i servizi e le interfacce disponibili nell'IDE.

  La scrittura di un pacchetto di controllo del codice sorgente basato su VSPackage richiede un'esperienza di programmazione più avanzata rispetto alla scrittura di un plug-in basato su API del plug-in del controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)