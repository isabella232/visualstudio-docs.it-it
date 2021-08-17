---
title: Elemento VisibilityConstraints | Microsoft Docs
description: L'elemento VisibilityConstraints determina la visibilità statica di gruppi di comandi e barre degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0a24761a7f0c71f50be70b12de1203c0f22d2b8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049246"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints - elemento
L'elemento VisibilityConstraints determina la visibilità statica di gruppi di comandi e barre degli strumenti. La visibilità viene prima controllata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dall'ambiente di sviluppo integrato (IDE) senza caricare il pacchetto VSPackage.

## <a name="syntax"></a>Sintassi

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
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
|[VisibilityItem - elemento](../extensibility/visibilityitem-element.md)|Determina la visibilità statica di comandi e barre degli strumenti.|
|[Proprietà VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilità statica di gruppi di comandi e barre degli strumenti.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi (ad esempio voci di menu, menu, barre degli strumenti e caselle combinate) forniti da un VSPackage all'IDE.|

## <a name="example"></a>Esempio

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Vedere anche
- [VisibilityItem - elemento](../extensibility/visibilityitem-element.md)
- [Visual Studio tabella dei comandi (. Vsct) file](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
