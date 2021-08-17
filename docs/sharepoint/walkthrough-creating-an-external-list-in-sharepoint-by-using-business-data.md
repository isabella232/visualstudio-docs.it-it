---
title: Creare un elenco esterno in SharePoint dati aziendali
description: Creare un modello per il servizio BDC che restituisca informazioni sui contatti in un database aziendale, quindi creare un elenco esterno SharePoint questo modello.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a265a80116da0d1d2ffac469f7193c737a65a93a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075905"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Procedura dettagliata: Creare un elenco esterno in SharePoint usando i dati aziendali

Il servizio BDC (Business Data Connectivity) consente SharePoint visualizzare i dati aziendali da applicazioni server back-end, servizi Web e database.

Questa procedura dettagliata illustra come creare un modello per il servizio BDC che restituisce informazioni sui contatti in un database di esempio. Si creerà quindi un elenco esterno in SharePoint usando questo modello.

Vengono illustrate le attività seguenti:

- Creazione di un progetto.
- Aggiunta di un'entità al modello.
- Aggiunta di un metodo finder.
- Aggiunta di un metodo Finder specifico.
- Test del progetto.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- Accesso al database di esempio AdventureWorks. Per altre informazioni su come installare il database AdventureWorks, vedere SQL Server [Database di esempio](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Creare un progetto contenente un modello BDC

1. Nella barra dei menu in Visual Studio scegliere **File**  >  **nuovo**  >  **Project**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In **Visual C#** o **Visual Basic** espandere  il nodo SharePoint e quindi scegliere l'elemento **2010.**

3. Nel riquadro **Modelli** scegliere SharePoint **2010 Project**, assegnare al progetto il nome **AdventureWorksTest** e quindi scegliere **OK.**

     Verrà **SharePoint personalizzazione guidata.** In questa procedura guidata è possibile specificare il sito che verrà utilizzato per eseguire il debug del progetto e impostare il livello di attendibilità della soluzione.

4. Scegliere il **pulsante di opzione Distribuisci come soluzione farm** per impostare il livello di attendibilità.

5. Scegliere il **pulsante** Fine per accettare il sito locale SharePoint predefinito.

6. In **Esplora soluzioni** scegliere il nodo SharePoint progetto.

7. Sulla barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento .

8. Nel riquadro **Modelli** scegliere Modello di integrazione applicativa dei dati **(solo** soluzione farm), assegnare al progetto il nome **AdventureWorksContacts** e quindi scegliere **il pulsante** Aggiungi.

## <a name="add-data-access-classes-to-the-project"></a>Aggiungere classi di accesso ai dati al progetto

1. Sulla barra dei menu scegliere **Strumenti Connessione**  >  **database**.

     Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.

2. Aggiungere una connessione al database SQL Server di esempio AdventureWorks.

     Per altre informazioni, vedere [Add/Modify Connection (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. Scegliere il nodo di progetto in **Esplora soluzioni**.

4. Sulla barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

5. Nel riquadro **Modelli installati** scegliere il **nodo** Dati.

6. Nel riquadro **Modelli** scegliere LINQ to SQL **classi**.

7. Nella casella **Nome** specificare **AdventureWorks** e quindi scegliere il **pulsante** Aggiungi.

     Verrà aggiunto al progetto un file con estensione dbml e verrà aperto Object Relational Designer (O/R Designer).

8. Sulla barra dei menu scegliere **Visualizza Esplora server**  >  .

9. In **Esplora server** espandere il nodo che rappresenta il database di esempio AdventureWorks e quindi espandere **il nodo** Tabelle.

10. Aggiungere la **tabella Contact (Person)** in O/R Designer.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. La classe di entità ha proprietà mappate alle colonne della tabella Contact (Person).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Rimuovere l'entità predefinita dal modello BDC

Il **progetto Modello di connettività dati** business aggiunge un'entità predefinita denominata Entity1 al modello. Rimuovere questa entità. Successivamente si aggiungerà una nuova entità. A partire da un modello vuoto, si riduce il numero di passaggi necessari per completare la procedura dettagliata.

1. In **Esplora soluzioni** espandere il **nodo BdcModel1** e quindi aprire il file *BdcModel1.bdcm.*

2. Il file del modello di integrazione applicativa dei dati viene aperto nella finestra di progettazione del data center BDC.

3. Nella finestra di progettazione aprire il menu di scelta rapida per **Entity1** e quindi scegliere **Elimina.**

4. In **Esplora soluzioni** aprire il menu di scelta rapida per *Entity1.vb* (in Visual Basic) o *Entity1.cs* (in C#) e quindi scegliere **Elimina**.

5. Aprire il menu di scelta rapida *per Entity1Service.vb* (in Visual Basic) o *Entity1Service.cs* (in C#) e quindi scegliere **Elimina**.

## <a name="add-an-entity-to-the-model"></a>Aggiungere un'entità al modello

Aggiungere un'entità al modello. È possibile aggiungere entità dalla casella degli strumenti Visual Studio **alla** finestra di progettazione del data center BDC.

1. Sulla barra dei menu scegliere **Visualizza casella degli**  >  **strumenti**.

2. Nella scheda **BusinessDataConnectivity della** Casella **degli** strumenti aggiungere **un'entità** nella finestra di progettazione del data center BDC.

     La nuova entità viene visualizzata nella finestra di progettazione. Visual Studio aggiunge un file denominato *EntityService.vb* (in Visual Basic) o *EntityService.cs* (in C#) al progetto.

3. Sulla barra dei menu scegliere **Visualizza**  >  **finestra**  >  **Proprietà**.

4. Nella finestra **Proprietà** impostare il **valore della proprietà Name** su **Contact**.

5. Nella finestra di progettazione aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi** e quindi **identificatore**.

     Nell'entità viene visualizzato un nuovo identificatore.

6. Nella finestra **Proprietà** modificare il nome dell'identificatore in **ContactID**.

7. **Nell'elenco Nome tipo** scegliere **System.Int32**.

## <a name="add-a-specific-finder-method"></a>Aggiungere un metodo Finder specifico

Per consentire al servizio BDC di visualizzare un contatto specifico, è necessario aggiungere un metodo Finder specifico. Il servizio BDC chiama il metodo Finder specifico quando un utente sceglie un elemento in un elenco e quindi sceglie il pulsante **Visualizza** elemento sulla barra multifunzione.

Aggiungere un metodo Finder specifico all'entità Contact usando la **finestra Dettagli metodo BDC.** Per restituire un'entità specifica, aggiungere codice al metodo .

1. Nella finestra di progettazione del data center BDC scegliere **l'entità** Contatto.

2. Sulla barra dei menu scegliere **Visualizza altri**  >  **Windows**  >  **dettagli del metodo BDC.**

     Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati.

3. **Nell'elenco Add a Method (Aggiungi metodo)** scegliere Create Specific Finder Method **(Crea metodo Finder specifico).**

     Visual Studio aggiunge gli elementi seguenti al modello. Questi elementi vengono visualizzati nella finestra **Dettagli metodo BDC.**

    - Metodo denominato ReadItem.

    - Parametro di input per il metodo.

    - Parametro restituito per il metodo.

    - Descrittore di tipo per ogni parametro.

    - Istanza del metodo per il metodo .

4. Nella finestra **Dettagli metodo BDC** aprire l'elenco visualizzato per il descrittore del tipo di contatto e quindi scegliere **Modifica**. 

     Viene **aperto BDC Explorer** che offre una visualizzazione gerarchica del modello.

5. Nella finestra **Proprietà** aprire l'elenco accanto alla proprietà **TypeName,** scegliere la scheda Project **corrente** e quindi scegliere la proprietà **Contatto.**

6. In **BDC Explorer** aprire il menu di scelta rapida del **contatto** e quindi scegliere **Aggiungi descrittore di tipo**.

     Un nuovo descrittore di tipo denominato **TypeDescriptor1** viene visualizzato in **BDC Explorer.**

7. Nella finestra **Proprietà** impostare il **valore della proprietà Name** su **ContactID**.

8. Aprire l'elenco accanto alla **proprietà TypeName** e quindi scegliere **Int32**.

9. Aprire l'elenco accanto alla **proprietà Identificatore** e quindi scegliere **ContactID**.

10. Ripetere il passaggio 6 per creare un descrittore di tipo per ognuno dei campi seguenti.

    |Nome|Nome tipo|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Telefono|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Nell'entità Contact della  finestra di progettazione BDC aprire il **metodo ReadItem.**

     Il file di codice del servizio Contatti viene aperto nell'editor del codice.

12. Nella classe `ContactService` sostituire il metodo con il codice `ReadItem` seguente. Il codice esegue queste operazioni:

    - Recupera un record dalla tabella Contact del database AdventureWorks.

    - Restituisce un'entità Contact al servizio BDC.

    > [!NOTE]
    > Sostituire il valore del `ServerName` campo con il nome del server.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="add-a-finder-method"></a>Aggiungere un metodo finder

Per consentire al servizio BDC di visualizzare i contatti in un elenco, è necessario aggiungere un metodo Finder. Aggiungere un metodo Finder all'entità Contact usando la **finestra BDC Method Details (Dettagli metodo BDC).** Per restituire una raccolta di entità al servizio BDC, aggiungere codice al metodo .

1. Nella finestra di progettazione BDC scegliere **l'entità** Contact.

2. Nella finestra **BDC Method Details (Dettagli metodo BDC)** comprimere **il nodo ReadItem.**

3. **Nell'elenco Add a Method (Aggiungi** metodo) nel metodo **ReadList** scegliere **Create Finder Method (Crea metodo Finder).**

     Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.

4. Nell'entità Contact della  finestra di progettazione BDC aprire il **metodo ReadList.**

     Il file di codice per il servizio di Contact verrà aperto nell'editor di codice.

5. Nella classe `ContactService` sostituire il metodo con il codice `ReadList` seguente. Il codice esegue queste operazioni:

   - Recupera i dati dalla tabella Contacts del database AdventureWorks.

   - Restituisce un elenco di entità Contact al servizio BDC.

     > [!NOTE]
     > Sostituire il valore del `ServerName` campo con il nome del server.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="test-the-project"></a>Testare il progetto

Quando si esegue il progetto, viene aperto SharePoint sito di Visual Studio il modello al servizio di connettività dei dati di business. Creare un elenco esterno in SharePoint che fa riferimento all'entità Contact. I dati per i contatti nel database AdventureWorks vengono visualizzati nell'elenco.

> [!NOTE]
> Potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint possibile eseguire il debug della soluzione. Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

1. Premere **F5**.

     Verrà SharePoint il sito di lavoro.

2. Nel menu **Azioni sito** scegliere il **comando Altre** opzioni.

3. Nella pagina **Crea** scegliere il modello **Elenco** esterno e quindi scegliere **il pulsante** Crea.

4. Assegnare all'elenco personalizzato il **nome Contacts.**

5. Scegliere il pulsante Sfoglia accanto al **campo Tipo di contenuto** esterno.

6. Nella finestra **di dialogo** Selezione tipo di contenuto esterno scegliere l'elemento **AdventureWorksContacts.BdcModel1.Contact** e quindi scegliere **il pulsante** Crea.

     In SharePoint viene creato un elenco esterno con i contatti del database di esempio AdventureWorks.

7. Per testare il metodo Finder specifico, scegliere un contatto nell'elenco.

8. Sulla barra multifunzione scegliere la **scheda Elementi** e quindi scegliere il **comando Visualizza** elemento.

     I dettagli del contatto selezionato verranno visualizzati in un form.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come progettare modelli per il servizio BDC in SharePoint da questi argomenti:

- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md).
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Vedi anche

[Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md) 
 [Creare un modello di connettività dei dati aziendali](../sharepoint/creating-a-business-data-connectivity-model.md) 
 [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md) 
 [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)