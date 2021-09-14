---
title: Procedura dettagliata Analisi del codice gestito per i difetti del | Microsoft Docs
ms.date: 01/29/2018
description: Informazioni su come usare l'analisi del codice legacy per analizzare gli assembly di codice gestito .NET. Vedere come verificare la presenza di difetti e la conformità alle linee guida di progettazione .NET.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: b93e0cb2a3b74fe26b60094eb74d010e0b1f77ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631799"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Procedura dettagliata: Usare l'analisi statica del codice per trovare i difetti del codice

In questa procedura dettagliata si analerà un progetto gestito per i difetti del codice usando l'analisi del codice legacy.

Questo articolo illustra il processo di uso dell'analisi legacy per analizzare gli assembly di codice gestito .NET per verificarne la conformità alle linee guida di progettazione .NET.

## <a name="create-a-class-library"></a>Creare una libreria di classi

1. Aprire Visual Studio e creare un nuovo progetto dal modello Libreria **di classi (.NET Framework).**

1. Assegnare al progetto **il nome CodeAnalysisManagedDemo**.

1. Dopo aver creato il progetto, aprire il file *Class1.cs.*

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

   Viene visualizzata la pagina delle proprietà CodeAnalysisManagedDemo.

3. Scegliere la **Code Analysis** dati.

::: moniker range="vs-2017"

4. Assicurarsi che **l'opzione Code Analysis in compilazione** sia selezionata.

5. **Nell'elenco a discesa Run this rule set** (Esegui questo set di regole) selezionare Microsoft All Rules **(Tutte le regole Microsoft).**

::: moniker-end

::: moniker range=">=vs-2019"

4. Assicurarsi che **l'opzione Esegui in fase** di compilazione sia selezionata nella sezione **Analizzatori binari.**

5. **Nell'elenco a** discesa Regole attive selezionare **Tutte le regole Microsoft.**

::: moniker-end

6. Scegliere **Salva** elementi selezionati **dal** menu File , quindi chiudere le pagine delle proprietà.

7. Scegliere **Compila** **CodeAnalysisManagedDemo** dal menu Compila.

    Gli avvisi di compilazione del progetto CodeAnalysisManagedDemo vengono visualizzati nelle **finestre Elenco errori** e **Output.**

## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi del codice

1. Scegliere **Elenco** errori **dal** menu Visualizza .

    A seconda del profilo di sviluppatore scelto, potrebbe essere necessario scegliere **Altro Windows** **dal** menu Visualizza e quindi scegliere **Elenco errori.**

1. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

1. Espandere il nodo Proprietà e quindi aprire il file *AssemblyInfo.cs.*

1. Usare i suggerimenti seguenti per correggere gli avvisi:

   [CA1014: Contrassegnare](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)gli assembly con CLSCompliantAttribute : Aggiungere il codice alla fine del `[assembly: CLSCompliant(true)]` file AssemblyInfo.cs.

   [CA1032: Implementare costruttori di eccezioni standard:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)Aggiungere il `public demo (String s) : base(s) { }` costruttore alla classe `demo` .

   [CA1032: Implementare costruttori di eccezioni standard:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)Aggiungere il `public demo (String s, Exception e) : base(s, e) { }` costruttore alla classe `demo` .

   [CA1032: Implementare costruttori di eccezioni standard:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)Aggiungere il `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` costruttore alla demo della classe. È anche necessario aggiungere `using` un'istruzione per <xref:System.Runtime.Serialization?displayProperty=fullName> .

   [CA1032: Implementare costruttori di eccezioni standard:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)Aggiungere il `public demo () : base() { }` costruttore alla classe `demo` .

   [CA1709: Per](../code-quality/ca1709.md)gli identificatori è necessario fare correttamente distinzione tra maiuscole e minuscole: modificare la distinzione tra maiuscole e minuscole dello spazio `testCode` dei nomi in `TestCode` .

   [CA1709: Per](../code-quality/ca1709.md)gli identificatori deve essere corretta la distinzione tra maiuscole e minuscole: modificare il nome del membro in `Demo` .

   [CA1709: Per](../code-quality/ca1709.md)gli identificatori deve essere corretta la distinzione tra maiuscole e minuscole: modificare il nome del membro in `Item` .

   [CA1710: Gli identificatori devono avere il suffisso corretto:](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)Modificare il nome della classe e i relativi costruttori in `DemoException` .

   [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](/dotnet/fundamentals/code-analysis/quality-rules/ca2237): Aggiungere `[Serializable ()]` l'attributo alla classe `demo` .

   [CA2210: Gli](../code-quality/ca2210.md)assembly devono avere nomi sicuri validi: Firmare 'CodeAnalysisManagedDemo' con una chiave con nome sicuro:

   1. Nel menu **Project** scegliere **Proprietà CodeAnalysisManagedDemo.**

      Vengono visualizzate le proprietà del progetto.

   1. Scegliere la scheda **Firma** .

   1. Selezionare la **casella di controllo Firma assembly.**

   1. **Nell'elenco Choose a string name key file** (Scegliere un file di chiave del nome stringa) selezionare **\<New>** .

      Verrà visualizzata la finestra di dialogo **Crea chiave con nome sicuro**.

   1. Per **Nome file di chiave** immettere **TestKey**.

   1. Immettere una password e quindi scegliere **OK.**

   1. Scegliere **Salva** elementi **selezionati** dal menu File , quindi chiudere le pagine delle proprietà.

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

## <a name="exclude-code-analysis-warnings"></a>Escludere avvisi di analisi del codice

1. Per ognuno degli avvisi rimanenti, eseguire le operazioni seguenti:

    1. Selezionare l'avviso in **Elenco errori**.

    1. Scegliere Elimina nel file di eliminazione dal menu di scelta  >  **rapida.**

1. Ricompilare il progetto.

     Il progetto viene compilato senza avvisi o errori.

## <a name="see-also"></a>Vedi anche

[Analisi codice per il codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)
