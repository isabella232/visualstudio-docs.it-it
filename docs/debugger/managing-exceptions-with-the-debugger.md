---
title: Gestire le eccezioni con il debugger di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f19bbbfbde9a111c6edea112b7250fca934ac7f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881690"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gestire le eccezioni con il debugger di Visual Studio

Un'eccezione è un'indicazione di uno stato di errore che si verifica durante l’esecuzione di un programma. È possibile impostare il debugger quali eccezioni o set di eccezioni per interrompere l'esecuzione e a questo punto si desidera che l'interruzione del debugger. Quando il debugger si interrompe, viene illustrato in cui è stata generata l'eccezione. È anche possibile aggiungere o eliminare le eccezioni. Con una soluzione aperta in Visual Studio, usare **Debug > Windows > Impostazioni eccezioni** per aprire il **impostazioni eccezioni** finestra.

Fornire gestori che rispondono alle eccezioni più importanti. Anche informazioni su come configurare il debugger per interrompere sempre l'esecuzione per alcune eccezioni.

Quando si verifica un'eccezione, il debugger visualizza un messaggio di eccezione per il **Output** finestra. Il debugger può interrompere l'esecuzione nel seguente casi:

- Viene generata un'eccezione non gestita.
- Il debugger è configurato per l'esecuzione si interrompe prima che venga richiamato qualsiasi gestore.
- È stata impostata [Just My Code](../debugger/just-my-code.md), e viene configurato il debugger per interrompere qualsiasi eccezione non gestita nel codice utente.

