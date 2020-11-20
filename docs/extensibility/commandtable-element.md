---
title: Elemento CommandTable | Microsoft Docs
description: CommandTable è l'elemento radice del file con estensione vsct, che definisce il layout e il tipo dei comandi forniti da un VSPackage all'IDE.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 24e6792bb6199606f1d993492527d39c3f0f7f8b
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974526"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del file *. vsct* . Questo è il file che definisce il layout e il tipo effettivi dei comandi forniti da un pacchetto VSPackage all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per ulteriori informazioni, vedere [file della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

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
| xmlns | Obbligatorio. Spazi dei nomi XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = " <http://www.w3.org/2001/XMLSchema> " |
| Linguaggio | Facoltativo. L'attributo Language può essere utilizzato per specificare la lingua predefinita di tutti \<Strings> gli elementi nella tabella dei comandi.  Se la lingua non è specificata, verrà utilizzata la lingua del processo corrente:<br /><br /> lingua = "en-US" |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Extern (elemento)](../extensibility/extern-element.md)|Facoltativo. Contiene le direttive per il preprocessore per il compilatore.|
|[Elemento include](../extensibility/include-element.md)|Facoltativo. Contiene i percorsi di tutti i file da includere nella compilazione.|
|[Definisci elemento](../extensibility/define-element.md)|Facoltativo. Definisce un simbolo in base al nome e al valore.|
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativo. Elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Facoltativo. Definisce la posizione della barra dei comandi in cui devono essere inseriti i comandi.|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativo. Determina la visibilità statica dei comandi e delle barre degli strumenti.|
|[Elemento Portatasti](../extensibility/keybindings-element.md)|Facoltativo. Specifica le combinazioni di tasti di scelta rapida per i comandi.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Facoltativo. Consente a un VSPackage di implementare facoltativamente la propria versione di funzionalità originariamente supportata da altri pacchetti VSPackage.|
|[Symbols-elemento](https://www.microsoft.com/download/details.aspx?id=55984)|Facoltativo. Contiene i dati dei simboli, ovvero GUID, ID e così via, per il compilatore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
