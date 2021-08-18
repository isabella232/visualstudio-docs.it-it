---
title: Comandi e menu che usano assembly di interoperabilità | Microsoft Docs
description: Informazioni sulle attività che devono essere completate durante l'implementazione di comandi di menu e barra degli strumenti in un VSPackage tramite assembly di interoperabilità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 12f6cd61eb7e5f3e6bc96722f8d2ad8f29f5ee97
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124711"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandi e menu che usano assembly di interoperabilità
Un VSPackage che implementa i comandi di menu e barra degli strumenti tramite assembly di interoperabilità deve:

- Informare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'ambiente di sviluppo integrato (IDE) sui comandi supportati e se sono attualmente abilitati.

- Rispettare le regole (contratto) per la gestione dei comandi.

- Implementare in modo esplicito la gestione dei comandi usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

  La sezione seguente descrive come eseguire queste attività.

## <a name="in-this-section"></a>Contenuto della sezione
- [Determinare lo stato del comando tramite assembly di interoperabilità](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Descrive in che modo un VSPackage notifica all'IDE quali comandi supporta e se sono attualmente abilitati.

- [Contratti di comando negli assembly di interoperabilità](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Fornisce una definizione del contratto di comando di base usato da tutti i pacchetti VSPackage che implementano i comandi usando assembly di interoperabilità.

- [Implementazione del comando](../../extensibility/internals/command-implementation.md)

 Fornisce una panoramica del modo in cui un VSPackage implementa un comando.

- [Registrare i gestori dei comandi dell'assembly di interoperabilità](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Descrive le voci del Registro di sistema necessarie per notificare all'IDE che un pacchetto VSPackage fornisce un gestore comandi.

## <a name="related-sections"></a>Sezioni correlate
- [Disponibilità dei comandi](../../extensibility/internals/command-availability.md)

 Descrive i criteri usati dall'IDE per determinare quali comandi VSPackage sono disponibili e quale oggetto li gestisce.

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Fornisce informazioni dettagliate su come creare un'interfaccia utente che usa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporto dei comandi.

- [Routing dei comandi in VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Panoramica del processo usato per correlare un oggetto con la richiesta di comando corretta.
