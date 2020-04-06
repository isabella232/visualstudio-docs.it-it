---
title: CommandTable (Elemento) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739653"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del file *vsct.* Questo è il file che definisce il layout effettivo e il tipo dei comandi che un VSPackage fornisce all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per ulteriori informazioni, vedere File della tabella dei comandi di [Visual Studio (con estensione vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| xmlns | Obbligatorio. Spazi dei nomi XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs "<http://www.w3.org/2001/XMLSchema>" |
| Linguaggio | Facoltativa. L'attributo language può essere utilizzato \<per specificare la lingua predefinita di tutte le stringhe> gli elementi nella tabella dei comandi.  Se la lingua non è specificata, verrà utilizzata la lingua del processo corrente:<br /><br /> lingua: "en-us" |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Extern](../extensibility/extern-element.md)|Facoltativa. Contiene direttive per il preprocessore per il compilatore.|
|[Includi elemento](../extensibility/include-element.md)|Facoltativa. Contiene i percorsi di tutti i file da includere nella compilazione.|
|[Definisci elemento](../extensibility/define-element.md)|Facoltativa. Definisce un simbolo in base al nome e al valore.|
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativa. L'elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|
|[CommandPlacements (elemento)](../extensibility/commandplacements-element.md)|Facoltativa. Definisce la posizione nella barra dei comandi in cui devono essere posizionati i comandi.|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativa. Determina la visibilità statica di comandi e barre degli strumenti.|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Facoltativa. Specifica le combinazioni di tasti di scelta rapida, se presenti, per i comandi.|
|[UsedCommands (elemento)](../extensibility/usedcommands-element.md)|Facoltativa. Consente a un pacchetto VSPackage di implementare facoltativamente la propria versione della funzionalità originariamente supportata da altri pacchetti VSPackage.Allows a VSPackage to optionally implement its own version of functionality originally supported by other VSPackages.|
|[Elemento Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Facoltativa. Contiene tutti i dati dei simboli, ovvero GUID, ID e così via, per il compilatore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
