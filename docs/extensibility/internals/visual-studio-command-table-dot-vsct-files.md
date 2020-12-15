---
title: Tabella comandi di Visual Studio (. File vsct) | Microsoft Docs
description: Informazioni sui file di configurazione della tabella dei comandi, ovvero file di testo che descrivono il set di comandi contenuti in un pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 377bae52f506c1cb9ac0f6b2d4136faaab0b50ad
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488037"
---
# <a name="visual-studio-command-table-vsct-files"></a>File Visual Studio Command Table (con estensione vsct)
Un file di configurazione della tabella dei comandi è un file di testo che descrive il set di comandi contenuti in un pacchetto VSPackage. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilatore della tabella dei comandi (vsct) compila i file di configurazione basati su XML (file con estensione vsct) in file di output della tabella dei comandi binari (con estensione CTO). I file con estensione CTO risultanti sono identici a quelli creati usando il compilatore della tabella dei comandi (CTC) per compilare i file di configurazione. ctc. Tuttavia, i file con estensione vsct basati su XML presentano alcuni vantaggi, ad esempio un editor XML e XML IntelliSense.

 Per ulteriori informazioni sulla sintassi e la semantica dei file con estensione vsct, vedere [progettazione della tabella dei comandi XML (. File vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Contenuto della sezione
 [Progettazione di file (con estensione vsct) della tabella di comandi XML](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Viene descritto come progettare file con estensione vsct.

 [Procedura: Creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Confronta i metodi per la creazione di un file con estensione vsct. Viene descritto il processo per la creazione manuale di un nuovo file con estensione vsct.

## <a name="related-sections"></a>Sezioni correlate
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Fornisce informazioni dettagliate su ogni sezione del file di configurazione XML della tabella dei comandi.

 [Configurazione della tabella comandi (. CTC)](/previous-versions/bb165153(v=vs.100)) presenta una panoramica del formato di file CTC deprecato.

 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Descrive la specifica del formato della tabella dei comandi.

 [Risorse nei pacchetti VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Viene descritto come usare le risorse gestite e non gestite nei pacchetti VSPackage gestiti.

 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.