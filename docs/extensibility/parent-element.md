---
title: Elemento padre | Microsoft Docs
description: L'elemento padre specifica che un elemento è un elemento padre di un pulsante, di una casella combinata, di un menu o di un gruppo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac914fd3245982af89facb97ff2d528b410da99
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090382"
---
# <a name="parent-element"></a>Elemento padre
L'elemento padre di un pulsante o di una casella combinata può essere solo un gruppo. L'elemento padre di un menu o di un gruppo può essere qualsiasi altro menu o gruppo. In un [elemento CommandPlacement](../extensibility/commandplacement-element.md), questo elemento è obbligatorio. in tutti gli altri casi è facoltativa. Se questo elemento viene omesso, l'elemento padre di `Group_Undefined:0` sarà implicito.

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
 nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi forniti da un VSPackage all'Integrated Development Environment (IDE). Ad esempio, le voci di menu, i menu, le barre degli strumenti e le caselle combinate.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi [elemento del pulsante](../extensibility/button-element.md) .|
|[Menu (elemento)](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comandi di un VSPackage.|

## <a name="see-also"></a>Vedi anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
