---
title: Dividere una classe in classi parziali
description: Informazioni su come usare la parola chiave partial per dividere la dichiarazione di una classe o di una struttura tra più dichiarazioni in Progettazione classi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9a29aed406d216e2fd72d9763cd9d0522f9cdd17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951823"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Procedura: Dividere una classe in classi parziali in Progettazione classi

È possibile usare la parola chiave `partial` (`Partial` in Visual Basic) per dividere la dichiarazione di una classe o struttura in più dichiarazioni. È possibile usare tutte le dichiarazioni parziali che si desidera.

Le dichiarazioni possono essere in uno o più file di origine. Tutte le dichiarazioni devono trovarsi nello stesso assembly e nello stesso spazio dei nomi.

Le classi parziali sono utili in varie situazioni. In un progetto di grandi dimensioni, ad esempio, la separazione di una classe in più file consente a più programmatori di lavorare sul progetto contemporaneamente. Quando si lavora con il codice generato da Visual Studio, è possibile modificare la classe senza dover ricreare il file di origine. Esempi di codice generato da Visual Studio includono Windows Form e il codice wrapper del servizio Web. È quindi possibile creare codice che usa le classi generate automaticamente senza dover modificare il file creato da Visual Studio.

Esistono due tipi di metodi parziali, chiamati dichiarazione e implementazione in C# e Visual Basic.

**Progettazione classi** supporta classi e metodi parziali. La forma del tipo nel diagramma classi fa riferimento a una singola posizione di dichiarazione per la classe parziale. Se la classe parziale è definita in più file, è possibile specificare il percorso della dichiarazione che **Progettazione classi** utilizzerà impostando la proprietà **percorso nuovo membro** nella finestra **proprietà** . Ovvero, quando si fa doppio clic su una forma di classe, **Progettazione classi** passa al file di origine che contiene la dichiarazione di classe identificata dalla **nuova proprietà Location del membro** . Quando si fa doppio clic su un metodo parziale in una forma di classe, **Progettazione classi** passa alla dichiarazione del metodo parziale. Inoltre, nella finestra **Proprietà** la proprietà **Nome file** fa riferimento alla posizione di dichiarazione. Per le classi parziali, **Nome file** elenca tutti i file che contengono codice di dichiarazione e implementazione per tale classe. Per i metodi parziali, tuttavia, **Nome file** elenca solo il file che contiene la dichiarazione del metodo parziale.

L'esempio seguente suddivide la definizione della classe `Employee` in due dichiarazioni, ognuna delle quali definisce una routine differente. Le due definizioni parziali negli esempi possono trovarsi in un singolo file di origine o in due file di origine differenti.

> [!NOTE]
> Visual Basic usa definizioni di classi parziali per separare il codice generato da Visual Studio dal codice creato dall'utente. Il codice viene separato in file di origine distinti. Ad esempio, **Progettazione Windows Form** definisce classi parziali per controlli come `Form`. In questi controlli il codice generato non deve essere modificato.

Per altre informazioni sui tipi parziali in Visual Basic, vedere [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Esempio

Per suddividere una definizione di classe, usare la parola chiave `partial` (`Partial` in Visual Basic), come illustrato nell'esempio seguente:

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Vedi anche

- [Classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (Tipo) (Riferimenti per C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [parziale (Metodo) (Riferimenti per C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
