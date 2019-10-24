---
title: Comandi, menu e gruppi definiti dall'IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727288"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Comandi, menu e gruppi definiti dall'IDE
Molti menu, comandi e gruppi di comandi sono già definiti per l'uso da parte dell'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Questi comandi sono disponibili anche per l'uso quando si estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Ricerca di comandi definiti dall'ambiente
 I comandi dell'ambiente sono definiti in un set di quattro file con estensione vsct:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Questi file si trovano nel *percorso di installazione di \<Visual Studio SDK >* \\ \VisualStudioIntegration\Common\Inc. Questi file forniscono le definizioni e i GUID dei menu e dei gruppi che è possibile usare nel file di configurazione della tabella dei comandi (con estensione vsct) del pacchetto VSPackage come contenitori per i menu, i gruppi e i comandi.

## <a name="in-this-section"></a>Contenuto della sezione
- [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Fornisce i valori GUID e ID dei menu sulla barra dei menu di Visual Studio e dei gruppi in essi contenuti.

- [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Fornisce i valori GUID e ID delle barre degli strumenti nell'IDE di Visual Studio e dei gruppi in essi contenuti.

- [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Fornisce i valori GUID e ID dei comandi definiti dall'IDE di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)