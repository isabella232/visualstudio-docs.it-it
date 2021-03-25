---
title: Attributi condizionali di XML Schema VSCT | Microsoft Docs
description: Informazioni su come applicare gli attributi condizionali a VSCT XML Schema gli elenchi e gli elementi. Gli attributi restituiscono true o false, controllando l'output risultante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bc1bcb9d80474b467e90de6262e797087589065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062356"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML Schema attributi condizionali
È possibile applicare attributi condizionali a tutti gli elenchi e gli elementi. Gli operatori logici e le espressioni di espansione simboli restituiscono true o false. Se true, l'elenco o l'elemento associato viene incluso nell'output risultante.

 È possibile testare le espansioni del token rispetto ad altre espansioni o costanti del token. La funzione `Defined()` verifica se è stato definito un determinato nome, anche se non ha alcun valore.

 Quando viene applicato un attributo Condition a un elenco, la condizione viene applicata a ogni elemento figlio dell'elenco. Se un elemento figlio contiene un attributo Condition, la relativa condizione viene combinata con l'espressione padre da un'operazione AND.

 I valori 1,' 1' è true ' vengono valutati come true e 0,' 0' è false ' vengono valutati come false.

## <a name="operators"></a>Operatori
 Utilizzare gli operatori seguenti per valutare le espressioni condizionali.

|Operatore|Definizione|
|--------------|----------------|
|(,)|Raggruppamento|
|!|NOT logico|
|\<, >, \<=, >=, ==, !=|Relazionale e uguaglianza|
|e|Boolean|
|oppure|Boolean|

## <a name="examples"></a>Esempi

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Vedere anche
- [Tabella comandi di Visual Studio (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
