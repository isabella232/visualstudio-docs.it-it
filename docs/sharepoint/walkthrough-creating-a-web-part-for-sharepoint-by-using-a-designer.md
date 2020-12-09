---
title: Creazione di una Web part per SharePoint tramite la finestra di progettazione
description: In questa procedura dettagliata, creare una Web part visivamente utilizzando il modello di progetto Web part visiva di SharePoint in Visual Studio.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc214e98b2ec0ed6feb31c9aaa6e8170b3ddd2c8
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913984"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Procedura dettagliata: creare una Web part per SharePoint tramite una finestra di progettazione

Se si creano web part per un sito di SharePoint, gli utenti possono modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine del sito usando un browser. In questa procedura dettagliata viene illustrato come creare visivamente una Web part tramite il modello di progetto **Web part visiva** di SharePoint in Visual Studio.

La Web part che verrà creata consente di visualizzare una visualizzazione del calendario mensile e una casella di controllo per ogni elenco di calendari sul sito. Gli utenti possono specificare gli elenchi di calendario da includere nella visualizzazione mensile del calendario selezionando le caselle di controllo.

Vengono illustrate le attività seguenti:

- Creazione di una Web part tramite il modello di progetto **Web part visiva** .
- Progettazione della web part tramite la finestra di progettazione di Visual Web Developer in Visual Studio.
- Aggiunta di codice per gestire gli eventi dei controlli nella web part.
- Test della web part in SharePoint.

    > [!NOTE]
    > Nelle istruzioni seguenti potrebbe essere visualizzato un nome o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

## <a name="create-a-web-part-project"></a>Creazione di un progetto Web part

Per prima cosa, creare un progetto Web part utilizzando il modello di progetto **Web part visiva** .

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Per iniziare, usare l'opzione **Esegui come amministratore** .

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nella finestra di dialogo **nuovo progetto** , in **Visual C#** o **Visual Basic**, espandere **Office/SharePoint**, quindi scegliere la categoria **soluzioni SharePoint** .

4. Nell'elenco dei modelli scegliere il modello **SharePoint 2013-Visual Web part** , quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** . Utilizzando questa procedura guidata, è possibile specificare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

5. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm** .

6. Scegliere il pulsante **fine** per accettare il sito di SharePoint locale predefinito.

## <a name="designing-the-web-part"></a>Progettazione della web part

Progettare la Web part aggiungendo i controlli dalla **casella degli strumenti** alla superficie di Visual Web Developer Designer.

1. Nella finestra di progettazione di Visual Web Developer scegliere la scheda **progettazione** per passare alla visualizzazione progettazione.

2. Sulla barra dei menu scegliere **Visualizza**  >  **casella degli strumenti**.

3. Nel nodo **standard** della **casella degli strumenti** scegliere il controllo **CheckBoxList** , quindi eseguire una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il controllo **CheckBoxList** , scegliere **copia**, aprire il menu di scelta rapida per la prima riga nella finestra di progettazione, quindi scegliere **Incolla**.

    - Trascinare il controllo **CheckBoxList** dalla **casella degli strumenti** e connettere il controllo alla prima riga nella finestra di progettazione.

4. Ripetere il passaggio precedente, ma spostare un pulsante nella riga successiva della finestra di progettazione.

5. Nella finestra di progettazione scegliere il pulsante **Button1** .

6. Nella barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

     Si aprirà la finestra **Proprietà**.

7. Nella proprietà **Text** del pulsante immettere **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestione degli eventi dei controlli nella web part

Aggiungere il codice che consente all'utente di aggiungere calendari alla visualizzazione del calendario master.

1. Eseguire una delle procedure seguenti:

   - Nella finestra di progettazione fare doppio clic sul pulsante **Aggiorna** .

   - Nella finestra **Proprietà** per il pulsante **Aggiorna** scegliere il pulsante **eventi** . Nella proprietà **fare clic** immettere **Button1_Click**, quindi premere il tasto INVIO.

     Il file di codice del controllo utente viene aperto nell'editor di codice e `Button1_Click` viene visualizzato il gestore eventi. Successivamente, si aggiungerà codice a questo gestore eventi.

