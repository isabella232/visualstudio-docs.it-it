---
title: 'Procedura dettagliata: Creazione di una Web Part per SharePoint tramite una finestra di progettazione | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 146a1722f240895e0f508b0474df72f6f5f84ece
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870912"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Procedura dettagliata: Creare una web part per SharePoint tramite una finestra di progettazione

Se si creano web part per un sito di SharePoint, gli utenti possono modificare direttamente il contenuto, l'aspetto e comportamento delle pagine in tale sito utilizzando un browser. Questa procedura dettagliata viene illustrato come creare visivamente una web part tramite SharePoint **Web Part visiva** modello di progetto in Visual Studio.

Consente di visualizzare la web part che verrà creata una visualizzazione del calendario mensile e una casella di controllo per ogni elenco di calendario sul sito. Gli utenti possono specificare quali elenchi di calendario includere nella visualizzazione del calendario mensile selezionando le caselle di controllo.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di una web part tramite il **Web Part visiva** modello di progetto.
- Progettazione della web part utilizzando la finestra di progettazione di Visual Web Developer in Visual Studio.
- Aggiunta di codice per gestire gli eventi dei controlli nella web part.
- Test della web part in SharePoint.

    > [!NOTE]
    > Computer in uso potrebbe mostrare nomi diversi o posizioni di alcuni elementi dell'interfaccia utente per Visual Studio nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

## <a name="create-a-web-part-project"></a>Creare un progetto web part

In primo luogo, creare un progetto web part tramite il **Web Part visiva** modello di progetto.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando il **Esegui come amministratore** opzione.

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nel **nuovo progetto** in presenza di una finestra di dialogo **Visual c#** oppure **Visual Basic**, espandere **Office/SharePoint**e quindi scegliere il  **Soluzioni SharePoint** categoria.

4. Nell'elenco dei modelli, scegliere il **SharePoint 2013 - Web Part visiva** modello, quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata. Usando questa procedura guidata, è possibile specificare il sito che verrà usato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

5. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** keychains le **Distribuisci come soluzione farm** pulsante di opzione.

6. Scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

## <a name="designing-the-web-part"></a>Progettazione della web part

Progettare la web part aggiungendo i controlli dal **casella degli strumenti** nell'area della finestra di progettazione di Visual Web Developer.

1. Nella finestra di progettazione in Visual Web Developer, scegliere il **progettazione** pressione di tab per passare alla visualizzazione progettazione.

2. Scegliere **Visualizza** > **Casella degli strumenti** sulla barra dei menu.

3. Nel **Standard** nodo delle **della casella degli strumenti**, scegliere il **CheckBoxList** controllare e quindi effettuare una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **CheckBoxList** controllare, scegliere **copia**, aprire il menu di scelta rapida per la prima riga nella finestra di progettazione e quindi scegliere **Incolla**.

    - Trascinare il **CheckBoxList** controllare dalle **della casella degli strumenti**e connettere il controllo alla prima riga nella finestra di progettazione.

4. Ripetere il passaggio precedente, ma spostare un pulsante alla riga successiva della finestra di progettazione.

5. Nella finestra di progettazione, scegliere il **Button1** pulsante.

6. Nella barra dei menu, scegliere **View** > **finestra proprietà**.

     Il **proprietà** verrà visualizzata la finestra.

7. Nel **testo** proprietà del pulsante, immettere **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestione degli eventi dei controlli nella web part

Aggiungere il codice che consente all'utente di includere calendari alla visualizzazione del calendario master.

1. Eseguire una delle procedure seguenti:

   - Nella finestra di progettazione, fare doppio clic il **Update** pulsante.

   - Nel **delle proprietà** finestra per il **Update** pulsante la **eventi** pulsante. Nel **fare clic su** proprietà, immettere **Button1_Click**e quindi premere INVIO.

     Il file di codice del controllo utente verrà aperto nell'Editor di codice e `Button1_Click` gestore eventi viene visualizzato. In un secondo momento, si aggiungerà codice a questo gestore eventi.

