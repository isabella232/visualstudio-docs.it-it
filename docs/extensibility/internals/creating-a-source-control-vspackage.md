---
title: Creazione di un pacchetto VSPackage di controllo del codice sorgente | Microsoft Docs
description: Informazioni su come creare un pacchetto VSPackage del controllo del codice sorgente per creare un percorso di integrazione completa per l'integrazione del controllo del codice sorgente con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9be8b97b3e37a224b12781e66543f7ab126f2c6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958531"
---
# <a name="create-a-source-control-vspackage"></a>Creare un pacchetto VSPackage del controllo del codice sorgente
Questa documentazione include collegamenti alla panoramica dell'architettura di un pacchetto di controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , l'API definita dalle interfacce da implementare e i servizi da utilizzare e un esempio che illustra una semplice implementazione di un pacchetto di controllo del codice sorgente.

 Con un VSPackage del controllo del codice sorgente, è possibile creare un percorso di integrazione completa per l'integrazione del controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Consente al pacchetto di ignorare l'interfaccia utente predefinita del controllo del codice sorgente ospitata da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , rispondere alle richieste di controllo del codice sorgente dal sistema del progetto e interagire con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti come **Esplora soluzioni**. Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] offre ai [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partner un meccanismo per creare un pacchetto VSPackage che può essere integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un modello di servizio.

## <a name="in-this-section"></a>Contenuto della sezione
- [Operazioni preliminari](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Viene illustrato il pacchetto del controllo del codice sorgente, che rappresenta un'alternativa più avanzata al plug-in del controllo del codice sorgente per l'implementazione delle funzionalità di controllo del codice sorgente in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Viene presentato un diagramma e vengono illustrati i componenti di un pacchetto di controllo del codice sorgente.

- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)

 Descrive le varie funzionalità di un pacchetto di controllo del codice sorgente.

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Descrive la struttura del pacchetto VSPackage che un pacchetto del controllo del codice sorgente deve implementare per l'integrazione completa.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Viene illustrato come creare un plug-in del controllo del codice sorgente che fornisce funzionalità di controllo del codice sorgente nell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente.

- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)

 Vengono illustrate le opzioni per implementare il controllo del codice sorgente come funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
