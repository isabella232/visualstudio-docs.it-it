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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e79d4ba6db70876539aa2e85f0579953937cab14
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756324"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca
Quando si visualizzano dati nei Windows Form, è possibile scegliere i controlli esistenti dal **casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità non disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.LookupBindingPropertiesAttribute> possono contenere tre proprietà associabili ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.ComboBox>.

 Per altre informazioni sulla creazione di controlli, vedere [lo sviluppo di Windows Form controlli in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo dell'attributo di data binding|
|-----------------------------------|
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Il processo è descritto in questa pagina di procedura dettagliata.|

 Questa procedura dettagliata crea un controllo di ricerca che effettua l'associazione ai dati di due tabelle. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind. È associato il controllo di ricerca per il `CustomerID` campo il `Orders` tabella. Tale valore viene utilizzato per cercare i `CompanyName` dal `Customers` tabella.

 Durante questa procedura dettagliata, si apprenderà come:

-   Creare una nuova **Windows Forms Application**.

-   Aggiungere un nuovo **controllo utente** al progetto.

-   Progettare visivamente il controllo utente.

-   Implementare l'attributo `LookupBindingProperty`.

-   Creare un set di dati con il **configurazione dell'origine dati** procedura guidata.

-   Impostare il **CustomerID** colonna sul **ordini** tabella il **Zdroje dat** finestra, usare il nuovo controllo.

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

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione di Windows Form
 Il primo passaggio consiste nel creare un **Windows Forms Application**.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **LookupControlWalkthrough**, quindi scegliere **OK**.

     Il **LookupControlWalkthrough** progetto viene creato e aggiunto alla **Esplora soluzioni**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto
 Questa procedura dettagliata crea un controllo di ricerca da un **controllo utente**, quindi l'aggiunta di un **controllo utente** elemento per il **LookupControlWalkthrough** progetto.

#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto

1.  Dal **Project** dal menu **Aggiungi controllo utente**.

2.  Tipo `LookupBox` nella **Name** area e quindi fare clic su **Add**.

     Il **LookupBox** controllo viene aggiunto al **Esplora soluzioni**e nella finestra di progettazione.

## <a name="design-the-lookupbox-control"></a>Progettare il controllo LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Per progettare il controllo LookupBox

-   Trascinare un <xref:System.Windows.Forms.ComboBox> dal **casella degli strumenti** nell'area di progettazione del controllo utente.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto
 Per controlli di ricerca che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Per implementare l'attributo LookupBindingProperties

1.  Passare il **LookupBox** controllo alla visualizzazione codice. (Nelle **View** menu, scegliere **codice**.)

2.  Sostituire il codice nel controllo `LookupBox` con la stringa seguente:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database
Questo passaggio viene creata un'origine dati usando il **configurazione dell'origine dati** procedura guidata, in base il `Customers` e `Orders` tabelle nel database di esempio Northwind.

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione dell'origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

7.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo.

8.  Selezionare il `Customers` e `Orders` tabelle e quindi fare clic su **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e il `Customers` e `Orders` le tabelle vengono visualizzate nel **Zdroje dat** finestra.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Impostare la colonna CustomerID della tabella Orders per usare il controllo LookupBox
 All'interno di **Zdroje dat** finestra, è possibile impostare il controllo deve essere creato prima di trascinare gli elementi nel form.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Per impostare la colonna CustomerID da associare al controllo LookupBox

1.  Aprire **Form1** nella finestra di progettazione.

2.  Espandere la **clienti** nodo il **Zdroje dat** finestra.

3.  Espandere il **ordini** nodo (quello nel **clienti** nodo sotto il **Fax** colonna).

4.  Fare clic sulla freccia giù sul **ordini** nodo, scegliere **dettagli** dall'elenco di controllo.

5.  Fare clic sulla freccia giù sul **CustomerID** colonna (nelle **ordini** nodo) e scegliere **Personalizza**.

6.  Selezionare il **LookupBox** dall'elenco dei **controlli associati** nel **opzioni di personalizzazione dell'interfaccia utente dati** nella finestra di dialogo.

7.  Fare clic su **OK**.

8.  Fare clic sulla freccia giù sul **CustomerID** colonna e scegliere **LookupBox**.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form
 È possibile creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare controlli associati ai dati nel Windows Form

-   Trascinare il **ordini** nodo dalle **Zdroje dat** finestra nei Form, Windows e verificare che il **LookupBox** controllo viene usato per visualizzare i dati nel `CustomerID` colonna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associare il controllo di ricerca di CompanyName dalla tabella Customers

#### <a name="to-setup-the-lookup-bindings"></a>Per impostare le associazioni di ricerca

-   Selezionare principale **i clienti** nodo il **Zdroje dat** finestra e quindi trascinare casella combinata il **CustomerIDLookupBox** nel **Form1** .

     Ciò consente di impostare il data binding per visualizzare il `CompanyName` dal `Customers` tabella, pur mantenendo il `CustomerID` valore dal `Orders` tabella.

## <a name="running-the-application"></a>Esecuzione dell'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

-   Premere **F5** per eseguire l'applicazione.

-   Spostarsi tra alcuni record e verificare che il `CompanyName` viene visualizzato nei `LookupBox` controllo.

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)