2. Aggiungere le istruzioni seguenti all'inizio del file di codice del controllo utente.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Aggiungere la seguente riga di codice per il `VisualWebPart1` classe. Questo codice dichiara un controllo di visualizzazione del calendario mensile.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Sostituire il `Page_Load` metodo di `VisualWebPart1` classe con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

   - Aggiunge una visualizzazione del calendario mensile al controllo utente.

   - Aggiunge una casella di controllo per ogni elenco di calendario sul sito.

   - Specifica un modello per ogni tipo di elemento che viene visualizzato nella visualizzazione del calendario.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Sostituire il `Button1_Click` metodo di `VisualWebPart1` classe con il codice seguente. Questo codice aggiunge elementi da ogni calendario selezionato alla visualizzazione del calendario master.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testare la web part

Quando si esegue il progetto, viene aperto il sito di SharePoint. La web part viene automaticamente aggiunto alla raccolta Web Part in SharePoint. Per questo progetto di test, si eseguirà le attività seguenti:

- Aggiungere un evento a ognuno dei due elenchi di calendario distinti.
- Aggiungere la web part a una pagina web part.
- Specificare gli elenchi da includere nella visualizzazione del calendario mensile.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Per aggiungere eventi agli elenchi di calendario sul sito

1. In Visual Studio, scegliere il **F5** chiave.

     Viene aperto il sito di SharePoint e il [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barra Avvio veloce viene visualizzata nella pagina.

2. Nella barra Avvio veloce, sotto **sono elencati**, scegliere il **calendario** collegamento.

     Il **calendario** verrà visualizzata la pagina.

     Se è alcun collegamento di calendario non visualizzato sulla barra Avvio veloce, scegliere il **contenuti del sito** collegamento. Se non viene visualizzata la pagina di contenuto del sito una **calendario** di elemento, crearne uno.

3. Nella pagina del calendario, scegliere un giorno e quindi scegliere il **Add** collegamento nel giorno selezionato per aggiungere un evento.

4. Nel **Title** casella, immettere **evento nel calendario predefinito**e quindi scegliere il **Salva** pulsante.

5. Scegliere il **contenuti del sito** collegamento e quindi scegliere il **Aggiungi un'app** riquadro.

6. Nel **Create** pagina, scegliere il **calendario** digitare, denominare il calendario e quindi scegliere il **Create** pulsante.

7. Aggiungere un evento per il nuovo calendario, denominare l'evento **evento nel calendario personalizzato**, quindi scegliere il **salvare** pulsante.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Per aggiungere la web part a una pagina web part

1. Nel **contenuti del sito** pagina, aprire il **pagine del sito** cartella.

2. Sulla barra multifunzione scegliere la **file** scheda, aprire il **nuovo documento** dal menu e quindi scegliere il **Web Part Page** comando.

3. Nel **nuova pagina Web Part** pagina, denominare la pagina **SampleWebPartPage. aspx**e quindi scegliere il **Create** pulsante.

     Viene visualizzata la pagina web part.

4. Nella parte superiore della pagina web part, scegliere il **inserire** scheda e quindi scegliere il **Web Part** pulsante.

5. Scegliere il **Custom** cartella, scegliere il **VisualWebPart1** web part e quindi scegliere il **Add** pulsante.

     La web part viene visualizzata nella pagina. Nella web part sono visualizzati i controlli seguenti:

    - Una visualizzazione del calendario mensile.

    - Un' **Update** pulsante.

    - Oggetto **calendario** casella di controllo.

    - Oggetto **calendario personalizzato** casella di controllo.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Per specificare gli elenchi da includere nella visualizzazione del calendario mensile

Nella web part, specificare i calendari che si desidera includere nella visualizzazione del calendario mensile e quindi scegliere il **Update** pulsante.

Gli eventi da tutti i calendari specificati vengono visualizzati nella visualizzazione del calendario mensile.

## <a name="see-also"></a>Vedere anche

[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
