---
title: Elemento symbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce299f99699a7bc048b3dc7da39aea3f734addeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719395"
---
# <a name="symbols-element"></a>Elemento Symbols
Definisce GUID e ID usati da altri elementi VSCT. Per il codice non gestito, queste informazioni provengono in genere dai file di intestazione specificati dall' [elemento extern](../extensibility/extern-element.md). Il codice gestito utilizza gli elementi figlio dell'elemento symbols per definire queste informazioni.

 Se si crea un file con estensione vsct da un file CTO esistente, i simboli verranno generati come elementi figlio dell'elemento symbols. Per ulteriori informazioni, vedere [procedura: creare un oggetto. File vsct da un esistente. File CTO](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 L'elemento symbols non deve essere confuso con l' [elemento define](../extensibility/define-element.md), che definisce le coppie nome/valore per l'uso da parte del preprocessore.

## <a name="syntax"></a>Sintassi

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|Nessuno||

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|GuidSymbol|Definisce un simbolo GUID. GuidSymbol dispone di due attributi obbligatori: Name e value. Il nome è il nome del simbolo e il valore è il valore del GUID sotto forma di stringa.<br /><br /> Ad esempio: \<GuidSymbol Name = "guidVsPackage1Pkg" value = "{c5f54698-101A-4846-84D3-dc748f9cd848}"/>|
|IDSymbol|Definisce un simbolo. IDSymbol dispone di due attributi obbligatori: Name e value. Il nome è il nome del simbolo e il valore è il valore del simbolo sotto forma di stringa.<br /><br /> Ad esempio: \<IDSymbol Name = "MyMenuGroup" value = "0x1020"/>|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Elemento radice del file con estensione vsct.|

## <a name="example"></a>Esempio

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)