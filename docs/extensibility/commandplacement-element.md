---
title: Elemento CommandPlacement . Documenti Microsoft
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
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739739"
---
# <a name="commandplacement-element"></a>CommandPlacement (elemento)
L'elemento CommandPlacement consente di includere pulsanti, gruppi e menu in più gruppi o menu. Utilizzando l'elemento CommandPlacement, non è necessario ridefinire completamente questi elementi per modificare l'aspetto di un'interfaccia utente.

 Per ulteriori informazioni, consultate [Creare gruppi riutilizzabili di pulsanti.](../extensibility/creating-reusable-groups-of-buttons.md)

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
|guid|Obbligatorio. Guid del set di comandi, come definito [nell'elemento Symbols](../extensibility/symbols-element.md).|
|id|Obbligatorio. ID del menu, del gruppo o del comando da `Symbols Element`inserire, come definito nel file .|
|priority|Obbligatorio. Determina la posizione visiva dell'elemento nel relativo elemento padre.|
|Condizione|Facoltativa. Consultate [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent|Obbligatorio. Menu o gruppo che ospita l'elemento da posizionare.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[CommandPlacements (elemento)](../extensibility/commandplacements-element.md)|Specifica gruppi di elementi CommandPlacements e CommandPlacement.|

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
- [CommandPlacements (elemento)](../extensibility/commandplacements-element.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
