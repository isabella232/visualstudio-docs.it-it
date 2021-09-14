---
title: Creare una web part per SharePoint progettazione
description: In questa procedura dettagliata creare una web part visivamente usando il modello di progetto SharePoint visual web part in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2a00ea5c8720c02b9dbdbd8a6fad7fa7657efeb5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711398"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Procedura dettagliata: Creare una web part per SharePoint usando una finestra di progettazione

Se si creano web part per un sito SharePoint, gli utenti possono modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine in tale sito usando un browser. Questa procedura dettagliata illustra come creare una web part in modo visivo usando il modello di progetto SharePoint **visual web part** in Visual Studio.

La web part che verrà creata visualizza una visualizzazione calendario mensile e una casella di controllo per ogni elenco di calendari nel sito. Gli utenti possono specificare gli elenchi di calendari da includere nella visualizzazione calendario mensile selezionando le caselle di controllo.

Vengono illustrate le attività seguenti:

- Creazione di una web part tramite il **modello di progetto Web part** visiva.
- Progettazione della web part tramite la finestra di progettazione di Visual Web Developer in Visual Studio.
- Aggiunta di codice per gestire gli eventi dei controlli nella web part.
- Test della web part in SharePoint.

    > [!NOTE]
    > Il computer potrebbe visualizzare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente per Visual Studio nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

## <a name="create-a-web-part-project"></a>Creare un progetto web part

Creare prima di tutto un progetto web part usando il **modello di progetto Web part** visiva.

1. Iniziare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando **l'opzione Esegui come** amministratore.

2. Nella barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.
::: moniker range="=vs-2017"

3. Nella finestra **di dialogo Nuovo Project,** in **Visual C#** o **Visual Basic** espandere **Office/SharePoint** e quindi scegliere la categoria SharePoint **Soluzioni.**

4. Nell'elenco dei modelli scegliere il **modello SharePoint 2013 - Web part** visiva e quindi scegliere **OK.**

     Verrà **visualizzata SharePoint personalizzazione** guidata. Tramite questa procedura guidata è possibile specificare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.
::: moniker-end
::: moniker range=">=vs-2019"
3. Nella finestra **di dialogo Create a New Project** selezionare SharePoint Empty *Project** per la versione specifica di SharePoint installata. Ad esempio, se è stata SharePoint 2019, selezionare il modello SharePoint **2019 - Vuoto Project 2019.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. Nella casella **Nome** immettere **TestProject1** e quindi scegliere **il pulsante** Crea.

::: moniker-end
5. Nella sezione **Qual è il livello di attendibilità** SharePoint soluzione? scegliere il pulsante di opzione Distribuisci come **soluzione** farm.

6. Scegliere il **pulsante** Fine per accettare il sito locale SharePoint predefinito.

## <a name="designing-the-web-part"></a>Progettazione della web part

Progettare la web part aggiungendo controlli dalla casella **degli** strumenti all'area della finestra di progettazione di Visual Web Developer.

1. Nella finestra di progettazione di Visual Web Developer scegliere la **scheda Progettazione** per passare alla visualizzazione Progettazione.

2. Sulla barra dei menu scegliere **Visualizza casella degli**  >  **strumenti**.

3. Nel nodo **Standard** della Casella **degli strumenti** scegliere il **controllo CheckBoxList** e quindi eseguire una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **controllo CheckBoxList,** scegliere Copia **,** aprire il menu di scelta rapida per la prima riga nella finestra di progettazione e quindi scegliere **Incolla**.

    - Trascinare **il controllo CheckBoxList** dalla **Casella degli strumenti** e connettere il controllo alla prima riga della finestra di progettazione.

4. Ripetere il passaggio precedente, ma spostare un oggetto Button alla riga successiva della finestra di progettazione.

5. Nella finestra di progettazione scegliere il **pulsante Button1.**

6. Sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

     Si aprirà la finestra **Proprietà**.

7. Nella proprietà **Text** del pulsante immettere **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestione degli eventi dei controlli nella web part

Aggiungere il codice che consente all'utente di aggiungere calendari alla visualizzazione calendario master.

