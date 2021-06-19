---
title: Eseguire il debug di una violazione di accesso C++ | Microsoft Docs
description: Vedere i suggerimenti per la risoluzione di una violazione di accesso quando più puntatori sono candidati. Le versioni recenti di Visual Studio il puntatore errant.
ms.custom: SEO-VS-2020
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3689942c9db9fde3598590cf30100fc590c50753
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387034"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Come è possibile eseguire il debug di una violazione di accesso C++?

## <a name="problem-description"></a>Descrizione del problema

Il programma genera una violazione di accesso. Come è possibile effettuarne il debug?

## <a name="solution"></a>Soluzione

Se si riceve un avviso di violazione di accesso su una riga di codice che dereferenzia più puntatori, può essere difficile individuare il puntatore che ha causato la violazione di accesso. A partire da Visual Studio 2015 Update 1, la finestra di dialogo di eccezione ora specifica esplicitamente il puntatore che ha causato la violazione di accesso.

Ad esempio, con il codice seguente si dovrebbe ottenere una violazione di accesso:

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Se si esegue questo codice in Visual Studio 2015 Update 1, dovrebbe comparire la finestra di dialogo di eccezione seguente:

![Screenshot di una finestra Microsoft Visual Studio di eccezione, che mostra una violazione di accesso in lettura per "A->B era nullptr". Il pulsante Interrompi è selezionato.](../debugger/media/accessviolationcplus.png)

Se non è possibile determinare perché il puntatore ha causato una violazione di accesso, tracciare il codice per assicurarsi che il puntatore che provoca il problema sia stato assegnato correttamente.  Se viene passato come parametro, assicurarsi che venga passato correttamente e che non si crei accidentalmente una [copia superficiale.](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy) Verificare quindi che i valori non vengano involontariamente modificati in qualche punto del programma creando un punto di interruzione dei dati per il puntatore in questione per assicurarsi che non venga modificato altrove nel programma. Per ulteriori informazioni sui punti di interruzione dei dati, vedere la relativa sezione in [Using Breakpoints](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)