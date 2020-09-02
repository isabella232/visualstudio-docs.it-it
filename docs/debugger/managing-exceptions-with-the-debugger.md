---
title: Gestire le eccezioni con il debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: how-to
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff28944a36d338230a17cd533a4832452e42885b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348457"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gestire le eccezioni con il debugger in Visual Studio

Un'eccezione è un'indicazione di uno stato di errore che si verifica durante l’esecuzione di un programma. È possibile indicare al debugger quali eccezioni o set di eccezioni si interrompono e, a quel punto, si desidera che il debugger si interrompa (ovvero sospendere il debugger). Quando il debugger si interrompe, viene visualizzata la posizione in cui è stata generata l'eccezione. È anche possibile aggiungere o eliminare le eccezioni. Con una soluzione aperta in Visual Studio, usare **Debug > Windows > le impostazioni delle eccezioni** per aprire la finestra **Impostazioni eccezioni** .

Fornire gestori che rispondono alle eccezioni più importanti. Se è necessario sapere come aggiungere gestori per le eccezioni, vedere correggere i [bug scrivendo codice C# migliore](../debugger/write-better-code-with-visual-studio.md). Inoltre, informazioni su come configurare il debugger in modo da interrompere sempre l'esecuzione per alcune eccezioni.

Quando si verifica un'eccezione, il debugger scrive un messaggio di eccezione nella finestra di **output** . Potrebbe interrompere l'esecuzione nei casi seguenti:

- Viene generata un'eccezione che non viene gestita.
- Il debugger è configurato per interrompere l'esecuzione prima che venga richiamato un gestore.
- È stato impostato [Just My Code](../debugger/just-my-code.md)e il debugger è configurato per l'interruzione in caso di eccezione non gestita nel codice utente.

> [!NOTE]
> ASP.NET dispone di un gestore di eccezioni di livello superiore che mostra le pagine di errore in un browser. Non interrompe l'esecuzione a meno che non sia attivato **Just My Code** . Per un esempio, vedere [indicare al debugger di continuare in caso di eccezioni non gestite dall'utente](#BKMK_UserUnhandled) .

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> In un'applicazione Visual Basic il debugger gestisce tutti gli errori come eccezioni, anche se si usano gestori degli errori di tipo On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indica al debugger di interrompere l'interruzione quando viene generata un'eccezione

Il debugger può interrompere l'esecuzione nel punto in cui viene generata un'eccezione, pertanto è possibile esaminare l'eccezione prima che venga richiamato un gestore.

Nella finestra **Impostazioni eccezioni** (**Debug > Windows > impostazioni eccezioni**) espandere il nodo per una categoria di eccezioni, ad esempio **eccezioni Common Language Runtime**. Selezionare quindi la casella di controllo per un'eccezione specifica all'interno di tale categoria, ad esempio **System. AccessViolationException**. È inoltre possibile selezionare un'intera categoria di eccezioni.

![AccessViolationException selezionata](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> È possibile trovare eccezioni specifiche utilizzando la finestra **Cerca** nella barra degli strumenti **Impostazioni eccezioni** oppure utilizzare la ricerca per filtrare gli spazi dei nomi specifici (ad esempio **System.io**).

Se si seleziona un'eccezione nella finestra **Impostazioni eccezioni** , l'esecuzione del debugger viene interrotta ogni volta che viene generata l'eccezione, a prescindere dal fatto che sia gestita. A questo punto, l'eccezione viene chiamata eccezione first-chance. Di seguito vengono riportati un paio di scenari di esempio:

- Nell'applicazione console C# seguente il metodo Main genera un'eccezione **AccessViolationException** all'interno di un `try/catch` blocco.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Se **le impostazioni dell'eccezione**sono state archiviate in **AccessViolationException** , l'esecuzione si interrompe sulla `throw` riga quando si esegue questo codice nel debugger. È quindi possibile continuare l'esecuzione. Nella console dovrebbero essere visualizzate entrambe le righe:

  ```cmd
  caught exception
  goodbye
  ```

  ma non Visualizza la `here` riga.

- Un'applicazione console C# fa riferimento a una libreria di classi con una classe che dispone di due metodi. Un metodo genera un'eccezione e la gestisce, mentre un secondo metodo genera la stessa eccezione ma non la gestisce.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Il metodo seguente è il metodo Main() dell'applicazione console:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Se **le impostazioni dell'eccezione**sono state archiviate in **AccessViolationException** , l'esecuzione si interrompe sulla `throw` riga in **ThrowHandledException ()** e **ThrowUnhandledException ()** quando si esegue questo codice nel debugger.

Per ripristinare le impostazioni predefinite delle eccezioni, scegliere il pulsante **Ripristina le impostazioni predefinite dell'elenco** :

![Ripristinare i valori predefiniti in Impostazioni eccezione](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Indicare al debugger di continuare a eseguire le eccezioni non gestite dall'utente

Se si esegue il debug di codice .NET o JavaScript con [Just My Code](../debugger/just-my-code.md), è possibile indicare al debugger di evitare l'interruzione di eccezioni non gestite nel codice utente, ma gestite altrove.

1. Nella finestra **Impostazioni eccezioni** aprire il menu di scelta rapida facendo clic con il pulsante destro del mouse su un'etichetta di colonna e quindi scegliere **Mostra colonne > azioni aggiuntive**. Se è stato disattivato **Just My Code**, questo comando non verrà visualizzato. Viene visualizzata una terza colonna denominata **azioni aggiuntive** .

   ![Colonna azioni aggiuntive](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Per un'eccezione che mostra **continua se non gestita nel codice utente** in questa colonna, il debugger continua se tale eccezione non viene gestita nel codice utente ma viene gestita esternamente.

2. Per modificare questa impostazione per un'eccezione specifica, selezionare l'eccezione, fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere **continua se non gestita nel codice utente**. È anche possibile modificare l'impostazione per un'intera categoria di eccezioni, ad esempio l'intera eccezione di Common Language Runtime.

   ![* * Continua se non gestita nell'impostazione del codice utente * *](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Ad esempio, le applicazioni Web ASP.NET gestiscono le eccezioni convertendo tali eccezioni in un codice di stato HTTP 500 ([gestione delle eccezioni in API Web ASP.NET](/aspnet/web-api/overview/error-handling/exception-handling)), che potrebbe non essere utile per determinare l'origine dell'eccezione. Nell'esempio seguente, il codice utente effettua una chiamata a `String.Format()` che genera un’eccezione <xref:System.FormatException>. L'esecuzione si interrompe come segue:

![Interruzioni per l'utente&#45;eccezione non gestita](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Aggiungere ed eliminare le eccezioni

È possibile aggiungere ed eliminare le eccezioni. Per eliminare un tipo di eccezione da una categoria, selezionare l'eccezione e scegliere il pulsante **Elimina l'eccezione selezionata dall'elenco** (il segno meno) nella barra degli strumenti **Impostazioni eccezioni** . In alternativa, è possibile fare clic con il pulsante destro del mouse sull'eccezione e scegliere **Elimina** dal menu di scelta rapida. L'eliminazione di un'eccezione ha lo stesso effetto di un'eccezione deselezionata, ovvero il debugger non si interrompe quando viene generata.

Per aggiungere un'eccezione:

1. Nella finestra **Impostazioni eccezioni** selezionare una delle categorie di eccezioni (ad esempio **Common Language Runtime**).

2. Scegliere il pulsante **Aggiungi un'eccezione alla categoria selezionata** (il segno più).

   ![* * Aggiungere un'eccezione al pulsante Category * * selezionato](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Digitare il nome dell'eccezione, ad esempio **System. UriTemplateMatchException**.

   ![Digitare il nome dell'eccezione](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   L'eccezione viene aggiunta all'elenco (in ordine alfabetico) e controllata automaticamente.

Per aggiungere un'eccezione alle eccezioni di accesso alla memoria GPU, alle eccezioni di runtime JavaScript o alle categorie di eccezioni Win32, includere il codice di errore e la descrizione.

> [!TIP]
> Controllare l’ortografia. La finestra **Impostazioni eccezioni** non verifica l'esistenza di un'eccezione aggiunta. Quindi, se si digita System **. UriTemplateMatchException**, si otterrà una voce per tale eccezione (e non per **System. UriTemplateMatchException**).

Poiché sono persistenti nel file con estensione suo della soluzione, le impostazioni delle eccezioni si applicano a una soluzione specifica. Non è possibile riutilizzare impostazioni di eccezioni specifiche in tutte le soluzioni. A questo punto vengono rese permanente solo le eccezioni aggiunte. le eccezioni eliminate non sono. È possibile aggiungere un'eccezione, chiudere e riaprire la soluzione e l'eccezione sarà ancora presente. Ma se si elimina un'eccezione e si chiude e si riapre la soluzione, l'eccezione viene visualizzata nuovamente.

La finestra **Impostazioni eccezioni** supporta tipi di eccezioni generiche in C#, ma non in Visual Basic. Per interrompere l’esecuzione in corrispondenza di eccezioni come `MyNamespace.GenericException<T>`, è necessario aggiungere l'eccezione come **MyNamespace.GenericException'1**. Ovvero, se è stata creata un'eccezione simile a questo codice:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

È possibile aggiungere l'eccezione alle **impostazioni delle eccezioni** usando la procedura precedente:

![Aggiunta di eccezione generica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Aggiungere condizioni a un'eccezione

Utilizzare la finestra **Impostazioni eccezioni** per impostare le condizioni per le eccezioni. Le condizioni attualmente supportate includono i nomi di modulo da includere o escludere per l'eccezione. Impostando i nomi dei moduli come condizioni, è possibile scegliere di interrompere l'eccezione solo per determinati moduli di codice. È anche possibile scegliere di evitare di suddividere in moduli specifici.

> [!NOTE]
> L'aggiunta di condizioni a un'eccezione è supportata a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Per aggiungere eccezioni condizionali:

1. Scegliere il pulsante **modifica condizioni** nella finestra Impostazioni eccezioni oppure fare clic con il pulsante destro del mouse sull'eccezione e scegliere **modifica condizioni**.

   ![Condizioni per un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Per aggiungere altre condizioni necessarie all'eccezione, selezionare **Aggiungi condizione** per ogni nuova condizione. Verranno visualizzate ulteriori righe di condizione.

   ![Condizioni aggiuntive per un'eccezione](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Per ogni riga di condizione, digitare il nome del modulo e impostare l'elenco operatore di confronto su **uguale** a o **non uguale**a. È possibile specificare caratteri jolly ( **\\\*** ) nel nome per specificare più di un modulo.

4. Se è necessario eliminare una condizione, scegliere la **X** alla fine della riga della condizione.

## <a name="see-also"></a>Vedere anche

- [Continuare l'esecuzione dopo un'eccezione](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Procedura: Esaminare il codice di sistema dopo un'eccezione](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Procedura: Usare controlli di runtime nativi](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Usare i controlli runtime senza la libreria di runtime del linguaggio C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
