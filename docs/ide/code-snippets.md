---
title: Frammenti di codice
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585418"
---
# <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice sono piccoli blocchi di codice riutilizzabili che possono essere inseriti in un file di codice usando un comando di menu di scelta rapida o una combinazione di tasti di scelta rapida. In genere contengono blocchi di codice di uso comune, ad esempio blocchi `try-finally` o `if-else`, ma possono essere usati per inserire intere classi o metodi.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Frammenti di codice (Visual Studio per Mac)](/visualstudio/mac/snippets).

Sono disponibili frammenti di codice per una vasta gamma di linguaggi, tra cui C#, C++, Visual Basic, XML e T-SQL, per citarne alcuni. Per visualizzare tutti i frammenti di codice installati disponibili per una lingua, aprire **Gestione frammenti di codice** dal menu **strumenti** (oppure premere **ctrl**+**K**, **CTRL**+**B**) e scegliere la lingua dal menu a discesa nella parte superiore.

![Finestra di dialogo Gestione frammenti di codice](media/code-snippets-manager.png)

I frammenti di codice sono accessibili nei modi generali seguenti:

- Nella barra dei menu scegliere **Modifica** > **IntelliSense** > **Inserisci frammento di codice**

- Dal menu di scelta rapida nell'editor del codice scegliere **Frammento** > **Inserisci frammento di codice**

- Dalla tastiera premere **ctrl**+**K**,**CTRL**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Frammenti di espansione e frammenti Racchiudi tra

In Visual Studio sono disponibili due tipi di frammento di codice: frammenti di espansione, che vengono aggiunti in un punto di inserimento specificato e possono sostituire un collegamento al frammento, e frammenti Racchiudi tra (solo C# e C++), che vengono aggiunti a un blocco di codice selezionato.

Un esempio di un frammento di espansione: in C# viene usato il collegamento tryf per inserire un blocco try-finally:

```csharp
try
{

}
finally
{

}
```

Per inserire questo frammento di codice, fare clic su **Inserisci frammento** di codice nel menu di scelta rapida della finestra del codice, quindi su oggetto **C#visivo**, quindi digitare `tryf`, quindi premere **Tab**. In alternativa, è possibile digitare `tryf` e premere due volte **Tab** .

Un esempio di un frammento Racchiudi tra: in C++ il collegamento `if` può essere usato come frammento di inserimento o come frammento Racchiudi tra. Se si seleziona una riga di codice (ad esempio `return FALSE;`) e quindi si sceglie **Racchiudi tra** > **if**, il frammento viene espanso intorno alla riga:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametri di sostituzione del frammento

I frammenti di codice possono contenere parametri di sostituzione, cioè segnaposto che è necessario sostituire per adattare il codice preciso che si scrive. Nell'esempio precedente `true` è un parametro di sostituzione, che è possibile sostituire con la condizione appropriata. La sostituzione effettuata viene ripetuta per ogni istanza dello stesso parametro di sostituzione nel frammento.

Ad esempio, in Visual Basic è presente un frammento di codice che inserisce una proprietà. Per inserire il frammento di codice, scegliere **Frammento** > **Inserisci frammento di codice** dal menu di scelta rapida in un file di codice di Visual Basic. Scegliere quindi **Modelli di codice** > **Proprietà, procedure, eventi** > **Definisci una proprietà**.

![Menu del frammento di codice per Definisci una proprietà](media/code-snippets-vb-property.png)

Viene inserito il codice seguente:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Se si modifica `newPropertyValue` in `m_property`, tutte le istanze di `newPropertyValue` vengono modificate. Se si modifica `String` in `Int` nella dichiarazione di proprietà, anche il valore nel metodo set viene modificato in `Int`.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md)
- [Procedura: Distribuire frammenti di codice](../ide/how-to-distribute-code-snippets.md)
- [Procedure consigliate per l'uso dei frammenti di codice](../ide/best-practices-for-using-code-snippets.md)
- [Risoluzione dei problemi relativi ai frammenti di codice](../ide/troubleshooting-snippets.md)
- [Frammenti di codice C#](../ide/visual-csharp-code-snippets.md)
- [C++frammenti di codice](../ide/visual-cpp-code-snippets.md)
- [Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)
- [Frammenti di codice (Visual Studio per Mac)](/visualstudio/mac/snippets)
