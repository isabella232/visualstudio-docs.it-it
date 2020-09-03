---
title: Comandi e menu che usano assembly di interoperabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195044"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandi e menu che usano assembly di interoperabilità
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage che implementa i comandi di menu e barre degli strumenti usando gli assembly di interoperabilità deve:  
  
- Informare il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE) sui comandi supportati e se sono attualmente abilitati.  
  
- Rispettare le regole (contratto) per la gestione dei comandi.  
  
- Implementare in modo esplicito la gestione dei comandi usando l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia o.  
  
  Di seguito viene descritto come eseguire queste attività.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Determinazione dello stato dei comandi in base agli assembly di interoperabilità](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Descrive in che modo un pacchetto VSPackage notifica all'IDE quali sono i comandi supportati e se sono attualmente abilitati.  
  
 [Contratti dei comandi negli assembly di interoperabilità](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fornisce una definizione del contratto di comando di base usato da tutti i VSPackage che implementano i comandi usando gli assembly di interoperabilità  
  
 [Implementazione](../../extensibility/internals/command-implementation.md)  
 Viene fornita una panoramica del modo in cui un VSPackage implementa un comando.  
  
 [Registrazione dei gestori dei comandi negli assembly di interoperabilità](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Descrive le voci del registro di sistema necessarie per notificare all'IDE che un pacchetto VSPackage fornisce un gestore comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Disponibilità](../../extensibility/internals/command-availability.md)  
 Vengono descritti i criteri utilizzati dall'IDE per determinare quali comandi VSPackage sono disponibili e quali oggetti li gestisce.  
  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Fornisce informazioni dettagliate su come creare un'interfaccia utente che utilizza il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporto dei comandi.  
  
 [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Panoramica del processo utilizzato per correlare un oggetto con la richiesta di comando corretta.
