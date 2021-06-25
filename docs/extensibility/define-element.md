---
title: Definire l'elemento | Microsoft Docs
description: L'elemento Define definisce una coppia nome/valore del simbolo. Questo simbolo può essere valutato da attributi condizionali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 409621410db727f933e41bae894f125dc877b4c2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898045"
---
# <a name="define-element"></a>Elemento Define
Definisce una coppia nome/valore del simbolo. Questo simbolo può essere valutato da attributi condizionali. Per altre informazioni, vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md) Vedere anche [l'elemento Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Sintassi

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|name|Obbligatorio. Nome del simbolo:<br /><br /> name="Mode"|
|Valore|Obbligatorio. Valore del simbolo:<br /><br /> value="Standard"|
|Condizione|facoltativo. Per altre informazioni, vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi forniti da un VSPackage all'ambiente di sviluppo integrato (IDE). Ad esempio, voci di menu, menu, barre degli strumenti e caselle combinate.|

## <a name="example"></a>Esempio

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Vedere anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
