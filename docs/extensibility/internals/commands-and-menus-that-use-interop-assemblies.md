---
title: I comandi e menu che usano assembly di interoperabilità | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2212d9eb38487bf824fd8df3c497d9f256379c10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907807"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>I comandi e menu che usano assembly di interoperabilità
Un pacchetto VSPackage che implementa i comandi di menu e barra degli strumenti usando assembly di interoperabilità deve:  
  
- Informare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) sui comandi supportati e se sono attualmente abilitati.  
  
- Rispettare le regole (contratto) per la gestione dei comandi.  
  
- Implementare in modo esplicito la gestione dei comandi usando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia.  
  
  La sezione seguente descrive come eseguire queste attività.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Determinare lo stato del comando con gli assembly di interoperabilità](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Viene descritto come un pacchetto VSPackage notifica all'IDE sulle quali comandi supportati e se sono attualmente abilitati.  
  
 [Contratti dei comandi negli assembly di interoperabilità](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fornisce una definizione del contratto di comando di base usato da tutti i pacchetti VSPackage che implementa i comandi tramite assembly di interoperabilità.
  
 [Implementazione del comando](../../extensibility/internals/command-implementation.md)  
 Fornisce una panoramica del modo in cui un pacchetto VSPackage implementa un comando.  
  
 [Registrare i gestori di comando di assembly di interoperabilità](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Descrive le voci del Registro di sistema necessarie per inviare una notifica dell'IDE che un pacchetto VSPackage fornisce un gestore comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Disponibilità dei comandi](../../extensibility/internals/command-availability.md)  
 Descrive i criteri usati dall'IDE per determinare quali comandi VSPackage sono disponibili e l'oggetto che li gestisce.  
  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Vengono fornite informazioni dettagliate su come creare un'interfaccia utente che usa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando supporto.  
  
 [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Panoramica del processo utilizzato per correlare un oggetto con la richiesta corretta del comando.