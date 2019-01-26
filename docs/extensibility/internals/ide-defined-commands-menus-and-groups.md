---
title: Comandi definiti dall'IDE, menu e i gruppi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e9c7f8514dffbea2246f74019a8e684f8af76e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940687"
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
 [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fornisce i valori GUID e ID dei menu nella barra dei menu di Visual Studio e dei gruppi che contengono.  
  
 [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fornisce i valori GUID e ID delle barre degli strumenti nell'IDE di Visual Studio e dei gruppi che contengono.  
  
 [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fornisce i valori GUID e ID di comandi definiti dall'IDE di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)