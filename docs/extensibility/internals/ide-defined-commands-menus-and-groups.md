---
title: Comandi, menu e gruppi definiti dall'IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707725"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Comandi, menu e gruppi definiti dall'IDE
Molti menu, comandi e gruppi di comandi sono già definiti per l'uso da parte dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Questi comandi sono disponibili anche per l'uso quando si estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Ricerca di comandi definiti dall'ambiente
 I comandi dell'ambiente sono definiti in un set di quattro file con estensione vsct:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Questi file si trovano in *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Questi file forniscono le definizioni e i GUID dei menu e dei gruppi che è possibile usare nel file di configurazione della tabella dei comandi (con estensione vsct) del pacchetto VSPackage come contenitori per i menu, i gruppi e i comandi.

## <a name="in-this-section"></a>Contenuto della sezione
- [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Fornisce i valori GUID e ID dei menu sulla barra dei menu di Visual Studio e dei gruppi in essi contenuti.

- [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Fornisce i valori GUID e ID delle barre degli strumenti nell'IDE di Visual Studio e dei gruppi in essi contenuti.

- [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Fornisce i valori GUID e ID dei comandi definiti dall'IDE di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
