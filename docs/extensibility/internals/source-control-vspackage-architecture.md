---
title: Architettura VSPackage del controllo del codice sorgente | Microsoft Docs
description: Informazioni sull'architettura di un pacchetto di controllo del codice sorgente, ovvero un pacchetto VSPackage che fornisce funzionalità per Visual Studio come servizio di controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 35bf749c20af958350a92159844583e007e09fd6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159035"
---
# <a name="source-control-vspackage-architecture"></a>Architettura dei pacchetti VSPackage di controllo del codice sorgente
Un pacchetto di controllo del codice sorgente è un VSPackage che usa i servizi forniti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dall'IDE. In cambio, un pacchetto di controllo del codice sorgente fornisce la relativa funzionalità come servizio di controllo del codice sorgente. Inoltre, un pacchetto di controllo del codice sorgente è un'alternativa più versatile rispetto a un plug-in di controllo del codice sorgente per l'integrazione del controllo del codice sorgente in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Un plug-in di controllo del codice sorgente che implementa l'API plug-in del controllo del codice sorgente è associato a un contratto rigoroso. Ad esempio, un plug-in non può sostituire l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente predefinita. Inoltre, l'API plug-in del controllo del codice sorgente non consente a un plug-in di implementare il proprio modello di controllo del codice sorgente. Un pacchetto di controllo del codice sorgente, tuttavia, supera entrambe queste limitazioni. Un pacchetto di controllo del codice sorgente ha il controllo completo sull'esperienza di controllo del codice sorgente di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente. Inoltre, un pacchetto di controllo del codice sorgente può usare il proprio modello e logica di controllo del codice sorgente e può definire tutte le interfacce utente correlate al controllo del codice sorgente.

## <a name="source-control-package-components"></a>Source-Control componenti del pacchetto
 Come illustrato nel diagramma dell'architettura, un componente denominato stub del controllo del codice sorgente è un vspackage che integra un pacchetto di controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Lo stub del controllo del codice sorgente gestisce le attività seguenti.

- Fornisce l'interfaccia utente comune necessaria per la registrazione del pacchetto del controllo del codice sorgente.

- Carica un pacchetto di controllo del codice sorgente.

- Imposta un pacchetto di controllo del codice sorgente come attivo/inattivo.

  Lo stub del controllo del codice sorgente cerca il servizio attivo per il pacchetto di controllo del codice sorgente e instrada tutte le chiamate al servizio in ingresso dall'IDE a tale pacchetto.

  Il pacchetto dell'adattatore del controllo del codice sorgente è uno speciale pacchetto di controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente che fornisce. Questo pacchetto è il componente centrale per il supporto dei plug-in del controllo del codice sorgente basati sull'API plug-in del controllo del codice sorgente. Quando un plug-in del controllo del codice sorgente è il plug-in attivo, lo stub del controllo del codice sorgente invia i relativi eventi al pacchetto dell'adattatore del controllo del codice sorgente. A sua volta, il pacchetto dell'adattatore del controllo del codice sorgente comunica con il plug-in del controllo del codice sorgente usando l'API plug-in del controllo del codice sorgente e fornisce anche un'interfaccia utente predefinita comune per tutti i plug-in del controllo del codice sorgente.

  Quando un pacchetto di controllo del codice sorgente è il pacchetto attivo, d'altra parte, lo stub del controllo del codice sorgente comunica direttamente con il pacchetto usando le interfacce Source-Control [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] package. Il pacchetto di controllo del codice sorgente è responsabile dell'hosting della propria interfaccia utente del controllo del codice sorgente.

  ![Immagine dell'architettura di controllo del codice sorgente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Per un pacchetto di controllo del codice sorgente, non fornisce codice di controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente o un'API per l'integrazione. A differenza dell'approccio descritto in Creazione di un plug-in di controllo del codice sorgente in cui il [plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md) del controllo del codice sorgente deve implementare un set rigido di funzioni e callback.

  Come qualsiasi VSPackage, un pacchetto di controllo del codice sorgente è un oggetto COM che può essere creato usando `CoCreateInstance` . Il pacchetto VSPackage si rende disponibile per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Dopo la creazione di un'istanza, un vspackage riceve un puntatore al sito e un'interfaccia che fornisce al pacchetto VSPackage l'accesso ai servizi e alle interfacce disponibili <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> nell'IDE.

  La scrittura di un pacchetto di controllo del codice sorgente basato su VSPackage richiede competenze di programmazione più avanzate rispetto alla scrittura di un plug-in basato su API del controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Per iniziare](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
