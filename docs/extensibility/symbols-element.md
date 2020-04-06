---
title: Elemento Symbols Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699344"
---
# <a name="symbols-element"></a>Elemento Symbols
Definisce GUID e ID utilizzati da altri elementi VSCT. Per il codice non gestito, queste informazioni provengono in genere dai file di intestazione specificati da [Extern Element](../extensibility/extern-element.md). Il codice gestito usa gli elementi figlio dell'elemento Symbols per definire queste informazioni.

 Se si crea un file vsct da un file .cto esistente, i simboli verranno generati come elementi figlio dell'elemento Symbols. Per ulteriori informazioni, vedere Procedura: creare un oggetto [. File Vsct da un file esistente. File Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 L'elemento Symbols non deve essere confuso con l'elemento [Define](../extensibility/define-element.md), che definisce le coppie nome-valore per l'utilizzo da parte del preprocessore.

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
|GuidSymbol (Simbolo Guid)|Definisce un simbolo GUID. GuidSymbol ha due attributi obbligatori: name e value. Il nome è il nome del simbolo e il valore è il valore del GUID come stringa.<br /><br /> Ad esempio:\<GuidSymbol name "guidVsPackage1Pkg" value"/c5f54698-101a-4846-84d3-dc748f9cd848" />|
|IdSymbol (Simbolo)|Definisce un simbolo. IDSymbol ha due attributi obbligatori: name e value. Il nome è il nome del simbolo e il valore è il valore del simbolo come stringa.<br /><br /> Ad esempio:\<IDSymbol name : "MyMenuGroup" value "0x1020" />|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Elemento radice del file vsct.|

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
