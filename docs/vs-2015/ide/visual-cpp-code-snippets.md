---
title: Frammenti di codice Visual C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 884ec6cc25fd2ef415dc71055361344d79021d5e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696369"
---
# <a name="visual-c-code-snippets"></a>Frammenti di codice Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile usare frammenti di codice per aggiungere il codice usato comunemente per file di codice C++. In generale, è possibile usare frammenti di codice in modo molto simile a C#, ma il set predefinito di frammenti di codice è diverso.  
  
 È possibile aggiungere un frammento di codice in una determinata posizione nel codice (inserimento) o racchiudere il codice selezionato con un frammento di codice.  
  
## <a name="inserting-a-code-snippet"></a>Inserimento di un frammento di codice  
 Per inserire un frammento di codice, aprire un file di codice C++ (file CPP o H), fare clic su un punto qualsiasi all'interno del file ed eseguire una delle seguenti operazioni:  
  
- Fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e selezionare **Inserisci frammento di codice**  
  
- Nel menu**Modifica/IntelliSense** selezionare **Inserisci frammento di codice**  
  
- Usare i tasti di scelta rapida: **CTRL + K + X**  
  
  Verrà visualizzato un elenco di opzioni che iniziano con **#if**. Quando si seleziona **#if** il codice seguente viene aggiunto al file:  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 Sarà quindi possibile sostituire il valore 0 con la condizione corretta.  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>Uso di un frammento di codice per racchiudere il codice selezionato  
 Per usare un frammento di codice per racchiudere il codice selezionato, selezionare una riga (o più righe) ed eseguire una delle operazioni seguenti:  
  
1. Fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e selezionare **Racchiudi tra**  
  
2. Nel menu**Modifica/IntelliSense** selezionare **Racchiudi tra**  
  
3. Usare i tasti di scelta rapida: **CTRL + K + S**  
  
   Selezionare **#if**. Viene visualizzato un output simile al seguente:  
  
```cpp  
#if 0  
#include "pch.h"  // or whatever line you had selected  
#endif // 0  
```  
  
 Sarà quindi possibile sostituire il valore 0 con la condizione corretta.  
  
## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Dove posso trovare un elenco completo dei frammenti di codice C++?  
 È possibile trovare l'elenco completo dei frammenti di codice C++ selezionando **Gestione frammenti di codice** nel menu **Strumenti** e impostando il **Linguaggio** su **Visual C++**. Nella finestra seguente espandere **Visual C++**. Verranno visualizzati i nomi di tutti i frammenti di codice C++ in ordine alfabetico.  
  
 I nomi della maggior parte dei frammenti di codice sono di chiara interpretazione, ma alcuni nomi potrebbero confondere.  
  
## <a name="class-vs-classi"></a>Class e classi  
 Il frammento di codice **class** offre la definizione di una classe denominata MyClass, con il costruttore e il distruttore predefiniti appropriati, dove le definizioni del costruttore e del distruttore si trovano all'esterno della classe:  
  
```cpp  
class MyClass  
{  
public:  
MyClass();  
~MyClass();  
  
private:  
  
};  
  
MyClass::MyClass()  
{  
}  
  
MyClass::~MyClass()  
{  
}  
```  
  
 Anche il frammento di codice classi fornisce la definizione di una classe denominata MyClass, ma i costruttori e distruttori predefiniti sono definiti nella definizione di classe:  
  
```cpp  
class MyClass  
{  
public:  
MyClass()  
{  
}  
  
~MyClass()  
{  
}  
  
private:  
  
};  
```  
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>For, foreach, forr e rfor  
 Sono disponibili quattro diversi frammenti for che forniscono tipi diversi di cicli for.  
  
 Il frammento **for`size_t` rende disponibile un ciclo**  in cui la condizione è basata sulla lunghezza (in `for`) di un oggetto:  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 Il frammento **foreach** rende disponibile un ciclo `for each` che scorre i membri di una raccolta:  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 Il frammento **forr** rende disponibile un ciclo `for` inverso in cui la condizione è basata sulla lunghezza (in numeri interi) di un oggetto:  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 Il frammento **rfor** rende disponibile un ciclo for [basato su intervallo](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) (collegamento):  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>Frammento distruttore (~)  
 Il frammento distruttore (**~**) ha un comportamento diverso in contesti diversi. Se si inserisce questo frammento di codice all'interno di una classe, esso fornisce un distruttore per quella classe. Si consideri, ad esempio, il codice seguente:  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 Se si inserisce il frammento distruttore, esso fornisce un distruttore per SomeClass:  
  
```cpp  
class SomeClass {  
    ~SomeClass()  
    {  
  
    }  
};  
```  
  
 Se si prova a inserire il frammento distruttore all'esterno di una classe, esso fornisce un distruttore con un nome segnaposto:  
  
```cpp  
~TypeNamePlaceholder()  
{  
  
```