> [!NOTE]
> ASP.NET dispone di un gestore di eccezioni di livello superiore che mostra le pagine di errore in un browser. Non viene interrotta l'esecuzione, a meno che **Just My Code** è attivata. Per un esempio, vedere [impostare il debugger per continuare in caso di eccezioni non gestite dall'utente](#BKMK_UserUnhandled) sotto.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> In un'applicazione Visual Basic, il debugger gestisce tutti gli errori come eccezioni, anche se si usa sui gestori di errori di stile di errore.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Impostare il debugger per interrompere l'esecuzione quando viene generata un'eccezione

Il debugger può interrompere l'esecuzione nel punto in cui viene generata un'eccezione, pertanto è possibile esaminare l'eccezione prima che venga richiamato un gestore.

Nel **impostazioni eccezioni** finestra (**Debug > Windows > Impostazioni eccezioni**), espandere il nodo per una categoria di eccezioni, ad esempio **eccezioni Common Language Runtime**. Quindi selezionare la casella di controllo per un'eccezione specifica all'interno di tale categoria, ad esempio **System. AccessViolationException**. È inoltre possibile selezionare un'intera categoria di eccezioni.

![AccessViolationException selezionata](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> È possibile trovare eccezioni specifiche usando il **ricerca** finestra nel **impostazioni eccezioni** sulla barra degli strumenti o utilizzare la ricerca per filtrare per spazi dei nomi specifici (ad esempio **System.IO**).

Se si seleziona un'eccezione nel **impostazioni eccezioni** finestra, esecuzione del debugger interromperà ogni volta che viene generata l'eccezione, indipendentemente dal fatto che viene gestito. L'eccezione viene ora chiamato un'eccezione first-chance. Di seguito vengono riportati un paio di scenari di esempio:

- Nell'esempio c# applicazione console, il metodo Main genera un' **AccessViolationException** all'interno di un `try/catch` blocco.

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

  Se si dispone **AccessViolationException** archiviato **impostazioni eccezioni**, l'esecuzione si interrompe il `throw` riga quando si esegue questo codice nel debugger. È quindi possibile continuare l'esecuzione. Nella console dovrebbero essere visualizzate entrambe le righe:

  ```cmd
  caught exception
  goodbye
  ```

  ma non vengono visualizzati il `here` riga.

- Un'applicazione console c# fa riferimento a una libreria di classi con una classe che dispone di due metodi. Un metodo genera un'eccezione e gestisce, mentre un secondo metodo, genera la stessa eccezione ma non la gestisce.

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

  Ecco il metodo Main () dell'applicazione console:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Se si dispone **AccessViolationException** archiviato **impostazioni eccezioni**, l'esecuzione si interrompe il `throw` riga sia in **throwhandledexception ()** e **Throwunhandledexception ()** quando si esegue questo codice nel debugger.

Per ripristinare le impostazioni delle eccezioni per le impostazioni predefinite, scegliere il **Ripristina le impostazioni predefinite dell'elenco** pulsante:

![Ripristina impostazioni predefinite nelle impostazioni eccezioni](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Impostare il debugger per continuare in caso di eccezioni non gestite dall'utente

Se si esegue il debug di codice .NET o JavaScript con [Just My Code](../debugger/just-my-code.md), è possibile impostare il debugger per evitare l'interruzione per eccezioni non gestite nel codice utente, ma gestite in un' posizione.

1. Nel **impostazioni eccezioni** finestra, aprire il menu di scelta rapida facendo clic con un'etichetta di colonna e quindi selezionare **Mostra colonne > azioni aggiuntive**. (Se è stata disattivata **Just My Code**, questo comando non è disponibile.) Una terza colonna denominata **azioni aggiuntive** viene visualizzata.

   ![Colonna Azioni aggiuntiva](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Per un'eccezione che illustra **continua se non gestita nel codice utente** in questa colonna, il debugger continua se tale eccezione non gestita nel codice utente ma viene gestita esternamente.

2. Per modificare questa impostazione per una determinata eccezione, selezionare l'eccezione, fare doppio clic per visualizzare il menu di scelta rapida e selezionare **continua se non gestita nel codice utente**. È anche possibile modificare l'impostazione per un'intera categoria di eccezioni, ad esempio l'intere eccezioni di Common Language Runtime).

   ![* * Continua se non gestita nel codice * * impostazioni utente](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Ad esempio, le applicazioni web ASP.NET gestiscono le eccezioni convertendole in un codice di stato HTTP 500 ([gestione delle eccezioni in API Web ASP.NET](http://www.asp.net/web-api/overview/error-handling/exception-handling)), che potrebbe non aiutare determinare la causa dell'eccezione. Nell'esempio seguente, il codice utente effettua una chiamata a `String.Format()` che genera un’eccezione <xref:System.FormatException>. L'esecuzione si interrompe come segue:

![Le interruzioni utente&#45;eccezione non gestita](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Aggiungere ed eliminare le eccezioni

È possibile aggiungere ed eliminare le eccezioni. Per eliminare un tipo di eccezione da una categoria, selezionare l'eccezione e scegliere il **Elimina l'eccezione selezionata dall'elenco** pulsante (il segno di sottrazione) le **impostazioni eccezioni** sulla barra degli strumenti. Oppure è possibile fare doppio clic sull'eccezione e selezionare **Elimina** dal menu di scelta rapida. L'eliminazione di un'eccezione ha lo stesso effetto dell'eccezione non selezionata, ovvero che il debugger interrompa quando viene generata.

Per aggiungere un'eccezione:

1. Nel **impostazioni eccezioni** finestra, selezionare una delle categorie di eccezioni (ad esempio **Common Language Runtime**).

2. Scegliere il **aggiungere un'eccezione alla categoria selezionata** pulsante (il segno più).

   ![* * Aggiungere un'eccezione al pulsante selezionato categoria * *](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Digitare il nome dell'eccezione (ad esempio, **uritemplatematchexception**).

   ![Digitare il nome dell'eccezione](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   L'eccezione viene aggiunto all'elenco (in ordine alfabetico) e controllato automaticamente.

Per aggiungere un'eccezione per le eccezioni di accesso a memoria GPU, eccezioni di Runtime JavaScript o categorie di eccezioni Win32, includere il codice di errore e la descrizione.

> [!TIP]
> Controllare l’ortografia. Il **impostazioni eccezioni** finestra non verifica l'esistenza di un'eccezione aggiunta. Pertanto, se digita **Sytem**, si otterrà una voce per tale eccezione (e non per **uritemplatematchexception**).

Impostazioni eccezioni sono persistenti nel file con estensione suo della soluzione, quindi vengono applicate a una particolare soluzione. È possibile riutilizzare impostazioni di eccezioni specifiche nelle soluzioni. A questo punto vengono mantenute solo le eccezioni aggiunte non sono le eccezioni eliminate. È possibile aggiungere un'eccezione, chiudere e riaprire la soluzione e l'eccezione sarà ancora disponibile. Ma se si elimina un'eccezione e si chiude e si riapre la soluzione, l'eccezione viene visualizzata nuovamente.

La finestra **Impostazioni eccezioni** supporta tipi di eccezioni generiche in C#, ma non in Visual Basic. Per interrompere l’esecuzione in corrispondenza di eccezioni come `MyNamespace.GenericException<T>`, è necessario aggiungere l'eccezione come **MyNamespace.GenericException'1**. Vale a dire, se è stata creata un'eccezione a questo codice:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

È possibile aggiungere l'eccezione **impostazioni eccezioni** utilizzando la procedura precedente:

![aggiunta di eccezione generica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Aggiungere le condizioni per un'eccezione

Usare la **impostazioni eccezioni** finestra per impostare le condizioni in caso di eccezioni. Attualmente sono supportati le condizioni includono i nomi di modulo da includere o escludere per l'eccezione. Imposta i nomi di modulo come condizioni, è possibile scegliere per l'interruzione per l'eccezione solo su alcuni moduli di codice. È anche possibile scegliere evitare l'interruzione per moduli specifici.

> [!NOTE]
> Aggiunta di condizioni per un'eccezione è stata introdotta in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Per aggiungere le eccezioni condizionale:

1. Scegliere il **modificare le condizioni** pulsante nella finestra Impostazioni eccezioni o l'eccezione e scegliere **Modifica condizioni**.

   ![Le condizioni per un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Per aggiungere condizioni aggiuntive necessarie per l'eccezione, selezionare **Aggiungi condizione** per ogni nuova condizione. Vengono visualizzate le righe di una condizione aggiuntiva.

   ![Condizioni aggiuntive per un'eccezione](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Per ogni riga della condizione, digitare il nome del modulo e modificare l'elenco di operatori di confronto per **è uguale a** oppure **non è uguale a**. È possibile specificare i caratteri jolly (* *\\* * *) nel nome per specificare più di un modulo.

4. Se si desidera eliminare una condizione, scegliere il **X** alla fine della riga di condizione.

## <a name="see-also"></a>Vedere anche

[Continuare l'esecuzione dopo un'eccezione](../debugger/continuing-execution-after-an-exception.md)<br/>
[Procedura: Esaminare il codice di sistema dopo un'eccezione](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Procedura: Usare controlli di runtime nativi](../debugger/how-to-use-native-run-time-checks.md)<br/>
[Usare i controlli runtime senza la libreria run-time di C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[: Esercitazione eseguire il debug usando Visual Studio](../debugger/getting-started-with-the-debugger.md)
