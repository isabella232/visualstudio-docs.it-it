---
title: Comandi definiti dall'IDE, menu e i gruppi | Microsoft Docs
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
ms.openlocfilehash: 5158a9d1a06ec6f08c67777e4f1ce2e4d37220e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315657"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Comandi, menu e gruppi definiti dall'IDE
Molti menu, comandi e i gruppi di comandi sono già definiti per l'utilizzo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Questi comandi sono anche disponibili per l'uso quando si estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Trovare comandi definiti dall'ambiente
 I comandi di ambiente vengono definiti in un set di file con estensione vsct quattro:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Questi file si trovano  *\<percorso di installazione di Visual Studio SDK >* \visualstudiointegration\common\inc\\. Questi file forniscono le definizioni e i GUID dei menu e i gruppi che è possibile usare nel file di configurazione (con estensione vsct) della tabella comandi del pacchetto VSPackage come contenitori per il proprio menu, gruppi e i comandi.

## <a name="in-this-section"></a>In questa sezione
- [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Fornisce i valori GUID e ID dei menu nella barra dei menu di Visual Studio e dei gruppi che contengono.

- [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Fornisce i valori GUID e ID delle barre degli strumenti nell'IDE di Visual Studio e dei gruppi che contengono.

- [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Fornisce i valori GUID e ID di comandi definiti dall'IDE di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)