1. Eseguire una delle procedure seguenti:

   - Nella finestra di progettazione fare doppio clic sul **pulsante** Aggiorna.

   - Nella finestra **Proprietà** per il **pulsante Aggiorna** scegliere il **pulsante** Eventi. Nella proprietà **Clic** immettere **Button1_Click** e quindi premere INVIO.

     Il file di codice del controllo utente viene aperto nell'editor di codice e viene visualizzato `Button1_Click` il gestore eventi. Successivamente, si aggiungerà il codice a questo gestore eventi.

2. Aggiungere le istruzioni seguenti all'inizio del file di codice del controllo utente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. Aggiungere la riga di codice seguente alla `VisualWebPart1` classe . Questo codice dichiara un controllo visualizzazione calendario mensile.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. Sostituire il `Page_Load` metodo della classe con il codice `VisualWebPart1` seguente. Il codice esegue queste operazioni:

   - Aggiunge una visualizzazione calendario mensile al controllo utente.

   - Aggiunge una casella di controllo per ogni elenco di calendari nel sito.

   - Specifica un modello per ogni tipo di elemento visualizzato nella visualizzazione calendario.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. Sostituire il `Button1_Click` metodo della classe con il codice `VisualWebPart1` seguente. Questo codice aggiunge gli elementi di ogni calendario selezionato alla visualizzazione calendario master.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>Testare la web part

Quando si esegue il progetto, viene aperto SharePoint sito web. La web part viene aggiunta automaticamente alla raccolta web part in SharePoint. Per testare questo progetto, eseguire le attività seguenti:

- Aggiungere un evento a ognuno dei due elenchi di calendari separati.
- Aggiungere la web part a una pagina web part.
- Specificare gli elenchi da includere nella visualizzazione calendario mensile.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Per aggiungere eventi agli elenchi di calendari nel sito

1. In Visual Studio premere **F5.**

     Verrà SharePoint il sito e la barra Avvio veloce [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] visualizzata nella pagina.

2. Nella barra Avvio veloce, in **Elenchi,** scegliere il **collegamento** Calendario.

     Verrà **visualizzata la** pagina Calendario.

     Se non viene visualizzato alcun collegamento calendario sulla barra Avvio veloce, scegliere il **collegamento Contenuto del** sito. Se nella pagina Contenuto del sito non viene visualizzato un **elemento Calendario,** crearne uno.

3. Nella pagina Calendario scegliere un giorno e quindi scegliere il **collegamento** Aggiungi nel giorno selezionato per aggiungere un evento.

4. Nella casella **Titolo** immettere **Evento nel calendario predefinito** e quindi scegliere il **pulsante** Salva.

5. Scegliere il **collegamento Contenuto del** sito e quindi scegliere il riquadro Aggiungi **un'app.**

6. Nella pagina **Crea** scegliere il tipo **di calendario,** assegnare un nome al calendario e quindi scegliere **il pulsante** Crea.

7. Aggiungere un evento al nuovo calendario, assegnare all'evento il nome Evento nel **calendario** personalizzato e quindi scegliere il **pulsante** Salva.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Per aggiungere la web part a una pagina web part

1. Nella pagina **Contenuto del** sito aprire la cartella **Pagine del** sito.

2. Sulla barra multifunzione scegliere la **scheda File,** aprire il menu **Nuovo** documento e quindi scegliere il **comando Pagina web** part.

3. Nella pagina **Nuova pagina web part** assegnare alla pagina il nome **SampleWebPartPage.aspx** e quindi scegliere **il pulsante** Crea.

     Verrà visualizzata la pagina web part.

4. Nell'area superiore della pagina web part scegliere la **scheda** Inserisci e quindi scegliere **il pulsante Web part.**

5. Scegliere la **cartella** Personalizzata, scegliere la web part **VisualWebPart1** e quindi scegliere **il pulsante** Aggiungi.

     La web part viene visualizzata nella pagina. Nella web part vengono visualizzati i controlli seguenti:

    - Visualizzazione calendario mensile.

    - Pulsante  Aggiorna.

    - Casella **di controllo** Calendario.

    - Casella **di controllo Calendario** personalizzato.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Per specificare gli elenchi da includere nella visualizzazione calendario mensile

Nella web part specificare i calendari da includere nella visualizzazione calendario mensile e quindi scegliere il **pulsante** Aggiorna.

Gli eventi di tutti i calendari specificati vengono visualizzati nella visualizzazione calendario mensile.

## <a name="see-also"></a>Vedi anche

[Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Procedura: Creare una SharePoint web part](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
