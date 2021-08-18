---
title: Elemento padre | Microsoft Docs
description: L'elemento Parent specifica che un elemento è un elemento padre di un pulsante, una casella combinata, un menu o un gruppo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cb2ce0ddcf779d5c6c9e0b880d99f169d762065d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152068"
---
# <a name="parent-element"></a>Elemento padre
L'elemento padre di un pulsante o di una casella combinata può essere solo un gruppo. L'elemento padre di un menu o gruppo può essere qualsiasi altro menu o gruppo. In un [elemento CommandPlacement](../extensibility/commandplacement-element.md)questo elemento è obbligatorio. in tutte le altre istanze è facoltativo. Se questo elemento viene omesso, l'elemento `Group_Undefined:0` padre di verrà implicito.

## <a name="syntax"></a>Sintassi

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[CommandTable - elemento](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi forniti da un VSPackage all'ambiente di sviluppo integrato (IDE). Ad esempio, voci di menu, menu, barre degli strumenti e caselle combinate.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa [gli elementi dell'elemento](../extensibility/button-element.md) Button.|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene voci che definiscono i gruppi di comandi di un VSPackage.|

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