2. Aggiungere le seguenti istruzioni all'inizio del file di codice del controllo utente.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Aggiungere la riga di codice seguente alla `VisualWebPart1` classe. Questo codice dichiara un controllo di visualizzazione calendario mensile.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Sostituire il `Page_Load` metodo della `VisualWebPart1` classe con il codice seguente. Il codice esegue queste operazioni:

   - Aggiunge una visualizzazione del calendario mensile al controllo utente.

   - Aggiunge una casella di controllo per ogni elenco di calendari sul sito.

   - Specifica un modello per ogni tipo di elemento visualizzato nella visualizzazione del calendario.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Sostituire il `Button1_Click` metodo della `VisualWebPart1` classe con il codice seguente. Questo codice aggiunge elementi da ogni calendario selezionato alla visualizzazione del calendario master.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testare la Web part

Quando si esegue il progetto, viene aperto il sito di SharePoint. La Web part viene aggiunta automaticamente alla raccolta di Web part in SharePoint. Per testare questo progetto, verranno eseguite le attività seguenti:

- Aggiungere un evento a ognuno dei due elenchi di calendario distinti.
- Aggiungere la Web part a una pagina Web part.
- Consente di specificare gli elenchi da includere nella visualizzazione del calendario mensile.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Per aggiungere eventi agli elenchi di calendario nel sito

1. In Visual Studio premere il tasto **F5** .

     Viene aperto il sito di SharePoint e la [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barra avvio veloce viene visualizzata nella pagina.

2. Nella barra avvio veloce, in **elenchi**, scegliere il collegamento al **Calendario** .

     Verrà visualizzata la pagina **Calendar** .

     Se nella barra avvio veloce non viene visualizzato alcun collegamento al calendario, scegliere il collegamento **contenuto del sito** . Se la pagina contenuto del sito non mostra un elemento del **Calendario** , crearne uno.

3. Nella pagina calendario scegliere un giorno, quindi scegliere il collegamento **Aggiungi** nel giorno selezionato per aggiungere un evento.

4. Nella casella **titolo** immettere **Event nel calendario predefinito**, quindi scegliere il pulsante **Salva** .

5. Scegliere il collegamento **contenuto del sito** e quindi scegliere il riquadro **Aggiungi un'app** .

6. Nella pagina **Crea** scegliere il tipo di **Calendario** , assegnare un nome al calendario, quindi scegliere il pulsante **Crea** .

7. Aggiungere un evento al nuovo calendario, denominare l'evento dell'evento **nel calendario personalizzato**, quindi scegliere il pulsante **Salva** .

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Per aggiungere la Web part a una pagina Web part

1. Nella pagina **contenuto del sito** aprire la cartella **pagine** del sito.

2. Sulla barra multifunzione scegliere la scheda **file** , aprire il menu **nuovo documento** , quindi scegliere il comando **pagina Web part** .

3. Nella pagina **nuova pagina Web part** assegnare un nome alla pagina **SampleWebPartPage. aspx**, quindi scegliere il pulsante **Crea** .

     Verrà visualizzata la pagina Web part.

4. Nella parte superiore della pagina Web part scegliere la scheda **Inserisci** , quindi fare clic sul pulsante **Web part** .

5. Scegliere la cartella **personalizzata** , scegliere la Web part **VisualWebPart1** , quindi fare clic sul pulsante **Aggiungi** .

     La Web part viene visualizzata nella pagina. Nella web part vengono visualizzati i controlli seguenti:

    - Una visualizzazione del calendario mensile.

    - Pulsante **Aggiorna** .

    - Casella di controllo **Calendario** .

    - Casella di controllo **calendario personalizzato** .

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Per specificare gli elenchi da includere nella visualizzazione del calendario mensile

Nella web part specificare i calendari che si desidera includere nella visualizzazione del calendario mensile, quindi scegliere il pulsante **Aggiorna** .

Gli eventi di tutti i calendari specificati vengono visualizzati nella visualizzazione del calendario mensile.

## <a name="see-also"></a>Vedi anche

[Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Procedura: creare una Web part](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 di SharePoint [Procedura dettagliata: creare una Web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
