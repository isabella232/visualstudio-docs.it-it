---
title: Elementi Symbols | Microsoft Docs
description: L'elemento Symbols definisce GUID e ID usati da altri elementi VSCT. Questo articolo contiene un esempio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6a9aad102cd5b4e701715d245bde20942d8abd50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144366"
---
# <a name="symbols-element"></a>Elemento Symbols
Definisce GUID e ID usati da altri elementi VSCT. Per il codice non gestito, queste informazioni provengono in genere dai file di intestazione specificati [dall'elemento Extern](../extensibility/extern-element.md). Il codice gestito usa gli elementi figlio dell'elemento Symbols per definire queste informazioni.

 Se si crea un file vsct da un file CTO esistente, i simboli verranno generati come elementi figlio dell'elemento Symbols. Per altre informazioni, vedere [Procedura: Creare un oggetto . Vsct File da un oggetto esistente. File Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 L'elemento Symbols non deve essere confuso con [l'elemento Define ,](../extensibility/define-element.md)che definisce le coppie nome-valore per l'uso da parte del preprocessore.

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
|nessuno||

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|GuidSymbol|Definisce un simbolo GUID. GuidSymbol ha due attributi obbligatori: name e value. Il nome è il nome del simbolo e il valore è il valore del GUID come stringa.<br /><br /> Ad esempio:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Definisce un simbolo. IDSymbol ha due attributi obbligatori: name e value. Il nome è il nome del simbolo e il valore è il valore del simbolo come stringa.<br /><br /> Ad esempio:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

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
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
