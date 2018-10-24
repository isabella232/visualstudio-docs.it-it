---
title: Elemento CommandTable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c2adca249ba245825f9b664b46e1b4674d0ea50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879909"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del *vsct* file. Si tratta del file che definisce il layout effettivo e il tipo dei comandi che un pacchetto VSPackage fornisce all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per altre informazioni, vedere [file table (vsct) di Visual Studio comando](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
| Attributo | Descrizione |
|-----------| - |
| xmlns | Obbligatorio. Spazi dei nomi XML:<br /><br /> xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns = "<http://www.w3.org/2001/XMLSchema>" |
| language | Facoltativo. L'attributo della lingua consente di specificare la lingua predefinita del tutto \<stringhe > elementi della tabella comandi.  Se la lingua non viene specificata, verrà usata la lingua del processo corrente:<br /><br /> Language = "en-us" |
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento extern](../extensibility/extern-element.md)|Facoltativo. Contiene le direttive del preprocessore per il compilatore.|  
|[L'elemento di inclusione](../extensibility/include-element.md)|Facoltativo. Contiene i percorsi di tutti i file da includere nella compilazione.|  
|[Definire l'elemento](../extensibility/define-element.md)|Facoltativo. Definisce un simbolo dato il nome e valore.|  
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativo. L'elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Facoltativo. Definisce dove sulla barra dei comandi i comandi devono essere inseriti.|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativo. Determina la visibilità statica di comandi e le barre degli strumenti.|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Facoltativo. Specifica le combinazioni di tasti di scelta rapida, se presente, per i comandi.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Facoltativo. Consente a un VSPackage se lo si desidera implementare la propria versione della funzionalità originariamente supportato da altri pacchetti VSPackage.|  
|[Elemento Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Facoltativo. Contiene tutti i dati dei simboli, GUID, gli ID e così via, per consentire al compilatore.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
## <a name="see-also"></a>Vedere anche  
 [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)