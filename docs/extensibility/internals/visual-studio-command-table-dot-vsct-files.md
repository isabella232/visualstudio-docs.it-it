---
title: Tabella dei comandi di Visual Studio (. File di Vsct) Documenti Microsoft
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
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704034"
---
# <a name="visual-studio-command-table-vsct-files"></a>File Visual Studio Command Table (con estensione vsct)
Un file di configurazione della tabella dei comandi è un file di testo che descrive il set di comandi contenuti in un pacchetto VSPackage.A command table configuration file is a text file that describes the set of commands that a VSPackage contains. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilatore della tabella dei comandi (VSCT) compila i file di configurazione basati su XML (file con estensione vsct) in file di output della tabella dei comandi binari (con estensione cto). I file .cto risultanti sono gli stessi che vengono creati utilizzando il compilatore della tabella dei comandi (CTC) per compilare i file di configurazione .ctc. Tuttavia, i file vsct basati su XML presenta alcuni vantaggi, ad esempio un editor XML e IntelliSense XML.

 Per altre informazioni sulla sintassi e la semantica dei file vsct, vedere Progettazione di tabelle di comando [XML (. Vsct) File](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Contenuto della sezione
 [Progettazione di file (con estensione vsct) della tabella di comandi XML](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Viene descritto come progettare file vsct.

 [Procedura: Creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Confronta i metodi per la creazione di un file vsct. Viene descritto il processo per la creazione manuale di un nuovo file vsct.

## <a name="related-sections"></a>Sezioni correlate
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Vengono fornite informazioni dettagliate su ogni sezione del file di configurazione XML della tabella dei comandi.

 [Configurazione tabella comandi (. Ctc) Files](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) Presenta una panoramica del formato di file .ctc deprecato.

 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Descrive la specifica del formato della tabella dei comandi.

 [Risorse nei pacchetti VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Viene descritto come utilizzare le risorse gestite e non gestite in VSPackage gestiti.

 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.
