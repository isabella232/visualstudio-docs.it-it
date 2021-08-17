---
title: Elemento CommandTable | Microsoft Docs
description: CommandTable è l'elemento radice del file con estensione vsct, che definisce il layout e il tipo dei comandi forniti da un VSPackage all'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: afedf0b5e6e761d9b9801cdc88aad16cba922c981904ef50399ae90cd00d8578
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293573"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del file *con estensione vsct.* Si tratta del file che definisce il layout e il tipo effettivi dei comandi forniti da un VSPackage all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per altre informazioni, vedere Visual Studio file di tabella dei comandi (con estensione [vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| xmlns | Obbligatorio. Spazi dei nomi XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs=" <http://www.w3.org/2001/XMLSchema> " |
| Linguaggio | facoltativo. L'attributo language può essere usato per specificare la lingua predefinita di tutti \<Strings> gli elementi nella tabella dei comandi.  Se la lingua non è specificata, verrà usata la lingua del processo corrente:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Extern](../extensibility/extern-element.md)|facoltativo. Contiene direttive per il preprocessore per il compilatore.|
|[Include - elemento](../extensibility/include-element.md)|facoltativo. Contiene i percorsi di tutti i file da includere nella compilazione.|
|[Elemento Define](../extensibility/define-element.md)|facoltativo. Definisce un simbolo in base al nome e al valore.|
|[Elemento Commands](../extensibility/commands-element.md)|facoltativo. Elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|
|[CommandPlacements - elemento](../extensibility/commandplacements-element.md)|facoltativo. Definisce dove devono essere posizionati i comandi sulla barra dei comandi.|
|[VisibilityConstraints - elemento](../extensibility/visibilityconstraints-element.md)|facoltativo. Determina la visibilità statica di comandi e barre degli strumenti.|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|facoltativo. Specifica le combinazioni di tasti di scelta rapida, se presenti, per i comandi.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|facoltativo. Consente a un VSPackage di implementare facoltativamente la propria versione delle funzionalità originariamente supportate da altri PACCHETTI VSPackage.|
|[Symbols - elemento](https://www.microsoft.com/download/details.aspx?id=55984)|facoltativo. Contiene tutti i dati dei simboli ( GUID, ID e così via) per il compilatore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
