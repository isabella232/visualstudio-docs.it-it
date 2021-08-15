---
title: Gestire le eccezioni con il debugger | Microsoft Docs
description: Informazioni su come specificare le eccezioni in cui si interrompe il debugger, a quel punto si vuole che il debugger si interrompa e come vengono gestite le interruzioni.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 25e5bc135b6533f309e1e8e3698c16c5e4e192a5730839a1516577a9afb31a0d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121324899"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gestire le eccezioni con il debugger in Visual Studio

Un'eccezione è un'indicazione di uno stato di errore che si verifica durante l’esecuzione di un programma. È possibile indicare al debugger le eccezioni o i set di eccezioni in cui interrompere l'esecuzione e a quale punto si vuole che il debugger si interrompa, ovvero sospende il debugger. Quando il debugger si interrompe, viene visualizzato il punto in cui è stata generata l'eccezione. È anche possibile aggiungere o eliminare eccezioni. Con una soluzione aperta in Visual Studio, usare Debug > Windows > **Eccezione Impostazioni** per aprire la **finestra** Impostazioni eccezione.

Fornire gestori che rispondono alle eccezioni più importanti. Se è necessario sapere come aggiungere gestori per le eccezioni, vedere Correggere i bug scrivendo [codice C# migliore.](../debugger/write-better-code-with-visual-studio.md) Informazioni anche su come configurare il debugger in modo che interrompa sempre l'esecuzione per alcune eccezioni.

Quando si verifica un'eccezione, il debugger scrive un messaggio di eccezione nella **finestra Output.** L'esecuzione può interrompersi nei casi seguenti quando:

- Viene generata un'eccezione che non viene gestita.
- Il debugger è configurato per interrompere l'esecuzione prima che venga richiamato qualsiasi gestore.
- È stato impostato [Just My Code](../debugger/just-my-code.md)e il debugger è configurato per l'interruzione in caso di eccezioni non gestite nel codice utente.

> [!NOTE]
> ASP.NET dispone di un gestore di eccezioni di livello superiore che mostra le pagine di errore in un browser. Non interrompe l'esecuzione a meno **Just My Code** non sia attivata. Per un esempio, vedere Indicare al debugger di continuare in caso di eccezioni non [gestite dall'utente più avanti.](#BKMK_UserUnhandled)

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> In un'applicazione Visual Basic il debugger gestisce tutti gli errori come eccezioni, anche se si usano gestori degli errori di tipo On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indicare al debugger di interrompere l'esecuzione quando viene generata un'eccezione

Il debugger può interrompere l'esecuzione nel punto in cui viene generata un'eccezione, pertanto è possibile esaminare l'eccezione prima che venga richiamato un gestore.

Nella finestra **Impostazioni** eccezioni (**Debug > Windows > Eccezioni Impostazioni**) espandere il nodo per una categoria di eccezioni, ad esempio Eccezioni Common Language **Runtime**. Selezionare quindi la casella di controllo per un'eccezione specifica all'interno di tale categoria, ad **esempio System.AccessViolationException**. È inoltre possibile selezionare un'intera categoria di eccezioni.

![AccessViolationException selezionata](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> È possibile trovare eccezioni  specifiche usando  la finestra Cerca nella barra degli strumenti Impostazioni eccezioni oppure usare la ricerca per filtrare spazi dei nomi specifici , ad esempio **System.IO**.

Se si seleziona un'eccezione nella finestra Impostazioni eccezioni, l'esecuzione del debugger si interrompe ogni volta **che** viene generata l'eccezione, indipendentemente dal fatto che sia gestita. A questo punto l'eccezione è denominata eccezione first chance. Di seguito vengono riportati un paio di scenari di esempio:

- Nell'applicazione console C# seguente il metodo Main genera **un'eccezione AccessViolationException** all'interno di un `try/catch` blocco .

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

  Se **accessViolationException** è selezionato in Exception **Impostazioni**, l'esecuzione si interromperà nella riga quando si `throw` esegue questo codice nel debugger. È quindi possibile continuare l'esecuzione. Nella console dovrebbero essere visualizzate entrambe le righe:

  ```cmd
  caught exception
  goodbye
  ```

  ma non visualizza la `here` riga.

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

  Se **accessViolationException** è selezionato in Exception **Impostazioni**, l'esecuzione si interromperà nella riga sia `throw` in **ThrowHandledException()** che in **ThrowUnhandledException()** quando si esegue questo codice nel debugger.

Per ripristinare le impostazioni predefinite delle eccezioni, scegliere il pulsante **Ripristina le impostazioni predefinite dell'elenco:**

![Ripristinare i valori predefiniti in Impostazioni eccezione](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Indicare al debugger di continuare con le eccezioni non gestite dall'utente

Se si esegue il debug di codice .NET o JavaScript con [Just My Code](../debugger/just-my-code.md), è possibile indicare al debugger di evitare l'interruzione in caso di eccezioni non gestite nel codice utente ma gestite altrove.

1. Nella finestra **Impostazioni** eccezioni aprire il menu di scelta rapida facendo clic con il pulsante destro del mouse su un'etichetta di colonna e quindi scegliere Mostra colonne **> Azioni aggiuntive**. Se è stato disattivato **Just My Code**, questo comando non verrà visualizzato. Verrà visualizzata una terza colonna **denominata Azioni** aggiuntive.

   ![Colonna Azioni aggiuntive](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Per un'eccezione che mostra Continua quando non gestita nel codice utente **in** questa colonna, il debugger continua se tale eccezione non viene gestita nel codice utente ma viene gestita esternamente.

2. Per modificare questa impostazione per una determinata eccezione, selezionare l'eccezione, fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere Continua se non **gestito nel codice utente.** È anche possibile modificare l'impostazione per un'intera categoria di eccezioni, ad esempio le eccezioni di Common Language Runtime.

   ![**Continua se non gestita nel codice utente** impostazione](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Ad esempio, ASP.NET applicazioni Web gestiscono le eccezioni convertendole in un codice di stato HTTP 500 ( Gestione delle eccezioni[in API Web ASP.NET](/aspnet/web-api/overview/error-handling/exception-handling)), che potrebbe non aiutare a determinare l'origine dell'eccezione. Nell'esempio seguente, il codice utente effettua una chiamata a `String.Format()` che genera un’eccezione <xref:System.FormatException>. L'esecuzione si interrompe come segue:

![Interruzioni in base all'&#45;'eccezione non gestita](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Aggiungere ed eliminare le eccezioni

È possibile aggiungere ed eliminare le eccezioni. Per eliminare un tipo di eccezione da una  categoria, selezionare l'eccezione e scegliere il pulsante Elimina l'eccezione selezionata dall'elenco (segno meno) sulla barra degli **strumenti Impostazioni** eccezioni. Oppure è possibile fare clic con il pulsante destro del mouse sull'eccezione **e scegliere Elimina** dal menu di scelta rapida. L'eliminazione di un'eccezione ha lo stesso effetto dell'annullamento della verifica dell'eccezione, ovvero il debugger non si interrompe quando viene generata.

Per aggiungere un'eccezione:

1. Nella finestra **Impostazioni** eccezioni selezionare una delle categorie di eccezioni( ad esempio, **Common Language Runtime**).

2. Scegliere il **pulsante Aggiungi un'eccezione alla categoria** selezionata (segno più).

   ![Pulsante **Aggiungi un'eccezione alla categoria selezionata**](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Digitare il nome dell'eccezione, ad esempio **System.UriTemplateMatchException.**

   ![Digitare il nome dell'eccezione](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   L'eccezione viene aggiunta all'elenco (in ordine alfabetico) e selezionata automaticamente.

Per aggiungere un'eccezione alle categorie Eccezioni di accesso alla memoria GPU, Eccezioni di runtime JavaScript o Eccezioni Win32, includere il codice di errore e la descrizione.

> [!TIP]
> Controllare l’ortografia. La **finestra Impostazioni** eccezione non verifica l'esistenza di un'eccezione aggiunta. Pertanto, se si digita **Sytem.UriTemplateMatchException**, si otterrà una voce per l'eccezione (e non per **System.UriTemplateMatchException).**

Poiché sono persistenti nel file con estensione suo della soluzione, le impostazioni delle eccezioni si applicano a una soluzione specifica. Non è possibile riutilizzare impostazioni di eccezioni specifiche in tutte le soluzioni. Ora vengono rese persistenti solo le eccezioni aggiunte. le eccezioni eliminate non lo sono. È possibile aggiungere un'eccezione, chiudere e riaprire la soluzione e l'eccezione sarà ancora presente. Ma se si elimina un'eccezione e si chiude e si riapre la soluzione, l'eccezione viene visualizzata nuovamente.

La finestra **Impostazioni eccezioni** supporta tipi di eccezioni generiche in C#, ma non in Visual Basic. Per interrompere l’esecuzione in corrispondenza di eccezioni come `MyNamespace.GenericException<T>`, è necessario aggiungere l'eccezione come **MyNamespace.GenericException'1**. Ciò significa che se è stata creata un'eccezione simile al codice seguente:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

È possibile aggiungere l'eccezione **a Exception Impostazioni** usando la procedura precedente:

![Aggiunta di eccezione generica](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Aggiungere condizioni a un'eccezione

Usare la **finestra Impostazioni** eccezioni per impostare le condizioni per le eccezioni. Le condizioni attualmente supportate includono i nomi dei moduli da includere o escludere per l'eccezione. Impostando i nomi dei moduli come condizioni, è possibile scegliere di interrompere l'esecuzione dell'eccezione solo in determinati moduli di codice. È anche possibile scegliere di evitare l'interruzione in determinati moduli.

> [!NOTE]
> L'aggiunta di condizioni a un'eccezione è supportata a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Per aggiungere eccezioni condizionali:

1. Scegliere il **pulsante Modifica condizioni** nella finestra Impostazioni eccezione oppure fare clic con il pulsante destro del mouse sull'eccezione e scegliere Modifica **condizioni.**

   ![Condizioni per un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Per aggiungere altre condizioni necessarie all'eccezione, selezionare **Aggiungi condizione** per ogni nuova condizione. Vengono visualizzate altre righe di condizione.

   ![Condizioni aggiuntive per un'eccezione](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Per ogni riga della condizione digitare il nome del modulo e modificare l'elenco degli operatori di confronto in **Uguale** a **o Diverso da**. È possibile specificare caratteri jolly ( **\\\*** ) nel nome per specificare più di un modulo.

4. Se è necessario eliminare una condizione, scegliere **la X** alla fine della riga della condizione.

## <a name="see-also"></a>Vedi anche

- [Continuare l'esecuzione dopo un'eccezione](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Procedura: Esaminare il codice di sistema dopo un'eccezione](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Procedura: Usare controlli di runtime nativi](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
