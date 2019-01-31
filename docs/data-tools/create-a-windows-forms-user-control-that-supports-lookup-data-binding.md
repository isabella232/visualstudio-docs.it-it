---
title: Utilizzo tabelle di ricerca nel data binding - controlli Windows Form | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: f62308e44ee0687f57a15db7039656a8c4ba7dbb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917913"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding di ricerca

Quando si visualizzano dati nei Windows Form, è possibile scegliere i controlli esistenti dalla **Casella degli strumenti** o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.LookupBindingPropertiesAttribute> possono contenere tre proprietà associabili ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.ComboBox>.

Per altre informazioni sulla creazione di controlli, vedere [lo sviluppo di Windows Form controlli in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo dell'attributo di data binding|
| - |
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Il processo è descritto in questa pagina di procedura dettagliata.|

Questa procedura dettagliata crea un controllo di ricerca che effettua l'associazione ai dati di due tabelle. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind. È associato il controllo di ricerca per il `CustomerID` campo il `Orders` tabella. Tale valore viene utilizzato per cercare i `CompanyName` dal `Customers` tabella.

Durante questa procedura dettagliata si apprenderà come:

-   Creare una nuova applicazione **Windows Forms Application**.

-   Aggiungere un nuovo **controllo utente** al progetto.

-   Progettare visivamente il controllo utente.

-   Implementare l'attributo `LookupBindingProperty`.

-   Creare un set di dati con il **configurazione dell'origine dati** procedura guidata.

-   Impostare la colonna **CustomerID** nella tabella **Orders** della finestra **Origini dati** per usare il nuovo controllo.

-   Creare un form per visualizzare i dati nel controllo.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-a-windows-forms-app-project"></a>Creare un progetto di app di Windows Form

Il primo passaggio consiste nel creare un **Windows Forms Application** progetto.

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual C#**  oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Desktop di Windows**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **LookupControlWalkthrough**, quindi scegliere **OK**.

     Il progetto **LookupControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Dal momento che questa procedura dettagliata crea un controllo di ricerca da un **Controllo utente**, è necessario aggiungere un elemento **Controllo utente** al progetto **LookupControlWalkthrough**.

1.  Selezionare **Aggiungi controllo utente** dal menu **Progetto**.

2.  Tipo `LookupBox` nella **Name** area e quindi fare clic su **Add**.

     Il controllo **LookupBox** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.

## <a name="design-the-lookupbox-control"></a>Progettare il controllo LookupBox

Per progettare il controllo LookupBox, trascinare un <xref:System.Windows.Forms.ComboBox> dal **casella degli strumenti** nell'area di progettazione del controllo utente.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto

Per controlli di ricerca che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1.  Passare al controllo **LookupBox** per la visualizzazione del codice. Scegliere **Codice** dal menu **Visualizza**.

2.  Sostituire il codice nel controllo `LookupBox` con la stringa seguente:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Questo passaggio crea un'origine dati usando la **Configurazione guidata origine dati** basata sulle tabelle `Customers` e `Orders` nel database di esempio Northwind.

1.  Per aprire la **Zdroje dat** finestra via il **Data** dal menu fare clic su **Mostra origini dati**.

2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

7.  Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

8.  Selezionare le tabelle `Customers` e `Orders`, quindi fare clic su **Fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle `Customers` e `Orders` vengono visualizzate nella finestra **Origini dati**.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Impostare la colonna CustomerID della tabella Orders per usare il controllo LookupBox

Nella finestra **Origini dati** è possibile impostare il controllo da creare prima di trascinare elementi nel modulo.

1.  Aprire **Form1** nella finestra di progettazione.

2.  Espandere il nodo **Customers** nella finestra **Origini dati**.

3.  Espandere il nodo **Orders** (nel nodo **Customers** sotto la colonna **Fax**).

4.  Fare clic sulla freccia a discesa nel nodo **Orders** e scegliere **Dettagli** dall'elenco di controllo.

5.  Fare clic sulla freccia a discesa nella colonna **CustomerID** (nel nodo **Orders**) e scegliere **Personalizza**.

6.  Selezionare **LookupBox** dall'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.

7.  Fare clic su **OK**.

8.  Fare clic sulla freccia a discesa nella colonna **CustomerID** e scegliere **LookupBox**.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati ai dati trascinando elementi dalla finestra **Origini dati** in **Form1**.

Per creare controlli associati a dati del Form di Windows, trascinare il **ordini** nodo dalle **Zdroje dat** finestra nei Form, Windows e verificare che il **LookupBox** controllo è Consente di visualizzare i dati nel `CustomerID` colonna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associare il controllo di ricerca di CompanyName dalla tabella Customers

Per configurare le associazioni di ricerca, selezionare l'oggetto principale **clienti** nodo il **Zdroje dat** finestra e quindi trascinare casella combinata il **CustomerIDLookupBox** su **Form1**.

Viene in questo modo impostato il data binding per visualizzare `CompanyName` dalla tabella `Customers`, mantenendo al contempo il valore `CustomerID` della tabella `Orders`.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

-   Premere **F5** per eseguire l'applicazione.

-   Spostarsi all'interno di alcuni record e verificare che `CompanyName` venga mostrato nel controllo `LookupBox`.

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)