---
title: 'Procedura dettagliata: Analisi del codice gestito per i difetti del codice | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7ee957d6be2cfc75a0ecdd780862c34eb5a1c540
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968656"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procedura dettagliata: Analisi del codice gestito per individuarne i difetti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata, si analizza un progetto gestito per i difetti del codice utilizzando lo strumento di analisi codice.  
  
 Questa procedura dettagliata si passerà attraverso il processo di uso di analisi del codice per analizzare gli assembly di codice .NET gestita per verificare la conformità con le linee guida per la progettazione di Microsoft .NET Framework.  
  
 In questa procedura dettagliata, è:  
  
-   Analizzare e risolvere gli avvisi degli errori di codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Creare una libreria di classi  
  
#### <a name="to-create-a-class-library"></a>Per creare una libreria di classi  
  
1.  Nel **File** dal menu del [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], fare clic su **New** e quindi fare clic su **progetto**.  
  
2.  Nel **nuovo progetto** nella finestra di dialogo **tipi di progetto**, fare clic su **Visual c#**.  
  
3.  Sotto **modelli**, selezionare **libreria di classi**.  
  
4.  Nel **Name** casella di testo, digitare **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.  
  
5.  Dopo aver creato il progetto, aprire il file Class1.cs.  
  
6.  Sostituire il testo esistente in Class1.cs con il codice seguente:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Salvare il file Class1.cs.  
  
## <a name="analyze-the-project"></a>Analizzare il progetto  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Per analizzare un progetto gestito per i difetti del codice  
  
1.  Selezionare il progetto CodeAnalysisManagedDemo **Esplora soluzioni**.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
     Verrà visualizzata la pagina di proprietà CodeAnalysisManagedDemo.  
  
3.  Fare clic su **CodeAnalysis**.  
  
4.  Verificare che l'opzione **Abilita analisi codice su compilazione (definisce la costante CODE_ANALYSIS**) sia selezionata.  
  
5.  Dal **eseguire questo set di regole** elenco a discesa, seleziona **tutte le regole Microsoft**.  
  
6.  Nel **File** menu, fare clic su **Salva elementi selezionati**e quindi chiudere le proprietà ManagedDemo.  
  
7.  Nel **compilare** menu, fare clic su **Compila ManagedDemo**.  
  
     Gli avvisi di compilazione progetto CodeAnalysisManagedDemo vengono segnalati nel **analisi del codice** e **Output** windows.  
  
     Se il **analisi del codice** finestra non viene visualizzato, scegliere il **Analizza** menu, scegliere **Windows** e quindi **scegliere l'analisi del codice**.  
  
## <a name="correct-the-code-analysis-issues"></a>Risolvere i problemi di analisi del codice  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere delle violazioni delle regole di analisi codice  
  
1.  Nel **View** menu, fare clic su **elenco errori**.  
  
     A seconda del profilo sviluppatore scelto, potrebbe essere necessario scegliere **Other Windows** nel **View** menu e quindi fare clic su **elenco errori**.  
  
2.  Nelle **Esplora soluzioni**, fare clic su **Mostra tutti i file**.  
  
3.  Successivamente, espandere il nodo di proprietà e quindi aprire il file AssemblyInfo.cs.  
  
4.  Per correggere gli avvisi, usare quanto segue:  
  
- [CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: "demo" deve essere contrassegnato con CLSCompliantAttribute e relativo valore deve essere true.  
  
  -   Aggiungere il codice `using``System;` nel file AssemblyInfo.cs.  
  
       Successivamente, aggiungere il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.  
  
       Ricompilare il progetto.  
  
- [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: pubblica demo (String)  
  
  -   Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo`.  
  
- [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: demo pubblico (String, eccezione)  
  
  -   Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo`.  
  
- [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: protetti demo (SerializationInfo, StreamingContext)  
  
  -   Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1.cs.  
  
       Successivamente, aggiungere il costruttore `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Ricompilare il progetto.  
  
- [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Aggiungere il costruttore seguente alla classe: demos pubblico  
  
  -   Aggiungere il costruttore `public demo () : base() { }` alla classe `demo` **.**  
  
       Ricompilare il progetto.  
  
- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Correggere le maiuscole e minuscole del nome dello spazio dei nomi 'testCode' modificandolo in 'TestCode'.  
  
  -   Modifica le maiuscole e minuscole dei nomi `testCode` a `TestCode`.  
  
- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Correggere le maiuscole e minuscole di tipo nome "demo" modificandolo in "Demo".  
  
  -   Modificare il nome del membro da `Demo`.  
  
- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Correggere le maiuscole e minuscole del membro nome 'item' modificandolo in 'Item'.  
  
  -   Modificare il nome del membro da `Item`.  
  
- [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Rinominare 'testCode.demo' per terminare con 'Exception'.  
  
  -   Modificare il nome della classe e i relativi costruttori in `DemoException`.  
  
- [CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Firmare 'ManagedDemo' con una chiave con nome sicuro.  
  
  -   Nel **Project** menu, fare clic su **ManagedDemo proprietà**.  
  
       Vengono visualizzate le proprietà del progetto.  
  
       Fare clic su **firma**.  
  
       Selezionare il **firmare l'assembly** casella di controllo.  
  
       Nel **scegliere un file chiave con nome sicuro** elenco, selezionare  **\<nuovo... >**.  
  
       Il **Crea chiave con nome sicuro** verrà visualizzata la finestra di dialogo.  
  
       Nel **nome file di chiave**, digitare TestKey.  
  
       Immettere una password e quindi fare clic su **OK**.  
  
       Nel **File** menu, fare clic su **Salva elementi selezionati**e quindi chiudere le pagine delle proprietà.  
  
       Ricompilare il progetto.  
  
- [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Aggiungere un attributo [Serializable] a 'demo' perché questo tipo implementa ISerializable.  
  
  -   Aggiungere il `[Serializable ()]` alla classe `demo`.  
  
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
  
#### <a name="to-exclude-code-defect-warnings"></a>Per escludere avvisi di difetti del codice  
  
1. Per ognuno degli altri avvisi, eseguire le operazioni seguenti:  
  
   1. Nella finestra Analisi codice, selezionare l'avviso.  
  
   2. Scegliere **azioni**, quindi scegliere **Elimina messaggio**, quindi scegliere **File di eliminazione progetto**.  
  
      Per altre informazioni, vedere [Procedura: Eliminare gli avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Ricompilare il progetto.  
  
    Il progetto viene compilato senza eventuali avvisi o errori.
