---
title: Architettura VSPackage del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705075"
---
# <a name="source-control-vspackage-architecture"></a>Architettura dei pacchetti VSPackage di controllo del codice sorgente
Un pacchetto di controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è un pacchetto VSPackage che utilizza i servizi forniti dall'IDE. In cambio, un pacchetto di controllo del codice sorgente fornisce la funzionalità come servizio di controllo del codice sorgente. Inoltre, un pacchetto di controllo del codice sorgente è un'alternativa più versatile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]rispetto a un plug-in del controllo del codice sorgente per l'integrazione del controllo del codice sorgente in .

 Un plug-in del controllo del codice sorgente che implementa l'API del plug-in del controllo del codice sorgente rispetta un contratto rigoroso. Ad esempio, un plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non può sostituire l'interfaccia utente predefinita. Inoltre, l'API plug-in del controllo del codice sorgente non consente a un plug-in di implementare il proprio modello di controllo del codice sorgente. Un pacchetto di controllo del codice sorgente, tuttavia, supera entrambe queste limitazioni. Un pacchetto di controllo del codice sorgente ha [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il controllo completo sull'esperienza del controllo del codice sorgente di un utente. Inoltre, un pacchetto di controllo del codice sorgente può utilizzare il proprio modello di controllo del codice sorgente e la logica e può definire tutte le interfacce utente correlate al controllo del codice sorgente.

## <a name="source-control-package-components"></a>Componenti del pacchetto di controllo del codice sorgenteSource-Control Package Components
 Come illustrato nel diagramma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'architettura, un componente denominato Stub del controllo del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]codice sorgente è un pacchetto VSPackage che integra un pacchetto di controllo del codice sorgente con .

 Stub del controllo del codice sorgente gestisce le attività seguenti.

- Fornisce l'interfaccia utente comune necessaria per la registrazione del pacchetto del controllo del codice sorgente.

- Carica un pacchetto di controllo del codice sorgente.

- Imposta un pacchetto di controllo del codice sorgente come attivo/inattivo.

  Stub del controllo del codice sorgente cerca il servizio attivo per il pacchetto di controllo del codice sorgente e instrada tutte le chiamate di servizio in ingresso dall'IDE a tale pacchetto.

  Il pacchetto dell'adattatore del controllo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del codice sorgente è un pacchetto speciale del controllo del codice sorgente che fornisce. Questo pacchetto è il componente centrale per il supporto dei plug-in del controllo del codice sorgente basati sull'API del plug-in del controllo del codice sorgente. Quando un plug-in del controllo del codice sorgente è il plug-in attivo, lo Stub del controllo del codice sorgente invia i propri eventi al pacchetto dell'adattatore del controllo del codice sorgente. A sua volta, il pacchetto dell'adattatore del controllo del codice sorgente comunica con il plug-in del controllo del codice sorgente utilizzando l'API plug-in del controllo del codice sorgente e fornisce anche un'interfaccia utente predefinita comune per tutti i plug-in del controllo del codice sorgente.

  Quando un pacchetto del controllo del codice sorgente è il pacchetto attivo, d'altra parte, lo Stub del controllo del codice sorgente comunica direttamente con il pacchetto usando le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfacce del pacchetto di controllo del codice sorgente. Il pacchetto del controllo del codice sorgente è responsabile dell'hosting della propria interfaccia utente del controllo del codice sorgente.

  ![Immagine dell'architettura di controllo del codice sorgente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Per un pacchetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controllo del codice sorgente, non fornisce codice del controllo del codice sorgente o un'API per l'integrazione. In contrasto con l'approccio descritto in creazione di [un plug-in controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md) in cui il plug-in controllo del codice sorgente deve implementare un set rigido di funzioni e callback.

  Come qualsiasi VSPackage, un pacchetto di controllo del codice `CoCreateInstance`sorgente è un oggetto COM che può essere creato utilizzando . Il pacchetto VSPackage si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rende disponibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>per l'IDE implementando . Quando un'istanza è stata creata, un VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> riceve un puntatore del sito e un'interfaccia che fornisce l'accesso VSPackage ai servizi e le interfacce disponibili nell'IDE.

  La scrittura di un pacchetto di controllo del codice sorgente basato su VSPackage richiede competenze di programmazione più avanzate rispetto alla scrittura di un plug-in basato sull'API del plug-in del controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Guida introduttiva](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
