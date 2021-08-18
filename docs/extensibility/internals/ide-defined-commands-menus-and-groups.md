---
title: IDE-Defined comandi, menu e gruppi | Microsoft Docs
description: Informazioni sui menu, i comandi e i gruppi di comandi definiti nel Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9f25616c97ed4f3b1e8402432a36db86e72edb58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042396"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Comandi, menu e gruppi definiti dall'IDE
Molti menu, comandi e gruppi di comandi sono già definiti per l'uso da parte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'IDE. Questi comandi sono disponibili anche per l'uso quando si estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Ricerca Environment-Defined comandi
 I comandi di ambiente sono definiti in un set di quattro file con estensione vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Questi file si trovano in *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc. \\ Questi file forniscono le definizioni e i GUID dei menu e dei gruppi che è possibile usare nel file di configurazione della tabella dei comandi (con estensione vsct) del pacchetto VSPackage come contenitori per menu, gruppi e comandi personalizzati.

## <a name="in-this-section"></a>Contenuto della sezione
- [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Fornisce i valori GUID e ID dei menu Visual Studio barra dei menu e dei gruppi in essi contenuti.

- [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Fornisce i valori GUID e ID delle barre degli strumenti nell Visual Studio IDE e dei gruppi che contengono.

- [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Fornisce i valori GUID e ID dei comandi definiti dal Visual Studio IDE.

## <a name="see-also"></a>Vedi anche
- [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
