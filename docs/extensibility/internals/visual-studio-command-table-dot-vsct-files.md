---
title: Visual Studio Tabella dei comandi (. Vsct) Files | Microsoft Docs
description: Informazioni sui file di configurazione della tabella dei comandi, ovvero file di testo che descrivono il set di comandi contenuti in un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e7f85d60d12fcb4cd04aacb9281e8bbb9d973e6dfe2e5732379c6387fdabf173
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375455"
---
# <a name="visual-studio-command-table-vsct-files"></a>File Visual Studio Command Table (con estensione vsct)
Un file di configurazione della tabella dei comandi è un file di testo che descrive il set di comandi contenuti in un VSPackage. Il compilatore della tabella dei comandi (VSCT) compila i file di configurazione basati su XML (file con estensione vsct) in file di output della tabella dei comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] binari (con estensione cto). I file CTO risultanti sono gli stessi creati usando il compilatore della tabella dei comandi (CTC) per compilare i file di configurazione con estensione ctc. Tuttavia, i file con estensione vsct basati su XML presentano alcuni vantaggi, ad esempio un editor XML e IntelliSense XML.

 Per altre informazioni sulla sintassi e la semantica dei file con estensione vsct, vedere [Progettazione di una tabella di comandi XML (. Vsct) Files](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Contenuto della sezione
 [Progettazione di file (con estensione vsct) della tabella di comandi XML](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Viene descritto come progettare file con estensione vsct.

 [Procedura: Creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Confronta i metodi per la creazione di un file con estensione vsct. Viene descritto il processo di creazione manuale di un nuovo file con estensione vsct.

## <a name="related-sections"></a>Sezioni correlate
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Fornisce informazioni dettagliate su ogni sezione del file di configurazione XML della tabella dei comandi.

 [Configurazione tabella comandi (. Ctc) File](/previous-versions/bb165153(v=vs.100)) Presenta una panoramica del formato di file CTC deprecato.

 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Descrive la specifica del formato della tabella dei comandi.

 [Risorse nei pacchetti VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Viene descritto come usare le risorse gestite e non gestite nei pacchetti VSPackage gestiti.

 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.