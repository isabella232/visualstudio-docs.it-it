---
title: Procedura dettagliata per l'analisi del codice gestito per i difetti del codice | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548003"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Procedura dettagliata: Usare l'analisi del codice statica per individuare i difetti del codice

In questa procedura dettagliata si analizzerà un progetto gestito per i difetti del codice usando l'analisi del codice legacy.

Questo articolo illustra il processo di utilizzo dell'analisi legacy per analizzare gli assembly di codice gestito .NET per conformità con le linee guida di progettazione .NET.

## <a name="create-a-class-library"></a>Creare una libreria di classi

### <a name="to-create-a-class-library"></a>Per creare una libreria di classi

1. Nel menu **File** scegliere **Nuovo** > **Progetto**.

1. Nella finestra di dialogo **nuovo progetto** espandere oggetto**visivo C#**  **installato** > , quindi scegliere **desktop di Windows**.

1. Scegliere il modello **libreria di classi (.NET Framework)** .

1. Nella casella di testo **nome** digitare **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.

1. Dopo aver creato il progetto, aprire il file *Class1.cs* .

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

1. Selezionare il progetto CodeAnalysisManagedDemo in **Esplora soluzioni**.

1. Scegliere **Proprietà** dal menu **Progetto**.

     Verrà visualizzata la pagina delle proprietà CodeAnalysisManagedDemo.

1. Scegliere la scheda **analisi codice** .

1. Assicurarsi che l'opzione **Abilita analisi codice su compilazione** sia selezionata.

1. Dall'elenco a discesa **Esegui questo set di regole** selezionare **Microsoft all Rules**.

1. Scegliere **Salva elementi selezionati**dal menu **file** e quindi chiudere le pagine delle proprietà.

1. Scegliere **Compila CodeAnalysisManagedDemo**dal menu **Compila** .

    Gli avvisi di compilazione del progetto CodeAnalysisManagedDemo sono visualizzati nelle finestre **Elenco errori** e **output** .

## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi del codice

### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere le violazioni delle regole di analisi del codice

1. Scegliere **Elenco errori**dal menu **Visualizza** .

    A seconda del profilo dello sviluppatore scelto, potrebbe essere necessario puntare ad **altre finestre** dal menu **Visualizza** , quindi scegliere **Elenco errori**.

1. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

1. Espandere il nodo Proprietà, quindi aprire il file *AssemblyInfo.cs* .

1. Usare i suggerimenti seguenti per correggere gli avvisi:

   [CA1014 Contrassegnare gli assembly](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)con CLSCompliantAttribute: Microsoft. Design:' demo ' deve essere contrassegnato con CLSCompliantAttribute e il relativo valore deve essere true.

   1. Aggiungere il codice `using System;` al file AssemblyInfo.cs.

   1. Aggiungere quindi il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.

   [CA1032: Implementare costruttori](../code-quality/ca1032-implement-standard-exception-constructors.md)di eccezioni standard: Microsoft.Design: Aggiungere il costruttore seguente alla classe: public demo (String)

   1. Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe. `demo`

   [CA1032: Implementare costruttori](../code-quality/ca1032-implement-standard-exception-constructors.md)di eccezioni standard: Microsoft.Design: Aggiungere il costruttore seguente alla classe: public demo (String, Exception)

   1. Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe. `demo`

   [CA1032: Implementare costruttori](../code-quality/ca1032-implement-standard-exception-constructors.md)di eccezioni standard: Microsoft.Design: Aggiungere il seguente costruttore a questa classe: protected demo (SerializationInfo, StreamingContext)

   1. Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1.cs.

   1. Aggiungere quindi il costruttore`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementare costruttori](../code-quality/ca1032-implement-standard-exception-constructors.md)di eccezioni standard: Microsoft.Design: Aggiungere il costruttore seguente alla classe: public demo ()

   1. Aggiungere il costruttore `public demo () : base() { }` alla classe `demo` **.**

   [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: Correggere la combinazione di maiuscole e minuscole del nome dello spazio dei nomi ' testCode ' cambiandola in ' TestCode '.

   1. Modificare le maiuscole e minuscole `TestCode`dello spazio dei nomi `testCode` in.

   [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: Correggere la combinazione di maiuscole e minuscole del nome di tipo "demo" cambiandola in "demo".

   1. Modificare il nome del membro in `Demo`.

   [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: Correggere la combinazione di maiuscole e minuscole del nome del membro ' Item ' cambiandola in ' Item '.

   1. Modificare il nome del membro in `Item`.

   [CA1710 Gli identificatori devono avere il](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)suffisso corretto: Microsoft. Naming: Rinominare "testCode. demo" per terminare con "Exception".

   1. Modificare il nome della classe e i relativi costruttori in `DemoException`.

   [CA2210 Gli assembly devono avere nomi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)sicuri validi: Firmare ' CodeAnalysisManagedDemo ' con una chiave con nome sicuro.

   1. Scegliere **Proprietà CodeAnalysisManagedDemo**dal menu **progetto** .

      Verranno visualizzate le proprietà del progetto.

   1. Scegliere la scheda **Firma** .

   1. Selezionare la casella di controllo **Firma assembly** .

   1. Nell'elenco **Scegli un file chiave con nome stringa** selezionare  **\<nuovo... >** .

      Verrà visualizzata la finestra di dialogo **Crea chiave con nome sicuro** .

   1. Nel **nome del file di chiave**digitare TestKey.

   1. Immettere una password, quindi scegliere **OK**.

   1. Scegliere **Salva elementi selezionati**dal menu **file** e quindi chiudere le pagine delle proprietà.

   [CA2237: Contrassegnare i tipi ISerializable](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)con SerializableAttribute: Microsoft.Usage: Aggiungere un attributo [Serializable] al tipo ' demo ' poiché questo tipo implementa ISerializable.

   1. Aggiungere l' `[Serializable ()]` attributo alla classe `demo`.

   Una volta completate le modifiche, il file Class1.cs dovrebbe essere simile al seguente:

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

## <a name="exclude-code-analysis-warnings"></a>Escludi avvisi di analisi codice

1. Per ogni avviso rimanente, procedere come segue:

    1. Selezionare l'avviso nella **Elenco errori**.

    1. Dal menu di scelta rapida (menu di scelta rapida) scegliere **Elimina** > **nel file di eliminazione**.

1. Ricompilare il progetto.

     Il progetto viene compilato senza avvisi o errori.

## <a name="see-also"></a>Vedere anche

[Analisi codice per codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)