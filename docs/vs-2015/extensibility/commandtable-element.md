---
title: Elemento CommandTable | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1adc3e8f8c7894cfb3a55617ce594f52a60f2498
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817373"
---
# <a name="commandtable-element"></a>Elemento CommandTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable è l'elemento radice del file con estensione vsct. Si tratta del file che definisce il layout effettivo e il tipo dei comandi che un pacchetto VSPackage fornisce all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
  
| Attributo |                                                                                                                   Descrizione                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Obbligatorio. Spazi dei nomi XML:<br /><br /> xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns = "<http://www.w3.org/2001/XMLSchema>"                                   |
| language  | Facoltativo. L'attributo della lingua consente di specificare la lingua predefinita del tutto \<stringhe > elementi della tabella comandi.  Se la lingua non viene specificata, verrà usata la lingua del processo corrente:<br /><br /> Language = "en-us" |
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Extern](../extensibility/extern-element.md)|Facoltativo. Contiene le direttive del preprocessore per il compilatore.|  
|[Elemento Include](../extensibility/include-element.md)|Facoltativo. Contiene i percorsi di tutti i file da includere nella compilazione.|  
|[Elemento Define](../extensibility/define-element.md)|Facoltativo. Definisce un simbolo dato il nome e valore.|  
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativo. L'elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Facoltativo. Definisce dove sulla barra dei comandi i comandi devono essere inseriti.|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativo. Determina la visibilità statica di comandi e le barre degli strumenti.|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Facoltativo. Specifica le combinazioni di tasti di scelta rapida, se presente, per i comandi.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Facoltativo. Consente a un VSPackage se lo si desidera implementare la propria versione della funzionalità originariamente supportato da altri pacchetti VSPackage.|  
|[Elemento Symbols](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Facoltativo. Contiene tutti i dati dei simboli, GUID, gli ID e così via, per consentire al compilatore.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

