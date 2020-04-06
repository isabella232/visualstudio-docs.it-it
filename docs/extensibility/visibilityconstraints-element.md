---
title: Elemento VisibilityConstraints Documenti Microsoft
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
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698196"
---
# <a name="visibilityconstraints-element"></a>Elemento VisibilityConstraints
L'elemento VisibilityConstraints determina la visibilità statica di gruppi di comandi e barre degli strumenti. La visibilità viene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] innanzitutto controllata dall'ambiente di sviluppo integrato (IDE) senza caricare il pacchetto VSPackage.

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
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilità statica di comandi e barre degli strumenti.|
|[VisibilityConstraintsVisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilità statica di gruppi di comandi e barre degli strumenti.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi (ad esempio, voci di menu, menu, barre degli strumenti e caselle combinate) che un VSPackage fornisce all'IDE.|

## <a name="example"></a>Esempio

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Vedere anche
- [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)
- [Tabella dei comandi di Visual Studio (. Vsct) file](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
