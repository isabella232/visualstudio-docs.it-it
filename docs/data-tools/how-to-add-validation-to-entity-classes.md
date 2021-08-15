---
title: 'Procedura: Aggiungere la convalida a classi di entità'
description: Vedere come aggiungere la convalida alle classi di entità. Aggiungere la convalida per le modifiche a un valore in una colonna specifica. Aggiungere la convalida per gli aggiornamenti a una classe di entità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e11f02aa17faffcfcd138136646c4a237bd697ec6cf9ff51797aaaaa63968bc2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264441"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Procedura: Aggiungere la convalida a classi di entità
La *convalida* delle classi di entità rappresenta il processo mediante cui si conferma che i valori immessi negli oggetti dati sono conformi ai vincoli presenti nello schema di un oggetto e alle regole stabilite per l'applicazione. Per ridurre gli errori, è opportuno convalidare i dati prima di inviare aggiornamenti al database sottostante. La convalida consente anche di ridurre il numero potenziale di round trip tra un'applicazione e il database.

Gli strumenti LINQ to SQL [in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) forniscono metodi parziali che consentono agli utenti di estendere il codice generato dalla finestra di progettazione che viene eseguito durante inserimenti, aggiornamenti ed eliminazioni di entità complete e anche durante e dopo le singole modifiche di colonna.

> [!NOTE]
> Questo argomento illustra i passaggi di base per l'aggiunta della convalida alle classi di entità tramite **O/R Designer.** Poiché potrebbe essere difficile seguire questi passaggi generici senza fare riferimento a una classe di entità specifica, viene fornita una procedura dettagliata che usa dati effettivi.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Aggiungere la convalida per le modifiche al valore in una colonna specifica
In questa procedura viene mostrato come convalidare i dati quando viene modificato il valore in una colonna. Dato che la convalida viene eseguita nella definizione di classe anziché nell'interfaccia utente, se il valore causa l'esito negativo della convalida, viene generata un'eccezione. Implementare la gestione degli errori per il codice nell'applicazione che tenta di modificare i valori della colonna.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Per convalidare i dati durante la modifica del valore di una colonna

1. Aprire o creare un nuovo file classes LINQ to SQL (file **con estensione dbml)** in **O/R Designer.** (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. In **Object Relational Designer** fare clic con il pulsante destro del mouse sulla classe per cui si vuole aggiungere la convalida e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3. Posizionare il cursore nella classe parziale.

4. Per i progetti di Visual Basic:

    1. Espandere l'elenco **Nome metodo**.

    2. Individuare il metodo **OnNOMECOLONNAChanging** per la colonna a cui si vuole aggiungere la convalida.

    3. Viene aggiunto un metodo `OnCOLUMNNAMEChanging` alla classe parziale.

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

    Poiché i progetti C# non generano automaticamente gestori eventi, è possibile usare IntelliSense per creare i metodi parziali che modificano la colonna. Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di modifica delle colonne relativo alla colonna per cui si desidera aggiungere la convalida. Il codice seguente è simile al codice generato quando si seleziona un metodo parziale di modifica della colonna:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Aggiungere la convalida per gli aggiornamenti a una classe di entità
Oltre a controllare i valori durante le modifiche, è anche possibile convalidare i dati quando si tenta di aggiornare una classe di entità completa. La convalida durante un tentativo di aggiornamento consente di confrontare i valori di più colonne, se richiesto dalle regole business. Nella procedura riportata di seguito viene mostrato come eseguire la convalida quando si tenta di aggiornare una classe di entità completa.

> [!NOTE]
> Il codice di convalida per gli aggiornamenti alle classi di entità complete viene eseguito nella classe <xref:System.Data.Linq.DataContext> parziale, anziché nella classe parziale di una classe di entità specifica.

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Per convalidare i dati durante un aggiornamento a una classe di entità

1. Aprire o creare un nuovo file classes LINQ to SQL (file **con estensione dbml)** in **O/R Designer.** (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. Fare clic con il pulsante destro del mouse su un'area vuota in **Object Relational Designer** e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per `DataContext`.

3. Posizionare il cursore nella classe parziale per `DataContext`.

4. Per i progetti di Visual Basic:

    1. Espandere l'elenco **Nome metodo**.

    2. Fare clic su **UpdateNOMECLASSEDIENTITÀ**.

    3. Viene aggiunto un metodo `UpdateENTITYCLASSNAME` alla classe parziale.

    4. Accedere ai valori delle singole colonne usando l'argomento `instance`, come mostrato nel codice seguente:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Per i progetti C#:

    Poiché i progetti C# non generano automaticamente gestori eventi, è possibile usare IntelliSense per creare il metodo `UpdateCLASSNAME` parziale. Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di aggiornamento per la classe in cui si vuole aggiungere la convalida. Il codice seguente è simile al codice generato quando si seleziona un `UpdateCLASSNAME` metodo parziale:

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

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Convalida dei dati](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
