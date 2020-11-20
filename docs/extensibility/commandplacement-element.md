---
title: Elemento CommandPlacement | Microsoft Docs
description: L'elemento CommandPlacement consente di includere pulsanti, gruppi e menu in più di un gruppo o menu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2828a32ea837e95be438aafa6ec4b31293a43a7
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974068"
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
L'elemento CommandPlacement consente di includere pulsanti, gruppi e menu in più di un gruppo o menu. Utilizzando l'elemento CommandPlacement, non è necessario ridefinire completamente questi elementi per modificare l'aspetto di un'interfaccia utente.

 Per altre informazioni, vedere [creare gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md).

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
|guid|Obbligatorio. GUID del set di comandi, come definito nell' [elemento symbols](../extensibility/symbols-element.md).|
|id|Obbligatorio. ID del menu, del gruppo o del comando da inserire, come definito in `Symbols Element` .|
|priority|Obbligatorio. Determina la posizione visiva dell'elemento nel relativo elemento padre.|
|Condizione|Facoltativo. Vedere [Aattributes condizionale](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre|Obbligatorio. Menu o gruppo che ospita l'elemento da inserire.|

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
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
