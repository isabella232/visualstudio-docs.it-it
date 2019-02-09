---
title: Procedura dettagliata di analisi del codice gestito per i difetti del codice | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3097e52f99f044257b8eaf634455bdf19978d0c3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952841"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procedura dettagliata: Analisi del codice gestito per i difetti del codice

In questa procedura dettagliata, si sarà analizzare un progetto gestito per i difetti del codice utilizzando lo strumento di analisi codice.

Questa procedura dettagliata viene illustrato il processo di uso di analisi del codice per analizzare gli assembly di codice .NET gestita per verificare la conformità alle linee guida per la progettazione di Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Creare una libreria di classi

### <a name="to-create-a-class-library"></a>Per creare una libreria di classi

1. Nel menu **File** scegliere **Nuovo** > **Progetto**.

1. Nel **nuovo progetto** finestra di dialogo, espandere **installato** > **Visual c#**, quindi scegliere **Desktop di Windows**.

1. Scegliere il **libreria di classi (.NET Framework)** modello.

1. Nel **Name** casella di testo, digitare **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.

1. Dopo aver creato il progetto, aprire il *Class1.cs* file.

1. Sostituire il testo esistente in Class1.cs con il codice seguente:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Salvare il file Class1.cs.

## <a name="analyze-the-project"></a>Analizzare il progetto

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Per analizzare un progetto gestito per i difetti del codice

1. Selezionare il progetto CodeAnalysisManagedDemo **Esplora soluzioni**.

1. Scegliere **Proprietà** dal menu **Progetto**.

     Verrà visualizzata la pagina di proprietà CodeAnalysisManagedDemo.

1. Scegliere il **analisi del codice** scheda.

1. Verificare che l'opzione **Abilita analisi codice su compilazione** sia selezionata.

1. Dal **eseguire questo set di regole** elenco a discesa, seleziona **tutte le regole Microsoft**.

1. Nel **File** menu, fare clic su **Salva elementi selezionati**e quindi chiudere le pagine delle proprietà.

1. Nel **compilare** menu, fare clic su **compilare CodeAnalysisManagedDemo**.

    Gli avvisi di compilazione progetto CodeAnalysisManagedDemo vengono visualizzati nei **elenco errori** e **Output** windows.

## <a name="correct-the-code-analysis-issues"></a>Risolvere i problemi di analisi del codice

### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere delle violazioni delle regole di analisi codice

1. Nel **View** menu, scegliere **elenco errori**.

    A seconda del profilo sviluppatore scelto, potrebbe essere necessario scegliere **Other Windows** nel **View** dal menu e quindi scegliere **elenco errori**.

1. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

1. Espandere il nodo di proprietà e quindi aprire il *AssemblyInfo.cs* file.

1. Usare i suggerimenti seguenti per risolvere gli avvisi:

   [CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: "demo" deve essere contrassegnato con CLSCompliantAttribute e relativo valore deve essere true.

   1. Aggiungere il codice `using System;` nel file AssemblyInfo.cs.

   1. Successivamente, aggiungere il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: pubblica demo (String)

   1. Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo`.

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: demo pubblico (String, eccezione)

   1. Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo`.

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: protetti demo (SerializationInfo, StreamingContext)

   1. Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1.cs.

   1. Successivamente, aggiungere il costruttore `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: demos pubblico

   1. Aggiungere il costruttore `public demo () : base() { }` alla classe `demo` **.**

   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Correggere le maiuscole e minuscole del nome dello spazio dei nomi 'testCode' modificandolo in 'TestCode'.

   1. Modifica le maiuscole e minuscole dei nomi `testCode` a `TestCode`.

   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Correggere le maiuscole e minuscole di tipo nome "demo" modificandolo in "Demo".

   1. Modificare il nome del membro da `Demo`.

   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Correggere le maiuscole e minuscole del membro nome 'item' modificandolo in 'Item'.

   1. Modificare il nome del membro da `Item`.

   [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Rinominare 'testCode.demo' per terminare con 'Exception'.

   1. Modificare il nome della classe e i relativi costruttori in `DemoException`.

   [CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Firmare 'CodeAnalysisManagedDemo' con una chiave con nome sicuro.

   1. Nel **Project** menu, scegliere **CodeAnalysisManagedDemo proprietà**.

      Vengono visualizzate le proprietà del progetto.

   1. Scegliere la scheda **Firma** .

   1. Selezionare il **firmare l'assembly** casella di controllo.

   1. Nel **scegliere un file chiave con nome sicuro** elenco, selezionare  **\<nuovo... >**.

      Il **Crea chiave con nome sicuro** verrà visualizzata la finestra di dialogo.

   1. Nel **nome file di chiave**, digitare TestKey.

   1. Immettere una password e quindi scegliere **OK**.

   1. Nel **File** menu, scegliere **Salva elementi selezionati**e quindi chiudere le pagine delle proprietà.

   [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Aggiungere un attributo [Serializable] a 'demo' perché questo tipo implementa ISerializable.

   1. Aggiungere il `[Serializable ()]` alla classe `demo`.

   Dopo aver completato le modifiche, il file Class1.cs dovrebbe essere simile al seguente:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Ricompilare il progetto.

## <a name="exclude-code-analysis-warnings"></a>Escludere gli avvisi dell'analisi codice

1. Per ognuno degli altri avvisi, eseguire le operazioni seguenti:

    1. Selezionare l'avviso nel **elenco errori**.

    1. Dal menu di scelta rapida (menu di scelta rapida), scegliere **Suppress** > **nel File di eliminazione**.

1. Ricompilare il progetto.

     Il progetto viene compilato senza eventuali avvisi o errori.

## <a name="see-also"></a>Vedere anche

[Analisi del codice per il codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)