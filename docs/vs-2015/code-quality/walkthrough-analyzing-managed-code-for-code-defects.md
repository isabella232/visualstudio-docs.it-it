---
title: 'Procedura dettagliata: analisi del codice gestito per i difetti del codice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609329"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procedura dettagliata: Analisi del codice gestito per l'identificazione di errori del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata si analizza un progetto gestito per i difetti del codice usando lo strumento di analisi del codice.

 In questa procedura dettagliata viene illustrato il processo di utilizzo dell'analisi del codice per analizzare gli assembly di codice gestito .NET per conformità con le linee guida di progettazione di Microsoft .NET Framework.

 In questa procedura dettagliata vengono illustrate le operazioni seguenti:

- Analizzare e correggere gli avvisi di errore del codice.

## <a name="prerequisites"></a>Prerequisites

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]

## <a name="create-a-class-library"></a>Creare una libreria di classi

#### <a name="to-create-a-class-library"></a>Per creare una libreria di classi

1. Scegliere **nuovo** dal menu **file** di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], quindi fare clic su **progetto**.

2. Nella finestra di dialogo **nuovo progetto** , in **Tipi progetto**, fare clic su oggetto **visivo C#** .

3. In **modelli**selezionare **libreria di classi**.

4. Nella casella di testo **nome** digitare **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.

5. Dopo aver creato il progetto, aprire il file Class1.cs.

6. Sostituire il testo esistente in Class1.cs con il codice seguente:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Salvare il file Class1.cs.

## <a name="analyze-the-project"></a>Analizzare il progetto

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Per analizzare un progetto gestito per i difetti del codice

1. Selezionare il progetto CodeAnalysisManagedDemo in **Esplora soluzioni**.

2. Scegliere **Proprietà** dal menu **Progetto**.

     Verrà visualizzata la pagina delle proprietà CodeAnalysisManagedDemo.

3. Fare clic su **CodeAnalysis**.

4. Assicurarsi che l'opzione **Abilita analisi codice su compilazione (definisce la costante CODE_ANALYSIS**) sia selezionata.

5. Dall'elenco a discesa **Esegui questo set di regole** selezionare **Microsoft all Rules**.

6. Scegliere **Salva elementi selezionati**dal menu **file** e quindi chiudere le pagine delle proprietà di ManagedDemo.

7. Scegliere **Compila ManagedDemo**dal menu **Compila** .

     Gli avvisi di compilazione del progetto CodeAnalysisManagedDemo vengono segnalati nelle finestre di **analisi del codice** e di **output** .

     Se non viene visualizzata la finestra **analisi codice** , scegliere **finestre** dal menu **analizza** , quindi **scegliere analisi codice**.

## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi del codice

#### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere le violazioni delle regole di analisi del codice

1. Scegliere **Elenco errori**dal menu **Visualizza** .

     A seconda del profilo dello sviluppatore scelto, potrebbe essere necessario puntare ad **altre finestre** dal menu **Visualizza** , quindi fare clic su **Elenco errori**.

2. In **Esplora soluzioni**fare clic su **Mostra tutti i file**.

3. Successivamente, espandere il nodo Proprietà, quindi aprire il file AssemblyInfo.cs.

4. Per correggere gli avvisi, utilizzare quanto segue:

- [CA1014: contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design:' demo ' deve essere contrassegnato con CLSCompliantAttribute e il relativo valore deve essere true.

  - Aggiungere il codice `using``System;` al file AssemblyInfo.cs.

       Aggiungere quindi il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.

       Ricompilare il progetto.

- [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: public demo (String)

  - Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo`.

- [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: public demo (String, Exception)

  - Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo`.

- [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: protected demo (SerializationInfo, StreamingContext)

  - Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1.cs.

       Aggiungere quindi il costruttore `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Ricompilare il progetto.

- [CA1032: implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: public demo ()

  - Aggiungere il costruttore `public demo () : base() { }` alla classe `demo` **.**

       Ricompilare il progetto.

- [CA1709: gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere la combinazione di maiuscole e minuscole del nome dello spazio dei nomi ' testCode ' cambiandola in ' testCode '.

  - Modificare la combinazione di maiuscole e minuscole dello spazio dei nomi `testCode` `TestCode`.

- [CA1709: gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere la combinazione di maiuscole e minuscole del nome di tipo "demo" cambiandola in "demo".

  - Modificare il nome del membro in `Demo`.

- [CA1709: gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere la combinazione di maiuscole e minuscole del nome del membro ' Item ' cambiandola in ' Item '.

  - Modificare il nome del membro in `Item`.

- [CA1710: gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: rinominare ' TestCode. demo ' per terminare con ' Exception '.

  - Modificare il nome della classe e i relativi costruttori in `DemoException`.

- [CA2210: gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Sign ' ManagedDemo ' con una chiave con nome sicuro.

  - Scegliere **proprietà ManagedDemo**dal menu **progetto** .

       Verranno visualizzate le proprietà del progetto.

       Fare clic su **firma**.

       Selezionare la casella di controllo **Firma assembly** .

       Nell'elenco **Scegli un file chiave con nome stringa** selezionare **\<New... >** .

       Verrà visualizzata la finestra di dialogo **Crea chiave con nome sicuro** .

       Nel **nome del file di chiave**digitare TestKey.

       Immettere una password e quindi fare clic su **OK**.

       Scegliere **Salva elementi selezionati**dal menu **file** e quindi chiudere le pagine delle proprietà.

       Ricompilare il progetto.

- [CA2237: contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: aggiungere un attributo [Serializable] al tipo "demo" poiché questo tipo implementa ISerializable.

  - Aggiungere l'attributo `[Serializable ()]` alla classe `demo`.

       Ricompilare il progetto.

  Una volta completate le modifiche, il file Class1.cs dovrebbe essere simile al seguente:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Escludi avvisi di analisi codice

#### <a name="to-exclude-code-defect-warnings"></a>Per escludere gli avvisi relativi al difetto del codice

1. Per ogni avviso rimanente, procedere come segue:

   1. Nella finestra analisi codice selezionare l'avviso.

   2. Scegliere **azioni**, quindi **Elimina messaggio**, quindi scegliere **nel file di eliminazione del progetto**.

      Per altre informazioni, vedere [procedura: non visualizzare avvisi tramite la voce di menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Ricompilare il progetto.

    Il progetto viene compilato senza avvisi o errori.
