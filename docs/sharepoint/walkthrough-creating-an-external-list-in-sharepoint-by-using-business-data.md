---
title: 'Procedura dettagliata: Creazione di un elenco esterno in SharePoint utilizzando i dati aziendali | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18848f0ebd6ffa289ea09553de82f5b9eb893181
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295839"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Procedura dettagliata: Creare un elenco esterno in SharePoint utilizzando i dati di business

Il servizio di integrazione applicativa dei dati (BDC) consente di visualizzare i dati aziendali provenienti da server back-end applicazioni, servizi Web e i database in SharePoint.

Questa procedura dettagliata illustra come creare un modello per il servizio di integrazione applicativa dei dati che restituisce informazioni sui contatti in un database di esempio. Si creerà quindi un elenco esterno in SharePoint con questo modello.

In questa procedura dettagliata vengono illustrate le attività seguenti:

- Creazione di un progetto.
- Aggiunta di un'entità al modello.
- Aggiunta di un metodo finder.
- Aggiunta di un metodo Finder specifico.
- Test del progetto.

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- Accesso al database di esempio AdventureWorks. Per altre informazioni su come installare il database AdventureWorks, vedere [SQL Server Sample Databases](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Creare un progetto che contiene un modello di integrazione applicativa dei dati

1. Nella barra dei menu in Visual Studio, scegliere **File** > **New** > **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** elemento.

3. Nel **modelli** riquadro, scegliere **progetto SharePoint 2010**, denominare il progetto **AdventureWorksTest**e quindi scegliere il **OK** pulsante .

     Il **Personalizzazione guidata SharePoint** viene visualizzata. In questa procedura guidata, è possibile specificare il sito che si userà per il debug del progetto e impostare il livello di attendibilità della soluzione.

4. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione per impostare il livello di attendibilità.

5. Scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

6. Nelle **Esplora soluzioni**, scegliere il nodo del progetto SharePoint.

7. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

8. Nel **modelli** riquadro, scegliere **Business Data Connectivity Model (solo soluzione Farm)**, denominare il progetto **AdventureWorksContacts**e quindi scegliere il **Add** pulsante.

## <a name="add-data-access-classes-to-the-project"></a>Aggiungere classi di accesso ai dati al progetto

1. Nella barra dei menu, scegliere **degli strumenti** > **Connetti al Database**.

     Il **Aggiungi connessione** verrà visualizzata la finestra di dialogo.

2. Aggiungere una connessione al database di esempio AdventureWorks di SQL Server.

     Per altre informazioni, vedere [Aggiungi/Modifica connessione (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. Scegliere il nodo di progetto in **Esplora soluzioni**.

4. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

5. Nel **modelli installati** riquadro, scegliere il **dati** nodo.

6. Nel **modelli** riquadro, scegliere **classi LINQ to SQL**.

7. Nel **nome** , specificare **AdventureWorks**, quindi scegliere il **Aggiungi** pulsante.

     Verrà aggiunto al progetto un file con estensione dbml e verrà aperto Object Relational Designer (O/R Designer).

8. Nella barra dei menu, scegliere **View** > **Esplora Server**.

9. Nelle **Esplora Server**, espandere il nodo che rappresenta il database di esempio AdventureWorks e quindi espandere il **tabelle** nodo.

10. Aggiungere il **Contact (Person)** tabella nella finestra di Progettazione relazionale oggetti.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. La classe di entità dispone di proprietà che eseguono il mapping alle colonne della tabella Contact (Person).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Rimuovere l'entità predefinita dal modello di integrazione applicativa dei dati

Il **Business Data Connectivity Model** progetto aggiunge un'entità predefinita denominata Entity1 al modello. Rimuovere questa entità. In seguito si aggiungerà una nuova entità. A partire da un modello vuoto consente di ridurre il numero di passaggi necessari per completare la procedura dettagliata.

1. Nelle **Esplora soluzioni**, espandere il **BdcModel1** nodo e quindi aprire il *BdcModel1.bdcm* file.

2. Il file di modello di integrazione applicativa dei dati viene aperto nella finestra di progettazione integrazione applicativa dei dati.

3. Nella finestra di progettazione, aprire il menu di scelta rapida **Entity1**, quindi scegliere **eliminare**.

4. In **Esplora soluzioni**, aprire il menu di scelta rapida *Entity1.vb* (in Visual Basic) o *Entity1.cs* (in c#), quindi scegliere **Elimina** .

5. Aprire il menu di scelta rapida *Entity1Service.vb* (in Visual Basic) o *per Entity1Service.cs* (in c#), quindi scegliere **Elimina**.

## <a name="add-an-entity-to-the-model"></a>Aggiungere un'entità al modello

Aggiungere un'entità nel modello. È possibile aggiungere le entità da Visual Studio **casella degli strumenti** nella finestra di progettazione integrazione applicativa dei dati.

1. Nella barra dei menu, scegliere **View** > **casella degli strumenti**.

2. Nel **BusinessDataConnectivity** scheda della finestra del **della casella degli strumenti**, aggiungere un' **entità** nella finestra di progettazione integrazione applicativa dei dati.

     La nuova entità viene visualizzata nella finestra di progettazione. Visual Studio aggiunge un file denominato *EntityService* (in Visual Basic) o *EntityService.cs* (in c#) al progetto.

3. Nella barra dei menu, scegliere **View** > **delle proprietà** > **finestra**.

4. Nel **proprietà** impostare nella finestra di **nome** valore della proprietà **contatto**.

5. Nella finestra di progettazione, aprire il menu di scelta rapida per l'entità, scegliere **Add**, quindi scegliere **identificatore**.

     Viene visualizzato un nuovo identificatore dell'entità.

6. Nel **delle proprietà** finestra, modificare il nome dell'identificatore da **ContactID**.

7. Nel **nome del tipo** casella di riepilogo **System.Int32**.

## <a name="add-a-specific-finder-method"></a>Aggiungere un metodo Finder specifico

Per abilitare il servizio di integrazione applicativa dei dati visualizzare un contatto specifico, è necessario aggiungere un metodo Finder specifico. Il servizio di integrazione applicativa dei dati chiama il metodo Finder specifico quando un utente seleziona un elemento in un elenco e poi sceglie la **elemento della visualizzazione** pulsante della barra multifunzione.

Aggiungere un metodo Finder specifico per l'entità Contact usando il **Dettagli metodo BDC** finestra. Per restituire un'entità specifica, aggiungere codice al metodo.

1. Nella finestra di progettazione integrazione applicativa dei dati, scegliere il **contatto** entità.

2. Nella barra dei menu, scegliere **View** > **Other Windows** > **Dettagli metodo BDC**.

     Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati.

3. Nel **aggiungere un metodo** casella di riepilogo **Crea metodo Finder specifico**.

     Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nei **Dettagli metodo BDC** finestra.

    - Un metodo denominato metodo ReadItem.

    - Un parametro di input per il metodo.

    - Un parametro restituito del metodo.

    - Un descrittore di tipo per ogni parametro.

    - Un'istanza del metodo per il metodo.

4. Nel **Dettagli metodo BDC** finestra, aprire l'elenco visualizzato per il **Contact** descrittore di tipo e quindi scegliere **modifica**.

     Il **Esplora integrazione applicativa dei dati** apre e offre una visualizzazione gerarchica del modello.

5. Nel **delle proprietà** finestra, aprire l'elenco accanto al **TypeName** proprietà, scegliere il **progetto corrente** scheda e quindi scegliere il **contatto**proprietà.

6. Nel **Esplora integrazione Applicativa**, aprire il menu di scelta rapida del **contatto**e quindi scegliere **Aggiungi descrittore tipo**.

     Un nuovo descrittore di tipo denominato **TypeDescriptor1** viene visualizzato nei **Esplora integrazione applicativa dei dati**.

7. Nel **delle proprietà** impostare nella finestra di **nome** valore della proprietà da **ContactID**.

8. Aprire l'elenco accanto al **nomeTipo** proprietà, quindi scegliere **Int32**.

9. Aprire l'elenco accanto al **Identifier** proprietà, quindi scegliere **ContactID**.

10. Ripetere il passaggio 6 per creare un descrittore di tipi per ognuno dei campi seguenti.

    |nome|Nome tipo|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Telefono|System.String|
    |Indirizzo di posta elettronica|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Nella finestra di progettazione integrazione applicativa dei dati, nelle **contatto** entità, aprire il **ReadItem** (metodo).

     Il file di codice del servizio di Contact verrà aperto nell'Editor di codice.

12. Nel `ContactService` classe, sostituire il `ReadItem` metodo con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

    - Recupera un record dalla tabella Contact del database AdventureWorks.

    - Restituisce un'entità di contatto per il servizio di integrazione applicativa dei dati.

    > [!NOTE]
    > Sostituire il valore del `ServerName` campo con il nome del server.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Aggiungere un metodo finder

Per abilitare il servizio di integrazione applicativa dei dati visualizzare i contatti in un elenco, è necessario aggiungere un metodo Finder. Aggiungere un metodo Finder per l'entità Contact usando il **Dettagli metodo BDC** finestra. Per restituire una raccolta di entità per il servizio di integrazione applicativa dei dati, aggiungere codice al metodo.

1. Nella finestra di progettazione integrazione applicativa dei dati, scegliere il **contatto** entità.

2. Nel **Dettagli metodo BDC** Comprimi finestra la **ReadItem** nodo.

3. Nel **aggiungere un metodo** nell'elenco il **ReadList** metodo, scegliere **Crea metodo Finder**.

     Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.

4. Nella finestra di progettazione integrazione applicativa dei dati, nelle **contatto** entità, aprire il **ReadList** (metodo).

     Il file di codice per il servizio di Contact verrà aperto nell'editor di codice.

5. Nel `ContactService` classe, sostituire il `ReadList` metodo con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

   - Recupera i dati dalla tabella dei contatti del database AdventureWorks.

   - Restituisce un elenco di entità di contatto per il servizio di integrazione applicativa dei dati.

     > [!NOTE]
     > Sostituire il valore del `ServerName` campo con il nome del server.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Il progetto di test

Quando si esegue il progetto, viene aperto il sito di SharePoint e Visual Studio aggiunge il modello per il servizio di integrazione applicativa dei dati. Creare un elenco esterno in SharePoint che fa riferimento l'entità Contact. Nell'elenco vengono visualizzati i dati per i contatti nel database AdventureWorks.

> [!NOTE]
> Potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint, è possibile eseguire il debug, la soluzione. Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Premere **F5**.

     Viene aperto il sito di SharePoint.

2. Nel **Azioni sito** menu, scegliere il **altre opzioni** comando.

3. Nel **Create** pagina, scegliere il **elenco esterno** modello e quindi scegliere il **Create** pulsante.

4. Denominare l'elenco personalizzato **contatti**.

5. Scegliere il pulsante Sfoglia accanto al **tipo di contenuto esterno** campo.

6. Nel **Selezione tipo di contenuto esterno** finestra di dialogo scegliere la **AdventureWorksContacts.BdcModel1.Contact** elemento e quindi scegliere il **Create** pulsante.

     In SharePoint viene creato un elenco esterno con i contatti del database di esempio AdventureWorks.

7. Per testare il metodo Finder specifico, scegliere un contatto nell'elenco.

8. Sulla barra multifunzione scegliere la **elementi** scheda e quindi scegliere il **Visualizza elemento** comando.

     I dettagli del contatto selezionato verranno visualizzati in un form.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su come progettare modelli per il servizio di integrazione applicativa dei dati in SharePoint, vedere gli argomenti seguenti:

- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Vedere anche

[Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)  
[Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)  
[Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)  
[Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
