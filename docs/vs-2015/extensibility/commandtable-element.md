---
title: Elemento CommandTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477053"
---
# <a name="commandtable-element"></a>Elemento CommandTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable è l'elemento radice del file. vsct. Questo è il file che definisce il layout e il tipo effettivi dei comandi forniti da un pacchetto VSPackage all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
| Attributo |                                                                                                                   Descrizione                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Obbligatoria. Spazi dei nomi XML:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| language  | Facoltativa. L'attributo Language può essere utilizzato per specificare la lingua predefinita di tutte le stringhe \<> elementi della tabella dei comandi.  Se la lingua non è specificata, verrà utilizzata la lingua del processo corrente:<br /><br /> lingua = "en-US" |
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Extern](../extensibility/extern-element.md)|Facoltativa. Contiene le direttive per il preprocessore per il compilatore.|  
|[Elemento Include](../extensibility/include-element.md)|Facoltativa. Contiene i percorsi di tutti i file da includere nella compilazione.|  
|[Elemento Define](../extensibility/define-element.md)|Facoltativa. Definisce un simbolo in base al nome e al valore.|  
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativa. Elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Facoltativa. Definisce la posizione della barra dei comandi in cui devono essere inseriti i comandi.|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativa. Determina la visibilità statica dei comandi e delle barre degli strumenti.|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Facoltativa. Specifica le combinazioni di tasti di scelta rapida per i comandi.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Facoltativa. Consente a un VSPackage di implementare facoltativamente la propria versione di funzionalità originariamente supportata da altri pacchetti VSPackage.|  
|[Elemento Symbols](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Facoltativa. Contiene i dati dei simboli, ovvero GUID, ID e così via, per il compilatore.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|None||  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
