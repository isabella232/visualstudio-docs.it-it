---
title: Proprietà Define Element . Documenti Microsoft
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
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712265"
---
# <a name="define-element"></a>Definisci elemento
Definisce una coppia nome simbolo e valore. Questo simbolo può essere valutato da attributi condizionali. Per ulteriori informazioni, consultate [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md) Vedere anche [l'elemento Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Sintassi

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|name|Obbligatorio. Il nome del simbolo:<br /><br /> nome: "Modalità"|
|Valore|Obbligatorio. Il valore del simbolo:<br /><br /> valore: "Standard"|
|Condizione|Facoltativa. Per ulteriori informazioni, consultate [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, voci di menu, menu, barre degli strumenti e caselle combinate.|

## <a name="example"></a>Esempio

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
