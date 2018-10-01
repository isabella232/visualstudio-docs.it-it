---
title: Creazione di un VSPackage di controllo del codice sorgente | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e67d21fe906dd6bc2a1da0a7a483ee78aa0fe2db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526423"
---
# <a name="creating-a-source-control-vspackage"></a>Creazione di un pacchetto VSPackage di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creazione di un VSPackage di controllo del codice sorgente](https://docs.microsoft.com/visualstudio/extensibility/internals/creating-a-source-control-vspackage).  
  
Questa documentazione include collegamenti a panoramica dell'architettura di un pacchetto controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l'API definita per le interfacce da implementare e i servizi devono essere usati e un esempio che illustra una semplice origine controllare l'implementazione del pacchetto.  
  
 Con un controllo del codice sorgente VSPackage, è possibile creare un percorso di una profonda integrazione di controllo del codice sorgente per l'integrazione con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Consente di ignorare il controllo del codice sorgente predefinite dell'interfaccia utente ospitato dal pacchetto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]rispondere alle richieste di controllo di origine del sistema del progetto e interagirvi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componenti, ad esempio **Esplora soluzioni**. Il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] conferisce [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] opera in partnership con un meccanismo per creare un pacchetto VSPackage che può essere integrato con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando un modello di servizio.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Viene illustrato il pacchetto di controllo di origine, che è un'alternativa più avanzata per il plug-in per l'implementazione di funzionalità di controllo codice sorgente nel controllo del codice sorgente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Viene presentato un diagramma e illustra i componenti di un pacchetto controllo del codice sorgente.  
  
 [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)  
 Descrive le varie caratteristiche di un pacchetto controllo del codice sorgente.  
  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Descrive la struttura del pacchetto VSPackage che un pacchetto controllo del codice sorgente deve implementare per l'integrazione completa.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un controllo del codice sorgente del plug-in che fornisce controllo del codice sorgente nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaccia utente del controllo origine (UI).  
  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)  
 Vengono illustrate le opzioni per l'implementazione del controllo del codice sorgente come una funzionalità integrata di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

