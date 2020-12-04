---
title: Operatore di contesto nel debugger (C++) | Microsoft Docs
description: Potrebbe essere necessario fornire il contesto per un nome C++ che si trova in un ambito esterno ed è nascosto da un nome locale. Informazioni su come usare l'operatore di contesto a tale scopo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1bc238cc56e1b815e79ba381a7cd4866085d3bef
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559758"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Operatore di contesto nel debugger di Visual Studio (C++)
L'operatore di contesto in C++ può essere usato per qualificare la posizione di un punto di interruzione, il nome di una variabile o un'espressione. L'operatore di contesto è utile per specificare un nome da un ambito esterno che altrimenti sarebbe nascosto da un nome locale.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sintassi
 Il contesto può essere specificato in due modi:

1. {,,[*module*] } *expression*

     Le parentesi graffe devono contenere due virgole e il nome o il percorso completo del modulo (file eseguibile o DLL).

     Ad esempio, per impostare un punto di interruzione nella funzione `SomeFunction` di EXAMPLE.dll:

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *module*!*expression*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *module* è il nome di un modulo. È possibile usare un percorso completo per distinguere i moduli che hanno lo stesso nome.

   Se il percorso di *module* include una virgola, uno spazio incorporato o una parentesi graffa, è necessario racchiudere il percorso tra virgolette in modo che il parser del contesto possa riconoscere correttamente la stringa. Poiché le virgolette singole vengono considerate parte di un nome di file di Windows, è necessario usare le virgolette doppie. ad esempio:

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *expression* è una qualsiasi espressione C++ valida che viene risolta in una destinazione valida, ad esempio un nome di funzione, un nome di variabile o un indirizzo del puntatore in *module*.

  Quando l'analizzatore di espressioni rileva un simbolo in un'espressione, ne esegue la ricerca nel seguente ordine:

1. Ambito lessicale verso l'esterno, a partire dal blocco corrente, serie di istruzioni racchiuse tra parentesi graffe, verso il blocco di inclusione. Il blocco corrente è il codice contenente la posizione corrente, ovvero l'indirizzo del puntatore all'istruzione.

2. Ambito della funzione. Funzione corrente.

3. Ambito della classe, se la posizione corrente si trova all'interno di una funzione membro C++. Nell'ambito della classe sono incluse tutte le classi base. L'analizzatore di espressioni usa le regole di dominanza normali.

4. Simboli globali nel modulo corrente.

5. Simboli pubblici nel programma corrente.