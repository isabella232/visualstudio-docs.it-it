---
title: Elemento CommandPlacement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c43dab922d51d2d3f96ffaba0ef24f8f0e18fa1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341874"
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
L'elemento CommandPlacement Abilita i pulsanti, gruppi e i menu da includere in più di un gruppo o un menu. Usando l'elemento CommandPlacement, non è completamente ridefinire tali elementi per modificare l'aspetto di un'interfaccia utente.

 Per altre informazioni, vedere [creazione di gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md).

## <a name="syntax"></a>Sintassi

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. Il guid del set di comandi, come definito nel [elemento Symbols](../extensibility/symbols-element.md).|
|ID|Obbligatorio. L'id del menu, gruppo o comando per essere inserito, come definito nel `Symbols Element`.|
|priority|Obbligatorio. Determina la posizione dell'elemento visual nel relativo elemento padre.|
|Condizione|Facoltativo. Visualizzare [Aattributes condizionale](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre|Obbligatorio. Il menu o un gruppo che ospita l'elemento da inserire.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Specifica i gruppi di elementi CommandPlacements e CommandPlacement.|

## <a name="example"></a>Esempio

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Vedere anche
- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
