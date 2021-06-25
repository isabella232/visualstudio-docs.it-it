---
title: Elemento CommandPlacements | Microsoft Docs
description: L'elemento CommandPlacements raggruppa gli elementi CommandPlacement e altri raggruppamenti CommandPlacements. L'elemento CommandPlacements è facoltativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901890"
---
# <a name="commandplacements-element"></a>Elemento CommandPlacements
L'elemento CommandPlacements raggruppa gli elementi CommandPlacement e altri raggruppamenti CommandPlacements.

 L'elemento CommandPlacements è facoltativo. Se non è necessario includere comandi, gruppi o menu in una posizione secondaria, non è necessario includere questa sezione nel file *con estensione vsct.*

## <a name="syntax"></a>Sintassi

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|Condizione|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|CommandPlacements|Raggruppa gli elementi CommandPlacement e altri raggruppamenti CommandPlacements.|
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Consente di includere pulsanti, gruppi e menu in più gruppi o menu.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi.|

## <a name="example"></a>Esempio

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Vedere anche
- [Elemento CommandPlacement](../extensibility/commandplacement-element.md)
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
