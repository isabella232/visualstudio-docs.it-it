---
title: Elemento UsedCommands | Microsoft Docs
description: L'elemento UsedCommands raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands. L'elemento UsedCommands è facoltativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: be720228c3ea53e9bfc5f5b5f2da44e919d94199120a3fbafeb3a575e8d56266
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358818"
---
# <a name="usedcommands-element"></a>Elemento UsedCommands
L'elemento UsedCommands raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands.

 L'elemento UsedCommands è facoltativo. Se non si chiamano comandi definiti all'esterno del pacchetto, non è necessario includere questa sezione nel file con estensione vsct.

## <a name="syntax"></a>Sintassi

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|Condition|facoltativo. Vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento UsedCommand](../extensibility/usedcommand-element.md)|Comando implementato da altro codice.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi (ad esempio voci di menu, menu, barre degli strumenti e caselle combinate) forniti da un vspackage all'ambiente di sviluppo integrato (IDE).|

## <a name="example"></a>Esempio

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Vedere anche
- [Elemento UsedCommand](../extensibility/usedcommand-element.md)
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
