---
title: Creazione di un VSPackage di controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 259273eee51c74eb7cb5ca4534db9bc575fd1758
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345483"
---
# <a name="create-a-source-control-vspackage"></a>Creare un pacchetto VSPackage di controllo di origine
Questa documentazione include collegamenti a panoramica dell'architettura di un pacchetto controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'API definita per le interfacce da implementare e i servizi devono essere usati e un esempio che illustra una semplice origine controllare l'implementazione del pacchetto.

 Con un controllo del codice sorgente VSPackage, è possibile creare un percorso di una profonda integrazione di controllo del codice sorgente per l'integrazione con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Consente di ignorare il controllo del codice sorgente predefinite dell'interfaccia utente ospitato dal pacchetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]rispondere alle richieste di controllo di origine del sistema del progetto e interagirvi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti, ad esempio **Esplora soluzioni**. Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] conferisce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opera in partnership con un meccanismo per creare un pacchetto VSPackage che può essere integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando un modello di servizio.

## <a name="in-this-section"></a>Contenuto della sezione
- [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Viene illustrato il pacchetto di controllo di origine, che è un'alternativa più avanzata per il plug-in per l'implementazione di funzionalità di controllo codice sorgente nel controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Viene presentato un diagramma e illustra i componenti di un pacchetto controllo del codice sorgente.

- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)

 Descrive le varie caratteristiche di un pacchetto controllo del codice sorgente.

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Descrive la struttura del pacchetto VSPackage che un pacchetto controllo del codice sorgente deve implementare per l'integrazione completa.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un controllo del codice sorgente del plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Viene illustrato come creare un controllo del codice sorgente del plug-in che fornisce controllo del codice sorgente nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo origine (UI).

- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)

 Vengono illustrate le opzioni per l'implementazione del controllo del codice sorgente come una funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
