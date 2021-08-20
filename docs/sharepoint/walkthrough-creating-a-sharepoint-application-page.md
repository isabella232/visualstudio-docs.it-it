---
title: 'Procedura dettagliata: Creazione di un SharePoint di applicazione | Microsoft Docs'
description: In questa procedura dettagliata creare una pagina dell'applicazione (un modulo specializzato di una pagina ASP.NET) e quindi eseguirne il debug usando un sito SharePoint locale.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7aa99f3d9fb333d9d7b1177eae39a5f5800cb4e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148857"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Procedura dettagliata: Creare una pagina SharePoint'applicazione

Una pagina dell'applicazione è una forma specializzata di ASP.NET pagina. Le pagine dell'applicazione contengono contenuto unito a una SharePoint master. Per altre informazioni, vedere [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Questa procedura dettagliata illustra come creare una pagina dell'applicazione e quindi eseguirne il debug usando un sito SharePoint locale. Questa pagina mostra tutti gli elementi creati o modificati da ogni utente in tutti i siti server farm.

Vengono illustrate le attività seguenti:

- Creazione di un SharePoint progetto.
- Aggiunta di una pagina dell'applicazione SharePoint progetto.
- Aggiunta ASP.NET controlli alla pagina dell'applicazione.
- Aggiunta di codice dietro i controlli ASP.NET controllo.
- Test della pagina dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Windows e SharePoint.

## <a name="create-a-sharepoint-project"></a>Creare un SharePoint progetto

Creare prima di tutto un **oggetto Empty SharePoint Project**. Successivamente si aggiungerà un **elemento Pagina applicazione** a questo progetto.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Aprire la **finestra di dialogo** Nuovo Project, espandere il nodo **Office/SharePoint** nel linguaggio che si vuole usare e quindi scegliere il nodo SharePoint **Soluzioni.**

3. Nel riquadro **Visual Studio modelli installati** scegliere il modello SharePoint **2010 - Vuoto Project** modello. Assegnare al **progetto il nome MySharePointProject** e quindi scegliere **OK.**

     Verrà **SharePoint personalizzazione guidata.** Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

4. Scegliere il **pulsante di opzione** Distribuisci come  soluzione farm e quindi scegliere il pulsante Fine per accettare il sito locale SharePoint predefinito.

## <a name="create-an-application-page"></a>Creare una pagina dell'applicazione

Per creare una pagina dell'applicazione, aggiungere un **elemento Pagina** applicazione al progetto.

1. In **Esplora soluzioni** scegliere il **progetto MySharePointProject.**

2. Sulla barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** scegliere il modello Pagina applicazione **(Solo soluzione** farm).

4. Assegnare alla **pagina il nome SearchItems** e quindi scegliere **il pulsante** Aggiungi.

     La finestra di progettazione di Visual Web Developer visualizza la pagina dell'applicazione nella **visualizzazione Origine** in cui è possibile visualizzare gli elementi HTML della pagina. Nella finestra di progettazione viene visualizzato il markup per diversi <xref:System.Web.UI.WebControls.Content> controlli. Ogni controllo viene mappato a <xref:System.Web.UI.WebControls.ContentPlaceHolder> un controllo definito nella pagina master dell'applicazione predefinita.

## <a name="design-the-layout-of-the-application-page"></a>Progettare il layout della pagina dell'applicazione

L'elemento Pagina applicazione consente di usare una finestra di progettazione per aggiungere ASP.NET controlli alla pagina dell'applicazione. Questa finestra di progettazione è la stessa finestra di progettazione usata in Visual Web Developer. Aggiungere un'etichetta, un elenco di pulsanti  di opzione e una tabella alla visualizzazione Origine della finestra di progettazione e quindi impostare le proprietà esattamente come si farebbe quando si progetta una pagina ASP.NET standard.

1. Sulla barra dei menu scegliere **Visualizza casella degli**  >  **strumenti**.

2. Nel nodo Standard della Casella **degli strumenti** seguire questa procedura:

    - Aprire il menu di scelta rapida per l'elemento **Etichetta,** scegliere **Copia,** aprire il menu di scelta rapida per la riga sotto il controllo contenuto **PlaceHolderMain** nella finestra di progettazione e quindi scegliere **Incolla**.

    - Trascinare **l'elemento Label** dalla **Casella** degli strumenti nel corpo del controllo contenuto **PlaceHolderMain.**

3. Ripetere il passaggio precedente per aggiungere un **elemento DropDownList** e un **elemento Table** al controllo contenuto **PlaceHolderMain.**

4. Nella finestra di progettazione modificare il valore `Text` dell'attributo del controllo etichetta in Mostra tutti gli **elementi**.

5. Nella finestra di progettazione sostituire `<asp:DropDownList>` l'elemento con il codice XML seguente.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Gestire gli eventi dei controlli nella pagina

Gestire i controlli in una pagina dell'applicazione esattamente come qualsiasi ASP.NET pagina. In questa procedura si gestirà `SelectedIndexChanged` l'evento dell'elenco a discesa.

1. Scegliere **Codice** dal menu **Visualizza**.

     Il file di codice della pagina dell'applicazione viene aperto nell'editor di codice.

2. Aggiungi alla classe `SearchItems` il metodo seguente. Questo codice gestisce <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> l'evento di chiamando un metodo che verrà creato più avanti in questa procedura <xref:System.Web.UI.WebControls.DropDownList> dettagliata.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet5":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet5":::

3. Aggiungere le istruzioni seguenti all'inizio del file di codice della pagina dell'applicazione.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet1":::

4. Aggiungi alla classe `SearchItems` il metodo seguente. Questo metodo scorre tutti i siti nel server farm e cerca gli elementi creati o modificati dall'utente corrente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet2":::

5. Aggiungi alla classe `SearchItems` il metodo seguente. Questo metodo visualizza gli elementi creati o modificati dall'utente corrente nella tabella.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet3":::

## <a name="test-the-application-page"></a>Testare la pagina dell'applicazione

Quando si esegue il progetto, viene aperto SharePoint sito web e viene visualizzata la pagina dell'applicazione.

1. In **Esplora soluzioni** aprire il menu di scelta rapida per la pagina dell'applicazione e quindi scegliere **Imposta come elemento di avvio**.

2. Premere **F5**.

     Verrà SharePoint sito di lavoro.

3. Nella pagina dell'applicazione scegliere **l'opzione Modificato dall'utente** corrente.

     La pagina dell'applicazione viene aggiornata e visualizza tutti gli elementi modificati in tutti i siti server farm.

4. Nella pagina dell'applicazione scegliere **Creato dall'utente corrente** nell'elenco.

     La pagina dell'applicazione viene aggiornata e visualizza tutti gli elementi creati in tutti i siti server farm.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulle SharePoint dell'applicazione, vedere [Creare pagine dell'applicazione SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Per altre informazioni su come progettare il contenuto SharePoint pagina tramite Visual Web Designer, vedere gli argomenti seguenti:

- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creare controlli riutilizzabili per web part o pagine dell'applicazione.](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

## <a name="see-also"></a>Vedi anche

[Procedura: Creare una pagina dell'applicazione](../sharepoint/how-to-create-an-application-page.md) 
 [Tipo di _layouts applicazione](/previous-versions/office/aa979604(v=office.14))
