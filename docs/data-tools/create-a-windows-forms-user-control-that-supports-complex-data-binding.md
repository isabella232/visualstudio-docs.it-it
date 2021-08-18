---
title: Creare un controllo utente Windows Form con data binding
description: Informazioni su come creare un Windows utente form che supporta i data binding, implementando la classe ComplexBindingPropertiesAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b179c957320badae098d0f82107d26ebf0859df1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052980"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding complesso

Quando si visualizzano dati nei form in Windows applicazioni, è possibile scegliere i controlli esistenti dalla casella degli **strumenti**. In caso contrario, è possibile creare controlli personalizzati se l'applicazione richiede funzionalità non disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contengono `DataSource` e la proprietà `DataMember` che può essere associata ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.

Per altre informazioni sulla creazione di controlli, vedere [Sviluppo di Windows Form in fase di progettazione.](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)

Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo degli attributi di associazione dati|
| - |
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [Create a Windows Forms user control that supports simple data binding](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [Create a Windows Forms user control that supports lookup data binding](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Questa procedura dettagliata crea un controllo complesso che visualizza righe di dati da una tabella. In questo esempio viene usata la tabella `Customers` del database di esempio Northwind. Il controllo utente complesso visualizzerà la tabella dei clienti in un oggetto <xref:System.Windows.Forms.DataGridView> nel controllo personalizzato.

Durante questa procedura dettagliata si apprenderà come:

- Aggiungere un nuovo **controllo utente** al progetto.

- Progettare visivamente il controllo utente.

- Implementare l'attributo `ComplexBindingProperty`.

- Creare un set di dati con [la Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Impostare la **tabella Customers** nella finestra Origini [dati per](add-new-data-sources.md#data-sources-window) usare il nuovo controllo complesso.

- Aggiungere il nuovo controllo trascinandolo dalla finestra **Origini dati** in **Form1**.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** **Nell'Programma di installazione di Visual Studio** è possibile installare SQL Server Express Local DB come parte del  carico di lavoro Elaborazione ed archiviazione dati o come singolo componente.

1. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la **finestra SQL Server Esplora oggetti** dati. (SQL Server Esplora oggetti viene installato come parte  del carico di lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo . Fare clic con il pulsante destro del mouse Local DB'istanza e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    1. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    1. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

## <a name="create-a-windows-forms-app-project"></a>Creare un progetto Windows'app Forms

Il primo passaggio consiste nel creare un **progetto Windows'app Forms** per C# o Visual Basic. Assegnare al progetto il nome **ComplexControlWalkthrough**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Poiché questa procedura dettagliata crea un controllo associabile a dati complesso da **un controllo utente**, aggiungere un elemento **Controllo** utente al progetto:

1. Scegliere **Aggiungi controllo utente** dal menu **Progetto**.

1. Digitare **ComplexDataGridView** nell'area **Nome** e quindi fare clic su **Aggiungi**.

    Il controllo **ComplexDataGridView** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.

## <a name="design-the-complexdatagridview-control"></a>Progettare il controllo ComplexDataGridView

Per aggiungere un <xref:System.Windows.Forms.DataGridView> oggetto al controllo utente, trascinare un oggetto dalla casella degli strumenti <xref:System.Windows.Forms.DataGridView> all'area di progettazione del controllo utente. 

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding obbligatorio

Per controlli semplici che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Passare al controllo **ComplexDataGridView** per la visualizzazione del codice. Scegliere **Codice** dal menu **Visualizza**.

1. Sostituire il codice nel controllo `ComplexDataGridView` con la stringa seguente:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb" id="Snippet4":::

1. Scegliere **Compila** soluzione dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Usare la **Configurazione guidata origine** dati per creare un'origine dati basata sulla tabella nel database di esempio `Customers` Northwind:

1. Per aprire la **finestra Origini** dati , **scegliere** Mostra origini dati dal menu **Dati**.

2. Nella finestra **Origini dati** selezionare Aggiungi nuova **origine dati** per avviare la Configurazione **guidata origine** dati.

3. Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

   - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

   - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti.**

7. Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

8. Selezionare la tabella `Customers`, quindi fare clic su **Fine**.

   **NorthwindDataSet** viene aggiunto al progetto e la `Customers` tabella viene visualizzata nella finestra **Origini** dati.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Impostare la tabella Customers per l'uso del controllo ComplexDataGridView

**All'interno della finestra** Origini dati è possibile impostare il controllo da creare prima di trascinare elementi nel form:

1. Aprire **Form1** nella finestra di progettazione.

1. Espandere il nodo **Customers** nella finestra **Origini dati**.

1. Fare clic sulla freccia a discesa nel nodo **Customers** e scegliere **Personalizza**.

1. Selezionare **ComplexDataGridView** nell'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.

1. Fare clic sulla freccia a discesa nella tabella `Customers` e scegliere **ComplexDataGridView** nell'elenco di controllo.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati a dati trascinando elementi dalla **finestra Origini** dati nel form. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** al form. Verificare che il **controllo ComplexDataGridView** sia usato per visualizzare i dati della tabella.

## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **F5 per** eseguire l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:

- Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.

- Creazione di controlli che supportano scenari di ricerca. Per altre informazioni, vedere [Create a Windows Forms user control that supports lookup data binding](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vedi anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Controlli form](/dotnet/framework/winforms/controls/index)
