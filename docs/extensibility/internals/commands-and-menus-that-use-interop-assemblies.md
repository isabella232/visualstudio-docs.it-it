---
title: Comandi e menu che usano assembly di interoperabilità | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709494"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandi e menu che usano assembly di interoperabilità
Un pacchetto VSPackage che implementa i comandi di menu e barre degli strumenti usando gli assembly di interoperabilità deve:

- Informare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) sui comandi supportati e se sono attualmente abilitati.

- Rispettare le regole (contratto) per la gestione dei comandi.

- Implementare in modo esplicito la gestione dei comandi usando l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia o.

  Nella sezione seguente viene descritto come eseguire queste attività.

## <a name="in-this-section"></a>Contenuto della sezione
- [Determinare lo stato del comando tramite assembly di interoperabilità](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Descrive in che modo un pacchetto VSPackage notifica all'IDE quali sono i comandi supportati e se sono attualmente abilitati.

- [Contratti di comando negli assembly di interoperabilità](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Fornisce una definizione del contratto di comando di base usato da tutti i VSPackage che implementano i comandi usando gli assembly di interoperabilità.

- [Implementazione del comando](../../extensibility/internals/command-implementation.md)

 Viene fornita una panoramica del modo in cui un VSPackage implementa un comando.

- [Registrare i gestori di comandi di assembly di interoperabilità](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Descrive le voci del registro di sistema necessarie per notificare all'IDE che un pacchetto VSPackage fornisce un gestore comando.

## <a name="related-sections"></a>Sezioni correlate
- [Disponibilità comando](../../extensibility/internals/command-availability.md)

 Vengono descritti i criteri utilizzati dall'IDE per determinare quali comandi VSPackage sono disponibili e quali oggetti li gestisce.

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Fornisce informazioni dettagliate su come creare un'interfaccia utente che utilizza il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporto dei comandi.

- [Routing di comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Panoramica del processo utilizzato per correlare un oggetto con la richiesta di comando corretta.
