---
title: Elemento Parent . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702222"
---
# <a name="parent-element"></a>Elemento padre
L'elemento padre di un pulsante o di una casella combinata può essere solo un gruppo. L'elemento padre di un menu o di un gruppo può essere qualsiasi altro menu o gruppo. In un [CommandPlacement elemento](../extensibility/commandplacement-element.md), questo elemento è obbligatorio; in tutti gli altri casi è facoltativo. Se questo elemento viene omesso, l'elemento padre di `Group_Undefined:0` sarà implicito.

## <a name="syntax"></a>Sintassi

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore di comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore di comando GUID/ID.|

### <a name="child-elements"></a>Elementi figlio
 nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, voci di menu, menu, barre degli strumenti e caselle combinate.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi [Button.](../extensibility/button-element.md)|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un pacchetto VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene voci che definiscono i gruppi di comandi di un pacchetto VSPackage.|

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
