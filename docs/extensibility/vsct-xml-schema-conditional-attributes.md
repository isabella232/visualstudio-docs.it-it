---
title: Attributi condizionali dello schema XML VSCT | Microsoft Docs
description: Informazioni su come applicare attributi condizionali a elenchi ed elementi di XML Schema VSCT. Gli attributi restituiscono true o false, controllando l'output risultante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e91207016ed6e1baab80b323680d10a40e0331d8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905254"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributi condizionali dello schema XML VSCT
È possibile applicare attributi condizionali a tutti gli elenchi ed elementi. Gli operatori logici e le espressioni di espansione dei simboli restituiscono true o false. Se true, l'elenco o l'elemento associato viene incluso nell'output risultante.

 È possibile testare le espansioni di token rispetto ad altre espansioni di token o costanti. La funzione verifica se è stato definito un `Defined()` nome specifico, anche se non ha alcun valore.

 Quando un attributo Condition viene applicato a un elenco, la condizione viene applicata a ogni elemento figlio nell'elenco. Se un elemento figlio contiene un attributo Condition, la condizione viene combinata con l'espressione padre tramite un'operazione AND.

 I valori 1, '1' e 'true' vengono valutati come true e 0, '0' e 'false' vengono valutati come false.

## <a name="operators"></a>Operatori
 Usare gli operatori seguenti per valutare le espressioni condizionali.

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
- [Visual Studio tabella dei comandi (. Vsct) file](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
