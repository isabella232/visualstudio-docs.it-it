---
title: Elemento VisibilityConstraints | Microsoft Docs
description: L'elemento VisibilityConstraints determina la visibilità statica di gruppi di comandi e barre degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f50f23847da8f6d56da6763146efd147aebca8c6
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863920"
---
# <a name="visibilityconstraints-element"></a>Elemento VisibilityConstraints
L'elemento VisibilityConstraints determina la visibilità statica di gruppi di comandi e barre degli strumenti. La visibilità viene prima controllata dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) senza caricare il pacchetto VSPackage.

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
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilità statica dei comandi e delle barre degli strumenti.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilità statica di gruppi di comandi e barre degli strumenti.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi (ad esempio, le voci di menu, i menu, le barre degli strumenti e le caselle combinate) forniti da un VSPackage all'IDE.|

## <a name="example"></a>Esempio

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Vedere anche
- [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)
- [Tabella comandi di Visual Studio (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
