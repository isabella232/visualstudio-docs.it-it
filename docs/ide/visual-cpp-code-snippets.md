---
title: Frammenti di codice Visual C++
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 5069d1b92b9c4f73fdb8eca50eabce170f42cef1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937439"
---
# <a name="visual-c-code-snippets"></a>Frammenti di codice Visual C++

In Visual Studio, è possibile usare frammenti di codice per aggiungere il codice usato comunemente per file di codice C++. In generale, è possibile usare frammenti di codice in modo molto simile a C#, ma il set predefinito di frammenti di codice è diverso.

È possibile aggiungere un frammento di codice in una determinata posizione nel codice (inserimento) o racchiudere il codice selezionato con un frammento di codice.

## <a name="insert-a-code-snippet"></a>Inserire un frammento di codice

Per inserire un frammento di codice, aprire un file di codice C++ (con estensione *cpp* o *h*), fare clic in un punto qualsiasi all'interno del file ed eseguire una delle operazioni seguenti:

- Fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e selezionare **Inserisci frammento di codice**

- Nel menu**Modifica/IntelliSense** selezionare **Inserisci frammento di codice**

- Usare i tasti di scelta rapida: **CTRL**+**K**+**X**

Verrà visualizzato un elenco di opzioni che iniziano con **#if**. Quando si seleziona **#if** il codice seguente viene aggiunto al file:

```cpp
#if 0

#endif // 0
```

È possibile sostituire il valore **0** con la condizione corretta.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Usare un frammento di codice per racchiudere il codice selezionato

Per usare un frammento di codice per racchiudere il codice selezionato, selezionare una riga (o più righe) ed eseguire una delle operazioni seguenti:

- Fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere **Racchiudi tra**

- Nel menu **Modifica** > **IntelliSense** selezionare **Racchiudi tra**

- Se si usa la tastiera, premere: **CTRL**+**K**+**S**

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

Il frammento di codice **class** specifica la definizione di una classe denominata `MyClass`, con il costruttore e il distruttore predefiniti appropriati, dove le definizioni del costruttore e del distruttore si trovano all'esterno della classe:

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

Anche il frammento di codice **classi** specifica la definizione di una classe denominata `MyClass`, ma il costruttore e il distruttore predefiniti sono definiti nella definizione della classe:

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

## <a name="for-vs-forr-vs-rfor"></a>for, forr e rfor

Sono disponibili tre diversi frammenti **for** che specificano tipi diversi di cicli `for`.

Il frammento **rfor** rende disponibile un ciclo for [basato su intervallo](/cpp/cpp/range-based-for-statement-cpp) (collegamento). Questo costrutto è da preferire rispetto ai cicli `for` basati su indice.

```cpp
for (auto& i : v)
{

}
```

Il frammento **for** rende disponibile un ciclo `for` in cui la condizione è basata sulla lunghezza (in `size_t`) di un oggetto.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

Il frammento **forr** rende disponibile un ciclo `for` inverso in cui la condizione è basata sulla lunghezza (in numeri interi) di un oggetto.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Frammento distruttore (~)

Il frammento distruttore (**~**) ha un comportamento diverso in contesti diversi. Se si inserisce questo frammento di codice all'interno di una classe, esso fornisce un distruttore per quella classe. Si consideri, ad esempio, il codice seguente:

```cpp
class SomeClass {

};
```

Se si inserisce il frammento di codice per il distruttore, esso specifica un distruttore per `SomeClass`:

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

## <a name="see-also"></a>Vedere anche

- [Frammenti di codice](../ide/code-snippets.md)