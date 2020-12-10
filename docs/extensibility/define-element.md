---
title: Elemento define | Microsoft Docs
description: L'elemento define definisce un nome di simbolo e una coppia di valori. Questo simbolo può essere valutato dagli attributi condizionali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a427371afe55b6ea4ee20f658e683b9dcdb8fbe2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996240"
---
# <a name="define-element"></a>Definisci elemento
Definisce una coppia di nome e valore del simbolo. Questo simbolo può essere valutato dagli attributi condizionali. Per ulteriori informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md). Vedere anche l' [elemento symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Sintassi

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|name|Obbligatorio. Nome del simbolo:<br /><br /> Name = "Mode"|
|Valore|Obbligatorio. Valore del simbolo:<br /><br /> value = "standard"|
|Condizione|facoltativo. Per ulteriori informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi forniti da un VSPackage all'Integrated Development Environment (IDE). Ad esempio, le voci di menu, i menu, le barre degli strumenti e le caselle combinate.|

## <a name="example"></a>Esempio

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
