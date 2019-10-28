---
title: Creazione di un elenco esterno in SharePoint tramite dati aziendali
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d670215d6a46003315992201c64c23185be7d715
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984657"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Procedura dettagliata: creare un elenco esterno in SharePoint usando i dati aziendali

Il servizio di integrazione applicativa dei dati consente a SharePoint di visualizzare i dati aziendali da applicazioni server back-end, servizi Web e database.

In questa procedura dettagliata viene illustrato come creare un modello per il servizio BDC che restituisce informazioni sui contatti in un database di esempio. Si creerà quindi un elenco esterno in SharePoint utilizzando questo modello.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un progetto.
- Aggiunta di un'entità al modello.
- Aggiunta di un metodo Finder.
- Aggiunta di un metodo di ricerca specifico.
- Test del progetto.

## <a name="prerequisites"></a>Prerequisites

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- Accesso al database di esempio AdventureWorks. Per ulteriori informazioni su come installare il database AdventureWorks, vedere [SQL Server database di esempio](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Creare un progetto che contiene un modello di integrazione applicativa dei dati

1. Nella barra dei menu di Visual Studio scegliere **File** > **nuovo** **progetto** > .

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In **Visual C#**  o **Visual Basic**espandere il nodo **SharePoint** , quindi scegliere l'elemento **2010** .

3. Nel riquadro **modelli** scegliere **progetto SharePoint 2010**, denominare il progetto **AdventureWorksTest**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** . In questa procedura guidata è possibile specificare il sito che verrà utilizzato per eseguire il debug del progetto e impostare il livello di attendibilità della soluzione.

4. Scegliere il pulsante di opzione **Distribuisci come soluzione farm** per impostare il livello di attendibilità.

5. Scegliere il pulsante **fine** per accettare il sito di SharePoint locale predefinito.

6. In **Esplora soluzioni**scegliere il nodo del progetto SharePoint.

7. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

8. Nel riquadro **modelli** scegliere modello di **integrazione applicativa dei dati (solo soluzione farm)** , assegnare al progetto il nome **AdventureWorksContacts**, quindi scegliere il pulsante **Aggiungi** .

## <a name="add-data-access-classes-to-the-project"></a>Aggiungere classi di accesso ai dati al progetto

1. Nella barra dei menu scegliere **strumenti** > **Connetti al database**.

     Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.

2. Aggiungere una connessione al database di esempio di SQL Server AdventureWorks.

     Per ulteriori informazioni, vedere [Aggiungi/modifica connessione (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. Scegliere il nodo di progetto in **Esplora soluzioni**.

4. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

5. Nel riquadro **modelli installati** scegliere il nodo **dati** .

6. Nel riquadro **modelli** scegliere **LINQ to SQL classi**.

7. Nella casella **nome** specificare **AdventureWorks**, quindi scegliere il pulsante **Aggiungi** .

     Verrà aggiunto al progetto un file con estensione dbml e verrà aperto Object Relational Designer (O/R Designer).

8. Nella barra dei menu scegliere **visualizza** > **Esplora server**.

9. In **Esplora server**espandere il nodo che rappresenta il database di esempio AdventureWorks, quindi espandere il nodo **tabelle** .

10. Aggiungere la tabella **Contact (Person)** in O/R Designer.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. La classe di entità dispone di proprietà che vengono mappate alle colonne nella tabella Contact (Person).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Rimuovere l'entità predefinita dal modello di integrazione applicativa dei dati

Il progetto **modello di integrazione applicativa dei dati** aggiunge un'entità predefinita denominata Entity1 al modello. Rimuovere questa entità. Successivamente, si aggiungerà una nuova entità. A partire da un modello vuoto è possibile ridurre il numero di passaggi necessari per completare la procedura dettagliata.

1. In **Esplora soluzioni**espandere il nodo **BdcModel1** , quindi aprire il file *BdcModel1. bdcm* .

2. Il file modello di integrazione applicativa dei dati verrà aperto nella finestra di progettazione dell'integrazione applicativa

3. Nella finestra di progettazione aprire il menu di scelta rapida per **Entity1**, quindi scegliere **Elimina**.

4. In **Esplora soluzioni**aprire il menu di scelta rapida per *Entity1. vb* (in Visual Basic) o *Entity1.cs* ( C#in), quindi scegliere **Elimina**.

5. Aprire il menu di scelta rapida per *Entity1Service. vb* (in Visual Basic ) o Entity1Service.cs C#(in), quindi scegliere **Elimina**.

## <a name="add-an-entity-to-the-model"></a>Aggiungere un'entità al modello

Aggiungere un'entità al modello. È possibile aggiungere entità dalla **casella degli strumenti** di Visual Studio nella finestra di progettazione dell'integrazione applicativa dei dati.

1. Scegliere **Visualizza** > **Casella degli strumenti** sulla barra dei menu.

2. Nella scheda **BusinessDataConnectivity** della **casella degli strumenti**aggiungere un' **entità** nella finestra di progettazione dell'integrazione applicativa dei dati.

     La nuova entità verrà visualizzata nella finestra di progettazione. Visual Studio aggiunge al progetto un file denominato *EntityService. vb* (in Visual Basic) o *EntityService.cs* (in C#).

3. Nella barra dei menu scegliere **visualizza** > **Proprietà** > **finestra**.

4. Nella finestra **Proprietà** impostare il valore della proprietà **nome** su **Contact**.

5. Nella finestra di progettazione aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi**, quindi scegliere **identificatore**.

     Viene visualizzato un nuovo identificatore nell'entità.

6. Nella finestra **Proprietà** modificare il nome dell'identificatore in **ContactID**.

7. Nell'elenco **nome tipo** scegliere **System. Int32**.

## <a name="add-a-specific-finder-method"></a>Aggiungere un metodo Finder specifico

Per consentire al servizio BDC di visualizzare un contatto specifico, è necessario aggiungere un metodo di ricerca specifico. Il servizio BDC chiama il metodo Finder specifico quando un utente sceglie un elemento in un elenco e quindi sceglie il pulsante **Visualizza elemento** sulla barra multifunzione.

Aggiungere un metodo di ricerca specifico all'entità Contact usando la finestra **Dettagli metodo di integrazione applicativa dei dati** . Per restituire un'entità specifica, aggiungere il codice al metodo.

1. Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità **Contact** .

2. Sulla barra dei menu scegliere **visualizza** > **altre finestre** > **Dettagli metodo di integrazione applicativa dei dati**.

     Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati.

3. Nell'elenco **Aggiungi metodo** scegliere **Crea metodo di ricerca specifico**.

     Visual Studio aggiunge al modello gli elementi seguenti. Questi elementi vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati** .

    - Metodo denominato ReadItem.

    - Parametro di input per il metodo.

    - Parametro restituito per il metodo.

    - Descrittore di tipo per ogni parametro.

    - Istanza di metodo per il metodo.

4. Nella finestra **Dettagli metodo di integrazione applicativa dei dati** aprire l'elenco visualizzato per il descrittore del tipo di **contatto** , quindi scegliere **modifica**.

     Viene aperta la finestra di **esplorazione di integrazione applicativa** dei dati e viene fornita una visualizzazione gerarchica del modello.

5. Nella finestra **Proprietà** aprire l'elenco accanto alla proprietà **typeName** , scegliere la scheda **progetto corrente** , quindi scegliere la proprietà **contatto** .

6. In **Esplora integrazione applicativa**dei dati aprire il menu di scelta rapida del **contatto**, quindi scegliere **Aggiungi descrittore tipo**.

     Un nuovo descrittore di tipo denominato **TypeDescriptor1** viene visualizzato in **Esplora integrazione applicativa**dei dati.

7. Nella finestra **Proprietà** impostare il valore della proprietà **Name** su **ContactID**.

8. Aprire l'elenco accanto alla proprietà **typeName** , quindi scegliere **Int32**.

9. Aprire l'elenco accanto alla proprietà **Identifier** , quindi scegliere **ContactID**.

10. Ripetere il passaggio 6 per creare un descrittore di tipo per ognuno dei campi seguenti.

    |Name|Nome tipo|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Phone|System.String|
    |emailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Nell'entità **Contact** della finestra di progettazione dell'integrazione applicativa dei dati, aprire il metodo **ReadItem** .

     Il file di codice del servizio di contatto verrà aperto nell'editor di codice.

12. Nella classe `ContactService` sostituire il metodo `ReadItem` con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

    - Recupera un record dalla tabella Contact del database AdventureWorks.

    - Restituisce un'entità Contact per il servizio di integrazione applicativa dei dati.

    > [!NOTE]
    > Sostituire il valore del campo `ServerName` con il nome del server.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Aggiungere un metodo Finder

Per consentire al servizio BDC di visualizzare i contatti in un elenco, è necessario aggiungere un metodo Finder. Aggiungere un metodo Finder all'entità Contact usando la finestra **Dettagli metodo di integrazione applicativa dei dati** . Per restituire una raccolta di entità al servizio BDC, aggiungere il codice al metodo.

1. Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità **Contact** .

2. Nella finestra **Dettagli metodo di integrazione applicativa dei dati** , comprimere il nodo **ReadItem** .

3. Nell'elenco **Aggiungi un metodo** sotto il metodo **Read** list scegliere **Crea metodo Finder**.

     Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.

4. Nella finestra di progettazione dell'integrazione applicativa dei dati, nell'entità **Contact** aprire il metodo **Leggimi** .

     Il file di codice per il servizio di Contact verrà aperto nell'editor di codice.

5. Nella classe `ContactService` sostituire il metodo `ReadList` con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

   - Recupera i dati dalla tabella Contacts del database AdventureWorks.

   - Restituisce un elenco di entità di contatto per il servizio di integrazione applicativa dei dati.

     > [!NOTE]
     > Sostituire il valore del campo `ServerName` con il nome del server.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Testare il progetto

Quando si esegue il progetto, viene aperto il sito di SharePoint e Visual Studio aggiunge il modello al servizio di integrazione applicativa dei dati. Creazione di un elenco esterno in SharePoint che fa riferimento all'entità Contact. I dati dei contatti nel database AdventureWorks vengono visualizzati nell'elenco.

> [!NOTE]
> Per poter eseguire il debug della soluzione, potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Premere **F5**.

     Verrà aperto il sito di SharePoint.

2. Scegliere il comando **altre opzioni** dal menu **Azioni sito** .

3. Nella pagina **Crea** scegliere il modello **elenco esterno** , quindi scegliere il pulsante **Crea** .

4. Denominare i **contatti**elenco personalizzato.

5. Scegliere il pulsante Sfoglia accanto al campo **tipo di contenuto esterno** .

6. Nella finestra di dialogo **Selezione tipo di contenuto esterno** scegliere l'elemento **AdventureWorksContacts. BdcModel1. Contact** , quindi scegliere il pulsante **Crea** .

     In SharePoint viene creato un elenco esterno con i contatti del database di esempio AdventureWorks.

7. Per testare il metodo Finder specifico, scegliere un contatto nell'elenco.

8. Sulla barra multifunzione scegliere la scheda **elementi** , quindi scegliere il comando **Visualizza elemento** .

     I dettagli del contatto selezionato verranno visualizzati in un form.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulla progettazione di modelli per il servizio BDC in SharePoint, vedere gli argomenti seguenti:

- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md).
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Vedere anche

[Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
[creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
[Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
[integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
