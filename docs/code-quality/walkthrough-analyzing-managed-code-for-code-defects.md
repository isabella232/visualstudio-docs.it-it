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
ms.openlocfilehash: ab1e0b890d6241742770ed38ff61fc1c2c0ed2f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72535697"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Procedura dettagliata: usare l'analisi del codice statica per individuare i difetti del codice

In questa procedura dettagliata si analizzerà un progetto gestito per i difetti del codice usando l'analisi del codice legacy.

Questo articolo illustra il processo di utilizzo dell'analisi legacy per analizzare gli assembly di codice gestito .NET per conformità con le linee guida di progettazione .NET.

## <a name="create-a-class-library"></a>Creare una libreria di classi

1. Aprire Visual Studio e creare un nuovo progetto dal modello **libreria di classi (.NET Framework)** .

1. Denominare il progetto **CodeAnalysisManagedDemo**.

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

## <a name="analyze-the-project-for-code-defects"></a>Analizzare il progetto per i difetti del codice

1. Selezionare il progetto CodeAnalysisManagedDemo in **Esplora soluzioni**.

2. Scegliere **Proprietà** dal menu **Progetto**.

   Verrà visualizzata la pagina delle proprietà CodeAnalysisManagedDemo.

3. Scegliere la scheda **analisi codice** .

::: moniker range="vs-2017"

4. Assicurarsi che l'opzione **Abilita analisi codice su compilazione** sia selezionata.

5. Dall'elenco a discesa **Esegui questo set di regole** selezionare **Microsoft all Rules**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Assicurarsi che l'opzione **Esegui su compilazione** sia selezionata nella sezione **analizzatori binari** .

5. Dall'elenco a discesa **regole attive** selezionare **Microsoft all Rules**.

::: moniker-end

6. Scegliere **Salva elementi selezionati**dal menu **file** e quindi chiudere le pagine delle proprietà.

7. Scegliere **Compila CodeAnalysisManagedDemo**dal menu **Compila** .

    Gli avvisi di compilazione del progetto CodeAnalysisManagedDemo sono visualizzati nelle finestre **Elenco errori** e **output** .

## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi del codice

1. Scegliere **Elenco errori**dal menu **Visualizza** .

    A seconda del profilo dello sviluppatore scelto, potrebbe essere necessario puntare ad **altre finestre** dal menu **Visualizza** , quindi scegliere **Elenco errori**.

1. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

1. Espandere il nodo Proprietà, quindi aprire il file *AssemblyInfo.cs* .

1. Usare i suggerimenti seguenti per correggere gli avvisi:

   [CA1014: contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014.md): aggiungere il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.

   [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032.md): aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo` .

   [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032.md): aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo` .

   [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032.md): aggiungere il costruttore `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` alla classe demo. Sarà inoltre necessario aggiungere un' `using` istruzione per <xref:System.Runtime.Serialization?displayProperty=fullName> .

   [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032.md): aggiungere il costruttore `public demo () : base() { }` alla classe `demo` .

   [CA1709: gli identificatori devono essere configurati correttamente](../code-quality/ca1709.md): modificare la combinazione di maiuscole e minuscole dello spazio dei nomi `testCode` in `TestCode` .

   [CA1709: gli identificatori devono essere configurati correttamente](../code-quality/ca1709.md): modificare il nome del membro in `Demo` .

   [CA1709: gli identificatori devono essere configurati correttamente](../code-quality/ca1709.md): modificare il nome del membro in `Item` .

   [CA1710: gli identificatori devono avere il suffisso corretto](../code-quality/ca1710.md): modificare il nome della classe e i relativi costruttori in `DemoException` .

   [CA2237: contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237.md): aggiungere l' `[Serializable ()]` attributo alla classe `demo` .

   [CA2210: gli assembly devono avere nomi sicuri validi](../code-quality/ca2210.md): Sign ' CodeAnalysisManagedDemo ' con una chiave con nome sicuro:

   1. Scegliere **Proprietà CodeAnalysisManagedDemo**dal menu **progetto** .

      Verranno visualizzate le proprietà del progetto.

   1. Scegliere la scheda **Firma** .

   1. Selezionare la casella di controllo **Firma assembly** .

   1. Nell'elenco **scegliere un file di chiave con nome stringa** selezionare **\<New>** .

      Verrà visualizzata la finestra di dialogo **Crea chiave con nome sicuro**.

   1. Per **nome file di chiave**immettere **TestKey**.

   1. Immettere una password, quindi scegliere **OK**.

   1. Scegliere **Salva elementi selezionati**dal menu **file** e quindi chiudere le pagine delle proprietà.

   Dopo aver completato tutte le modifiche, il file Class1.cs dovrebbe essere simile al seguente:

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

    1. Dal menu di scelta rapida (menu di scelta rapida) scegliere **Elimina**  >  **nel file di eliminazione**.

1. Ricompilare il progetto.

     Il progetto viene compilato senza avvisi o errori.

## <a name="see-also"></a>Vedere anche

[Analisi codice per il codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)
