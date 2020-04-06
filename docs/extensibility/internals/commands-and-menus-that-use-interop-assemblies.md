---
title: Comandi e menu che utilizzano gli assembly di interoperabilità . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709494"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandi e menu che utilizzano assembly di interoperabilitàCommands and menus that use Interop assemblies
Un pacchetto VSPackage che implementa i comandi di menu e barra degli strumenti utilizzando gli assembly di interoperabilità deve:A VSPackage that implements menu and toolbar commands by using Interop assemblies must:

- Informare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'ambiente di sviluppo integrato (IDE) sui comandi supportati e se sono attualmente abilitati.

- Rispettare le regole (contratto) per la gestione dei comandi.

- Implementare in modo esplicito la gestione dei comandi utilizzando l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

  Nella sezione seguente viene descritto come eseguire queste attività.

## <a name="in-this-section"></a>Contenuto della sezione
- [Determinare lo stato dei comandi utilizzando gli assembly di interoperabilitàDetermine command status by using Interop assemblies](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Viene descritto come un VSPackage notifica l'IDE sui comandi che supporta e se sono attualmente abilitati.

- [Contratti di comando negli assembly di interoperabilitàCommand contracts in Interop assemblies](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Fornisce una definizione del contratto di comando di base utilizzato da tutti i package VS che implementano i comandi utilizzando gli assembly di interoperabilità.

- [Implementazione dei comandi](../../extensibility/internals/command-implementation.md)

 Fornisce una panoramica di come un VSPackage implementa un comando.

- [Registrare i gestori dei comandi dell'assembly di interoperabilità Register Interop assembly command handlers](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Descrive le voci del Registro di sistema necessarie per notificare l'IDE che un VSPackage fornisce un gestore di comando.

## <a name="related-sections"></a>Sezioni correlate
- [Disponibilità dei comandi](../../extensibility/internals/command-availability.md)

 Vengono descritti i criteri utilizzati dall'IDE per determinare quali comandi VSPackage sono disponibili e quale oggetto li gestisce.

- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Fornisce informazioni dettagliate su come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creare un'interfaccia utente che usa il supporto dei comandi.

- [Routing dei comandi nei pacchetti VSPackageCommand routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Panoramica del processo utilizzato per correlare un oggetto con la richiesta di comando corretta.
