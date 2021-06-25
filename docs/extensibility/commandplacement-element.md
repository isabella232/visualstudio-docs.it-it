---
title: Elemento CommandPlacement | Microsoft Docs
description: L'elemento CommandPlacement consente di includere pulsanti, gruppi e menu in più gruppi o menu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69be89fb2773be9de632b8059cf217303daaede7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901994"
---
# <a name="commandplacement-element"></a>CommandPlacement - elemento
L'elemento CommandPlacement consente di includere pulsanti, gruppi e menu in più gruppi o menu. Usando l'elemento CommandPlacement, non è necessario ridefinire completamente questi elementi per modificare l'aspetto di un'interfaccia utente.

 Per altre informazioni, vedere [Creare gruppi riutilizzabili di pulsanti.](../extensibility/creating-reusable-groups-of-buttons.md)

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
|guid|Obbligatorio. GUID del set di comandi, come definito [nell'elemento Symbols](../extensibility/symbols-element.md).|
|id|Obbligatorio. ID del menu, del gruppo o del comando da inserire, come definito in `Symbols Element` .|
|priority|Obbligatorio. Determina la posizione visiva dell'elemento nel relativo elemento padre.|
|Condizione|facoltativo. Vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre|Obbligatorio. Menu o gruppo che ospita l'elemento da inserire.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[CommandPlacements - elemento](../extensibility/commandplacements-element.md)|Specifica i gruppi di elementi CommandPlacements e CommandPlacement.|

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
- [CommandPlacements - elemento](../extensibility/commandplacements-element.md)
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
