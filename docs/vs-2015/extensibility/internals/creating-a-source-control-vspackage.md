---
title: Creazione di un pacchetto VSPackage di controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196961"
---
# <a name="creating-a-source-control-vspackage"></a>Creazione di un pacchetto VSPackage di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa documentazione include collegamenti alla panoramica dell'architettura di un pacchetto di controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , l'API definita dalle interfacce da implementare e i servizi da utilizzare e un esempio che illustra una semplice implementazione di un pacchetto di controllo del codice sorgente.  
  
 Con un VSPackage del controllo del codice sorgente, è possibile creare un percorso di integrazione completa per l'integrazione del controllo del codice sorgente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Consente al pacchetto di ignorare l'interfaccia utente predefinita del controllo del codice sorgente ospitata da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , rispondere alle richieste di controllo del codice sorgente dal sistema del progetto e interagire con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componenti come **Esplora soluzioni**. Il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] offre ai [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] partner un meccanismo per creare un pacchetto VSPackage che può essere integrato con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] un modello di servizio.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Per iniziare](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Viene illustrato il pacchetto del controllo del codice sorgente, che rappresenta un'alternativa più avanzata al plug-in del controllo del codice sorgente per l'implementazione delle funzionalità di controllo del codice sorgente in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Viene presentato un diagramma e vengono illustrati i componenti di un pacchetto di controllo del codice sorgente.  
  
 [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)  
 Descrive le varie funzionalità di un pacchetto di controllo del codice sorgente.  
  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Descrive la struttura del pacchetto VSPackage che un pacchetto del controllo del codice sorgente deve implementare per l'integrazione completa.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un plug-in del controllo del codice sorgente che fornisce funzionalità di controllo del codice sorgente nell' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaccia utente del controllo del codice sorgente.  
  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)  
 Vengono illustrate le opzioni per implementare il controllo del codice sorgente come funzionalità integrata di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
