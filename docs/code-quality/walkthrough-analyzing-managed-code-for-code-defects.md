---
title: 'Procedura dettagliata: Analisi del codice gestito per errori del codice | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ea39704ea232fb304257b897087f0ae60d19c4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procedura dettagliata: Analisi del codice gestito per l'identificazione di errori del codice
In questa procedura dettagliata, verrà analizzato un progetto gestito per errori del codice utilizzando lo strumento di analisi codice.  
  
 Questa procedura dettagliata verrà scorrere il processo di analisi del codice di utilizzo per analizzare gli assembly di codice gestito .NET per conformità con le linee guida di progettazione di Microsoft .NET Framework.  
  
 In questa procedura dettagliata, si:  
  
-   Analizzare e risolvere gli avvisi degli errori di codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Creare una libreria di classi  
  
#### <a name="to-create-a-class-library"></a>Per creare una libreria di classi  
  
1.  Nel **File** dal menu di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], fare clic su **New** e quindi fare clic su **progetto**.  
  
2.  Nel **nuovo progetto** nella finestra di dialogo **tipi di progetto**, fare clic su **Visual c#**.  
  
3.  In **modelli**selezionare **libreria di classi**.  
  
4.  Nel **nome** nella casella di testo **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.  
  
5.  Dopo aver creato il progetto, aprire il file Class1.cs.  
  
6.  Sostituire il testo esistente in Class1.cs con il codice seguente:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Salvare il file Class1.cs.  
  
## <a name="analyze-the-project"></a>Analizzare il progetto  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Per analizzare un progetto gestito per errori del codice  
  
1.  Selezionare il progetto CodeAnalysisManagedDemo in **Esplora**.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
     Verrà visualizzata la pagina proprietà CodeAnalysisManagedDemo.  
  
3.  Fare clic su **CodeAnalysis**.  
  
4.  Assicurarsi che **Attiva analisi codice in fase di compilazione (definisce la costante CODE_ANALYSIS**) sia selezionata.  
  
5.  Dal **eseguire il set di regole** elenco a discesa, seleziona **tutte le regole Microsoft**.  
  
6.  Nel **File** menu, fare clic su **Salva elementi selezionati**e quindi chiudere le pagine delle proprietà ManagedDemo.  
  
7.  Nel **compilare** menu, fare clic su **Compila ManagedDemo**.  
  
     Gli avvisi di compilazione progetto CodeAnalysisManagedDemo vengono segnalati nel **analisi del codice** e **Output** windows.  
  
     Se il **analisi del codice** finestra non sono visualizzate, scegliere il **Analizza** menu, scegliere **Windows** e quindi **scegliere analisi del codice**.  
  
## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi codice  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere le violazioni di regole di analisi codice  
  
1.  Nel **vista** menu, fare clic su **elenco errori**.  
  
     In base al profilo di sviluppo scelto, potrebbe essere necessario scegliere **altre finestre** sul **vista** menu e quindi fare clic su **elenco errori**.  
  
2.  In **Esplora**, fare clic su **Mostra tutti i file**.  
  
3.  Successivamente, espandere il nodo di proprietà e quindi aprire il file AssemblyInfo.cs.  
  
4.  Per correggere gli avvisi, usare la seguente:  
  
-   [CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: 'demo' deve essere contrassegnato con CLSCompliantAttribute e il relativo valore deve essere true.  
  
    -   Aggiungere il codice `using``System;` al file AssemblyInfo.cs.  
  
         Successivamente, aggiungere il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.  
  
         Ricompilare il progetto.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: public demo (String)  
  
    -   Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo`.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: public demo (String, eccezione)  
  
    -   Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo`.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: protected demo (SerializationInfo, StreamingContext)  
  
    -   Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1.  
  
         Successivamente, aggiungere il costruttore`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Ricompilare il progetto.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: public demo)  
  
    -   Aggiungere il costruttore `public demo () : base() { }` alla classe `demo` **.**  
  
         Ricompilare il progetto.  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole del nome dello spazio dei nomi 'testCode' modificandolo in 'TestCode'.  
  
    -   Modifica le maiuscole e minuscole dello spazio dei nomi `testCode` a `TestCode`.  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole nome del tipo 'demo' modificandolo in 'Demo'.  
  
    -   Modificare il nome del membro da `Demo`.  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole nome di membro 'item' modificandolo in 'Item'.  
  
    -   Modificare il nome del membro da `Item`.  
  
-   [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: rinominare 'testCode.demo' per terminare in 'Exception'.  
  
    -   Modificare il nome della classe e i relativi costruttori in `DemoException`.  
  
-   [CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): firmare 'ManagedDemo' con una chiave con nome sicuro.  
  
    -   Nel **progetto** menu, fare clic su **proprietà ManagedDemo**.  
  
         Vengono visualizzate le proprietà del progetto.  
  
         Fare clic su **firma**.  
  
         Selezionare il **firmare l'assembly** casella di controllo.  
  
         Nel **scegliere un file chiave con nome sicuro** elenco, selezionare  **\<nuovo … >**.  
  
         Il **Crea chiave con nome sicuro** viene visualizzata la finestra di dialogo.  
  
         Nel **nome file di chiave**, digitare TestKey.  
  
         Immettere una password e quindi fare clic su **OK**.  
  
         Nel **File** menu, fare clic su **Salva elementi selezionati**, quindi chiudere le pagine delle proprietà.  
  
         Ricompilare il progetto.  
  
-   [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: aggiungere un attributo [Serializable] a 'demo' poiché questo tipo implementa ISerializable.  
  
    -   Aggiungere il `[Serializable ()]` attributo alla classe `demo`.  
  
         Ricompilare il progetto.  
  
 Dopo aver completato le modifiche, il file Class1.cs dovrebbe essere simile al seguente:  
  
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
  
## <a name="exclude-code-analysis-warnings"></a>Escludere gli avvisi dell'analisi codice  
  
#### <a name="to-exclude-code-defect-warnings"></a>Per escludere gli avvisi degli errori di codice  
  
1.  Per ogni avviso rimanenti, eseguire le operazioni seguenti:  
  
    1.  Nella finestra Analisi codice, selezionare l'avviso.  
  
    2.  Scegliere **azioni**, quindi scegliere **Elimina messaggio**, quindi scegliere **File di eliminazione In progetto**.  
  
     Per ulteriori informazioni, vedere [procedura: esclusione di avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Ricompilare il progetto.  
  
     Il progetto venga compilato senza errori o avvisi.