---
title: Creazione di un pacchetto VSPackage del controllo del | Microsoft Docs
description: Informazioni su come creare un VSPackage del controllo del codice sorgente che crea un percorso di integrazione completo per il controllo del codice sorgente da integrare con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 151a2b7fcf648311a986db88d6e4c7df00487bbe682c760cfe05a51a45173e51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238619"
---
# <a name="create-a-source-control-vspackage"></a>Creare un pacchetto VSPackage del controllo del codice sorgente
Questa documentazione include collegamenti alla panoramica dell'architettura di un pacchetto di controllo del codice sorgente integrato con , all'API definita dalle interfacce da implementazione e ai servizi da utilizzare e a un esempio che illustra una semplice implementazione del pacchetto di controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente.

 Con un pacchetto VSPackage del controllo del codice sorgente, è possibile creare un percorso di integrazione completo per il controllo del codice sorgente da integrare con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Consente al pacchetto di ignorare l'interfaccia utente predefinita del controllo del codice sorgente ospitata da , rispondere alle richieste di controllo del codice sorgente dal sistema del progetto e interagire con componenti come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Esplora soluzioni**. offre ai partner un meccanismo per creare un VSPackage che [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] può essere integrato con usando un modello di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servizio.

## <a name="in-this-section"></a>Contenuto della sezione
- [Operazioni preliminari](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Viene illustrato il pacchetto di controllo del codice sorgente, che rappresenta un'alternativa più avanzata al plug-in del controllo del codice sorgente per l'implementazione delle funzionalità di controllo del codice sorgente in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Presenta un diagramma e illustra i componenti di un pacchetto di controllo del codice sorgente.

- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)

 Vengono descritte le varie funzionalità di un pacchetto di controllo del codice sorgente.

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Descrive la struttura del pacchetto VSPackage che un pacchetto di controllo del codice sorgente deve implementare per una completa integrazione.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Viene illustrato come creare un plug-in del controllo del codice sorgente che fornisce funzionalità di controllo del codice sorgente nell'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente del controllo del codice sorgente.

- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)

 Vengono illustrate le opzioni per l'implementazione del controllo del codice sorgente come funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
