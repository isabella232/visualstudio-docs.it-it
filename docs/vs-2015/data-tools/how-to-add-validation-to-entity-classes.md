---
title: 'Procedura: aggiungere la convalida a classi di entità | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a68b0314f3c64ce9196b8d48a78844bc81990a92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665988"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Procedura: Aggiungere la convalida a classi di entità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La *convalida* delle classi di entità rappresenta il processo mediante cui si conferma che i valori immessi negli oggetti dati sono conformi ai vincoli presenti nello schema di un oggetto e alle regole stabilite per l'applicazione. Per ridurre gli errori, è opportuno convalidare i dati prima di inviare aggiornamenti al database sottostante. La convalida consente anche di ridurre il numero potenziale di round trip tra un'applicazione e il database.

 Gli [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) forniscono metodi parziali che consentono agli utenti di estendere il codice generato dalla finestra di progettazione eseguito durante le operazioni di inserimento, aggiornamento ed eliminazione di entità complete e anche durante e dopo la modifica delle singole colonne.

> [!NOTE]
> In questo argomento vengono forniti i passaggi di base per aggiungere la convalida a classi di entità usando [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Poiché potrebbe essere difficile seguire questi passaggi generici senza fare riferimento a una classe di entità specifica, viene fornita una procedura dettagliata in cui vengono utilizzati i dati effettivi.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Aggiunta della convalida per le modifiche al valore di una specifica colonna
 In questa procedura viene mostrato come convalidare i dati quando viene modificato il valore in una colonna. Poiché la convalida viene eseguita nella definizione di classe anziché nell'interfaccia utente, se il valore causa l'esito negativo della convalida, viene generata un'eccezione. Implementare la gestione degli errori per il codice nell'applicazione che tenta di modificare i valori della colonna.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Per convalidare i dati durante la modifica del valore di una colonna

1. Aprire o creare un nuovo file di classi LINQ to SQL (file con**estensione dbml** ) nell'[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. In Progettazione relazionale di O, fare clic con il pulsante destro del mouse sulla classe per la quale si desidera aggiungere la convalida, quindi scegliere **Visualizza codice**.

    Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3. Posizionare il cursore nella classe parziale.

4. Per i progetti di Visual Basic:

   1. Espandere l'elenco **Nome metodo**.

   2. Individuare il metodo **on**_ColumnName_**Changing** per la colonna a cui si desidera aggiungere la convalida.

   3. Alla classe parziale viene aggiunto un metodo `Changing`*columnname* `On`.

   4. Aggiungere il codice riportato di seguito per verificare innanzitutto che sia stato immesso un valore e quindi per assicurarsi che il valore immesso per la colonna sia accettabile per l'applicazione. Poiché l'argomento `value` contiene il valore proposto, aggiungere logica per confermare che si tratta di un valore valido:

      ```vb
      If value.HasValue Then
          ' Add code to ensure that the value is acceptable.
          ' If value < 1 Then
          '    Throw New Exception("Invalid data!")
          ' End If
      End If
      ```

      Per i progetti C#:

   5. Poiché i progetti C# non generano automaticamente i gestori eventi, è possibile usare IntelliSense per creare i metodi parziali di modifica delle colonne.

       Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di modifica delle colonne relativo alla colonna per cui si desidera aggiungere la convalida. Il codice riportato di seguito è simile al codice generato quando si seleziona un metodo parziale di modifica delle colonne:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Aggiunta della convalida per gli aggiornamenti a una classe di entità
 Oltre a controllare i valori durante le modifiche, è anche possibile convalidare i dati quando si tenta di aggiornare una classe di entità completa. La convalida durante un tentativo di aggiornamento consente di confrontare i valori di più colonne, se richiesto dalle regole business. Nella procedura riportata di seguito viene mostrato come eseguire la convalida quando si tenta di aggiornare una classe di entità completa.

> [!NOTE]
> Il codice di convalida per gli aggiornamenti alle classi di entità complete viene eseguito nella classe <xref:System.Data.Linq.DataContext> parziale, anziché nella classe parziale di una classe di entità specifica.

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Per convalidare i dati durante un aggiornamento a una classe di entità

1. Aprire o creare un nuovo file di classi LINQ to SQL (file con**estensione dbml** ) nell'[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. Fare clic con il pulsante destro del mouse su un'area vuota della finestra di progettazione di O/R e scegliere **Visualizza codice**.

    Viene aperto l'editor del codice con una classe parziale per `DataContext`.

3. Posizionare il cursore nella classe parziale per `DataContext`.

4. Per i progetti di Visual Basic:

   1. Espandere l'elenco **Nome metodo**.

   2. Fare clic su **Update**_NOMECLASSEDIENTITÀ alla_.

   3. Alla classe parziale viene aggiunto un metodo di `Update`*NOMECLASSEDIENTITÀ alla* .

   4. Accedere ai valori delle singole colonne usando l'argomento `instance`, come mostrato nel codice seguente:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      Per i progetti C#:

   5. Poiché C# i progetti non generano automaticamente i gestori eventi, è possibile usare IntelliSense per creare il metodo partial `Update`*NomeClasse* .

   6. Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di aggiornamento relativo alla classe per cui si desidera aggiungere la convalida. Il codice seguente è simile al codice generato quando si seleziona un metodo parziale `Update`*ClassName* :

      ```csharp
      partial void UpdateCLASSNAME(CLASSNAME instance)
      {
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
          {
              string ErrorMessage = "Invalid data!";
              throw new System.Exception(ErrorMessage);
          }
      }
      ```

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) la [convalida dei dati](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
