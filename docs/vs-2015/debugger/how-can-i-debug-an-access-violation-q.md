---
title: Come è possibile effettuare il debug di una violazione di accesso? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6188cc273cdea1755071e36f606fb8f041508d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297316"
---
# <a name="how-can-i-debug-an-access-violation"></a>Come è possibile effettuare il debug di una violazione di accesso?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrizione del problema  
 Il programma genera una violazione di accesso. Come è possibile effettuarne il debug?  
  
## <a name="solution"></a>Soluzione  
 Se si riceve un avviso di violazione di accesso su una riga di codice che dereferenzia più puntatori, può essere difficile individuare il puntatore che ha causato la violazione di accesso. A partire da Visual Studio 2015 Update 1, la finestra di dialogo di eccezione ora specifica esplicitamente il puntatore che ha causato la violazione di accesso.  
  
 Ad esempio, con il codice seguente si dovrebbe ottenere una violazione di accesso:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 Se si esegue questo codice in Visual Studio 2015 Update 1, dovrebbe comparire la finestra di dialogo di eccezione seguente:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Se non è possibile determinare perché il puntatore ha causato una violazione di accesso, tracciare il codice per assicurarsi che il puntatore che provoca il problema sia stato assegnato correttamente.  Se viene passato come parametro, assicurarsi che sia passato in modo corretto e che non si stia creando accidentalmente una [copia superficiale](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Verificare quindi che i valori non vengano involontariamente modificati in qualche punto del programma creando un punto di interruzione dei dati per il puntatore in questione per assicurarsi che non venga modificato altrove nel programma. Per ulteriori informazioni sui punti di interruzione dei dati, vedere la relativa sezione in [Using Breakpoints](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
