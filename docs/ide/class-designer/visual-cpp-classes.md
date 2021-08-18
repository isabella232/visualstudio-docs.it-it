---
title: Classi C++ in Progettazione classi
description: Informazioni sulle classi C++ e su come sono supportate e possono avere più relazioni di ereditarietà in Progettazione classi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: bad6d017bfe58af9a514f632b4bf1fc3047cb054
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094490"
---
# <a name="c-classes-in-class-designer"></a>Classi C++ in Progettazione classi

**Progettazione classi** supporta le classi C++ e visualizza classi C++ native in modo analogo alle forme di classe di Visual Basic e C#, con la differenza che le classi C++ possono avere più relazioni di ereditarietà. È possibile espandere la forma classe in modo da visualizzare più campi e metodi nella classe o comprimerla per risparmiare spazio.

> [!NOTE]
> **Progettazione classi** non supporta le unioni (un tipo speciale di classe in cui la memoria allocata è solo la quantità necessaria per il membro dati più grande dell'unione).

## <a name="simple-inheritance"></a>Ereditarietà semplice

Quando si trascina più di una classe su un diagramma classi, le classi che presentano una relazione di ereditarietà di classe sono connesse con una freccia che punta nella direzione della classe di base. Ad esempio, quando vengono visualizzate in un diagramma classi, le classi seguenti sono connesse con una freccia che parte da B e arriva ad A:

```cpp
class A {};
class B : A {};
```

È anche possibile trascinare solo la classe B sul diagramma classi, fare clic col pulsante destro del mouse sulla forma classe relativa a B e quindi fare clic su **Mostra classi base** per visualizzare la relativa classe di base, ovvero A.

## <a name="multiple-inheritance"></a>Ereditarietà multipla

**Progettazione classi** supporta la visualizzazione di relazioni di ereditarietà a più classi. L'*ereditarietà multipla* viene usata quando una classe derivata presenta attributi di più di una classe di base. Di seguito è riportato un esempio di ereditarietà multipla:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Quando si trascina più di una classe sul diagramma classi, le classi che presentano una relazione di ereditarietà da classi multiple sono connesse con una freccia che punta nella direzione delle classi di base.

Facendo clic con il pulsante destro del mouse su una forma classe e scegliendo **Mostra classi base** vengono visualizzate le classi di base per la classe selezionata.

> [!NOTE]
> Il comando **Mostra classi derivate** non è supportato per il codice C++. Per visualizzare le classi derivate, scegliere **Visualizzazione classi**, espandere il nodo dei tipi, espandere la sottocartella **Tipi derivati** e trascinare tali tipi sul diagramma classi.

Per altre informazioni sulle ereditarietà da classi multiple, vedere [Ereditarietà multipla](/previous-versions/6td5yws2(v=vs.140)) e [Più classi base](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Classi astratte

**Progettazione classi** supporta le classi astratte, note anche come "classi di base astratte". Si tratta di classi per le quali non viene mai creata un'istanza, ma da cui è possibile derivare altre classi. Usando un esempio citato in "Ereditarietà multipla" più indietro in questo documento, è possibile creare un'istanza della classe `Bird` come singoli oggetti, come illustrato di seguito:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

È però possibile che non si intenda creare un'istanza della classe `Swimmer` come singoli oggetti e che si intenda solo usarla per derivare altri tipi di classi di animali, ad esempio `Penguin`, `Whale` e `Fish`. In tal caso, è necessario dichiarare la classe `Swimmer` come classe di base astratta.

Per dichiarare una classe come astratta, si può usare la parola chiave `abstract`. I membri contrassegnati come astratti o inclusi in una classe astratta sono virtuali e devono essere implementati dalle classi che derivano dalla classe astratta.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

È anche possibile dichiarare una classe come astratta includendo almeno una funzione virtuale pura:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Quando si visualizzano queste dichiarazioni in un diagramma classi, il nome della classe `Swimmer` e la relativa funzione virtuale pura `swim` vengono visualizzate in corsivo in una forma classe astratta, unitamente alla notazione **Classe astratta**. Si noti che la forma tipo di classe astratta è uguale a quella di una classe normale, ad eccezione del fatto che il bordo è costituito da una linea punteggiata.

Una classe derivata da una classe di base astratta deve eseguire l'override di ogni funzione virtuale pura della classe di base, altrimenti non è possibile creare un'istanza della classe derivata. Se, ad esempio, si deriva una classe `Fish` dalla classe `Swimmer`, `Fish` deve eseguire l'override del metodo `swim`:

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Quando si visualizza questo codice in un diagramma **classi,** Progettazione classi traccia una linea di ereditarietà da `Fish` a `Swimmer` .

## <a name="anonymous-classes"></a>Classi anonime

**Progettazione classi** supporta le classi anonime. I *tipi di classe anonimi* sono classi dichiarate senza un identificatore. Non possono includere un costruttore o un distruttore, non possono essere passate come argomenti alle funzioni e non possono essere restituite come valori restituiti dalle funzioni. È possibile usare una classe anonima per sostituire un nome di classe con un nome typedef, come nell'esempio seguente:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Anche le strutture possono essere anonime. **Progettazione classi** visualizza le classi e le strutture anonime nello stesso modo in cui visualizza il rispettivo tipo. Sebbene sia possibile dichiarare e visualizzare classi e strutture anonime, **Progettazione classi** non userà il nome del tag specificato. ma usa il nome generato da Visualizzazione classi. La classe o la struttura viene visualizzata Visualizzazione classi e **Progettazione classi** come elemento denominato **__unnamed**.

Per altre informazioni sulle classi anonime, vedere [Tipi di classe anonimi](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Classi modello

**Progettazione classi** supporta la visualizzazione di classi modello, nonché le dichiarazioni annidate. La tabella seguente illustra alcune dichiarazioni tipiche.

| Elemento del codice | Visualizzazione di Progettazione classi |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Classe modello |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Classe modello |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Classe modello |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Classe modello |

La tabella seguente illustra alcuni esempi di specializzazione parziale.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe modello|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Classe modello|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Classe modello|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Classe modello|

La tabella seguente illustra alcuni esempi di ereditarietà nella specializzazione parziale.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Classe modello<br /><br /> `B`<br /><br /> Classe<br /><br /> (punta alla classe A)<br /><br /> `C`<br /><br /> Classe<br /><br /> (punta alla classe A)|

La tabella seguente illustra alcuni esempi di funzioni del modello di specializzazione parziale.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func \<T, U> (+ 1 overload)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Classe modello<br /><br /> `B<T2>`<br /><br /> Classe modello<br /><br /> (B è contenuto all'interno della classe A in **Tipi annidati**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Classe<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Classe modello|

La tabella seguente illustra alcuni esempi di ereditarietà del modello.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Classe<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Classe<br /><br /> (B è contenuto all'interno della classe C in **Tipi annidati**)<br /><br /> `C<T>`<br /><br /> Classe modello|

La tabella seguente illustra alcuni esempi di tipica connessione di classe specializzata.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Classe<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Classe<br /><br /> `C<T>`<br /><br /> Classe modello<br /><br /> `D`<br /><br /> Classe<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Minimo \<T>|

## <a name="see-also"></a>Vedi anche

- [Uso del codice C++](working-with-visual-cpp-code.md)
- [Classi e struct](/cpp/cpp/classes-and-structs-cpp)
- [Tipi di classe anonimi](/cpp/cpp/anonymous-class-types)
- [Ereditarietà multipla](/previous-versions/6td5yws2(v=vs.140))
- [Più classi di base](/cpp/cpp/multiple-base-classes)
- [Modelli](/cpp/cpp/templates-cpp)