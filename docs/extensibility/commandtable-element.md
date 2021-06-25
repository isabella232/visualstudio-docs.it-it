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
ms.workload:
- vssdk
ms.openlocfilehash: 55faf4ee8bdc7ec261508fd07f5a573e7a29560f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901851"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del file *con estensione vsct.* Si tratta del file che definisce il layout e il tipo effettivi dei comandi forniti da un VSPackage all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per altre informazioni, vedere Visual Studio file di tabella dei comandi [(con estensione vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| Linguaggio | facoltativo. L'attributo language può essere usato per specificare la lingua predefinita di tutti gli \<Strings> elementi nella tabella dei comandi.  Se la lingua non viene specificata, verrà usata la lingua del processo corrente:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Extern](../extensibility/extern-element.md)|facoltativo. Contiene direttive per il preprocessore per il compilatore.|
|[Elemento Include](../extensibility/include-element.md)|facoltativo. Contiene i percorsi di tutti i file da includere nella compilazione.|
|[Elemento Define](../extensibility/define-element.md)|facoltativo. Definisce un simbolo in base al nome e al valore.|
|[Elemento Commands](../extensibility/commands-element.md)|facoltativo. Elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|facoltativo. Definisce la posizione in cui devono essere posizionati i comandi sulla barra dei comandi.|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|facoltativo. Determina la visibilità statica di comandi e barre degli strumenti.|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|facoltativo. Specifica le eventuali combinazioni di tasti di scelta rapida per i comandi.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|facoltativo. Consente a un VSPackage di implementare facoltativamente la propria versione della funzionalità originariamente supportata da altri VSPackage.|
|[Elemento Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|facoltativo. Contiene tutti i dati dei simboli, ad esempio GUID, ID e così via, per il compilatore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

## <a name="see-also"></a>Vedere anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
