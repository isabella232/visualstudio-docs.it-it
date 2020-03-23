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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585418"
---
# <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice sono piccoli blocchi di codice riutilizzabili che possono essere inseriti in un file di codice usando un comando di menu di scelta rapida o una combinazione di tasti di scelta rapida. In genere contengono blocchi di codice di uso comune, ad esempio blocchi `try-finally` o `if-else`, ma possono essere usati per inserire intere classi o metodi.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Frammenti di codice (Visual Studio per Mac)](/visualstudio/mac/snippets).

Sono disponibili frammenti di codice per una vasta gamma di linguaggi, tra cui C#, C++, Visual Basic, XML e T-SQL, per citarne alcuni. Per visualizzare tutti i frammenti installati disponibili per una lingua, aprire **Gestione frammenti** di codice dal menu **Strumenti** (oppure, premere **Ctrl**+**K**, **Ctrl**+**B**) e scegliere la lingua dal menu a discesa nella parte superiore.

![Finestra di dialogo Gestione frammenti di codice](media/code-snippets-manager.png)

I frammenti di codice sono accessibili nei modi generali seguenti:

- Nella barra dei menu scegliere **Modifica** > **frammento di codice** **IntelliSense** > 

- Dal menu di scelta rapida o dal menu di scelta rapida nell'editor di codice, scegliere **Snippet** > **Insert Snippet**

- Dalla tastiera, premere **Ctrl**+**K**,**Ctrl**+**X**

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

È possibile inserire questo frammento di codice facendo clic su **Inserisci frammento** di codice nel `tryf`menu di scelta rapida (menu di scelta rapida) della finestra del codice, quindi in Visual Basic , quindi in Visual **Basic**, digitare , quindi premere **TAB**. In alternativa, `tryf` è possibile digitare e premere **TAB** due volte.

Un esempio di un frammento Racchiudi tra: in C++ il collegamento `if` può essere usato come frammento di inserimento o come frammento Racchiudi tra. Se selezionate una riga di `return FALSE;`codice (ad esempio ) e scegliete **Circonda con** > **se**, il frammento di codice viene espanso intorno alla riga:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametri di sostituzione del frammento

I frammenti di codice possono contenere parametri di sostituzione, cioè segnaposto che è necessario sostituire per adattare il codice preciso che si scrive. Nell'esempio precedente `true` è un parametro di sostituzione, che è possibile sostituire con la condizione appropriata. La sostituzione effettuata viene ripetuta per ogni istanza dello stesso parametro di sostituzione nel frammento.

Ad esempio, in Visual Basic è presente un frammento di codice che inserisce una proprietà. Per inserire il frammento di codice, scegliere **Frammento** > di**codice Inserisci frammento** di codice dal menu di scelta rapida o con scelta rapida in un file di codice Visual Basic.To insert the snippet, choose Snippet Insert Snippet from the right-click or context menu in a Visual Basic code file. Scegliere quindi **Proprietà modelli** > di**codice, Procedure, Eventi** > **Definizione proprietà**.

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

- [Procedura dettagliata: creazione di un frammento di codiceWalkthrough: Creating a code snippet](../ide/walkthrough-creating-a-code-snippet.md)
- [Procedura: distribuire frammenti di codiceHow to: Distribute code snippets](../ide/how-to-distribute-code-snippets.md)
- [Procedure consigliate per l'utilizzo di frammenti di codiceBest practices for using code snippets](../ide/best-practices-for-using-code-snippets.md)
- [Risoluzione dei problemi relativi agli snippetTroubleshooting snippets](../ide/troubleshooting-snippets.md)
- [Frammenti di codice di C](../ide/visual-csharp-code-snippets.md)
- [Frammenti di codice di C](../ide/visual-cpp-code-snippets.md)
- [Informazioni di riferimento sullo schema dei frammenti di codiceCode snippets schema reference](../ide/code-snippets-schema-reference.md)
- [Frammenti di codice (Visual Studio per Mac)](/visualstudio/mac/snippets)
