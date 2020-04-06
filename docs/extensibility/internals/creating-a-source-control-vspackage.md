---
title: Creazione di un controllo del codice sorgente VSPackage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709186"
---
# <a name="create-a-source-control-vspackage"></a>Creare un controllo del codice sorgente VSPackageCreate a source control VSPackage
Questa documentazione include collegamenti alla panoramica dell'architettura di un pacchetto di controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'API definita dalle interfacce da implementare e i servizi da utilizzare e un esempio che illustra una semplice implementazione del pacchetto di controllo del codice sorgente.

 Con un controllo del codice sorgente VSPackage, è possibile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]creare un percorso di integrazione approfondita per il controllo del codice sorgente per l'integrazione con . Consente al pacchetto di ignorare l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utente predefinita del controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ospitata da , rispondere alle richieste del controllo del codice sorgente dal sistema del progetto e interagire con componenti quali **Esplora soluzioni**. Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] consente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ai partner con un meccanismo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per creare un pacchetto VSPackage che può integrare con l'utilizzo di un modello di servizio.

## <a name="in-this-section"></a>Contenuto della sezione
- [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Viene illustrato il pacchetto del controllo del codice sorgente, che è un'alternativa più avanzata al plug-in del controllo del codice sorgente per l'implementazione delle funzionalità del controllo del codice sorgente in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)

 Presenta un diagramma e illustra i componenti di un pacchetto di controllo del codice sorgente.

- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)

 Vengono descritte le varie funzionalità di un pacchetto di controllo del codice sorgente.

- [Elementi di design](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Viene descritta la struttura del pacchetto VSPackage che un pacchetto di controllo del codice sorgente deve implementare per l'integrazione completa.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un plug-in del controllo del codice sorgenteCreate a source control plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Viene illustrato come creare un plug-in del controllo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del codice sorgente che fornisce funzionalità di controllo del codice sorgente nell'interfaccia utente del controllo del codice sorgente .UI.

- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)

 Vengono illustrate le opzioni per l'implementazione del controllo del codice sorgente come funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
