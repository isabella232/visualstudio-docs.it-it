---
title: Definire l'elemento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d82bd5050955f69e23c71569a13ac1a5d428aef2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348143"
---
# <a name="define-element"></a>Definire l'elemento
Definisce una coppia nome / valore di simbolo. Questo simbolo può essere valutato da attributi condizionali. Per altre informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md). Vedere anche il [elemento Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Sintassi

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|name|Obbligatorio. Il nome del simbolo:<br /><br /> name="Mode"|
|predefinito|Obbligatorio. Il valore del simbolo:<br /><br /> value="Standard"|
|Condizione|Facoltativo. Per altre informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|

## <a name="example"></a>Esempio

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Vedere anche
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)