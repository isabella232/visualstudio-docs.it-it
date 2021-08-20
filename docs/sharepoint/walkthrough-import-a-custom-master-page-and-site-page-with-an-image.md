---
title: Importare una pagina master personalizzata & pagina del sito con immagine
description: In questa procedura dettagliata importare una SharePoint master personalizzata e una pagina del sito con un'immagine in un Visual Studio SharePoint progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7694c80d47e7dd16c603eaedd0527ac4ec4d9031
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135832"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Procedura dettagliata: Importare una pagina master personalizzata e una pagina del sito con un'immagine
  Questa procedura dettagliata illustra come importare una SharePoint master personalizzata e una pagina del sito con un'immagine in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint progetto.

 Questa procedura dettagliata illustra come eseguire le attività seguenti:

- Creare una pagina master personalizzata e una pagina del sito usando un'immagine in SharePoint Designer.

- Esportare una pagina master, un'immagine e una pagina del sito personalizzati in un file SharePoint soluzione (*con estensione wsp).*

- Importare e distribuire il file *con estensione wsp* in un progetto SharePoint usando il progetto Importa SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto della soluzione.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- SharePoint Progettazione 2010.

## <a name="create-items-in-sharepoint-designer"></a>Creare elementi in SharePoint Designer
 Questo esempio illustra come creare tre elementi in SharePoint Designer per l'esportazione: una pagina master personalizzata, una pagina del sito che fa riferimento alla pagina master personalizzata e un file di immagine da visualizzare nella pagina del sito. L'immagine viene aggiunta alla cartella /images/ in SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Per creare una pagina master personalizzata in SharePoint Designer

1. In SharePoint Designer scegliere l'oggetto sito **Pagine master** nel riquadro di spostamento.

2. Nella barra **multifunzione Pagine master** scegliere Pagina master **vuota**.

3. Scegliere la nuova pagina master e quindi nella barra **multifunzione Pagine master** scegliere Modifica **file**.

4. Nella parte inferiore di SharePoint Designer scegliere la **scheda** Codice.

5. Sostituire il markup esistente con il markup seguente.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6. Salvare la pagina, scegliere la **scheda Pagine master** e rinominare la pagina master come **mybasic1.master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Aggiungere un'immagine al database del contenuto in SharePoint Designer
 È ora possibile aggiungere un'immagine da visualizzare nella pagina del sito. L'immagine viene distribuita nel database SharePoint contenuto.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Per aggiungere un'immagine al database del contenuto in SharePoint Designer

1. Nel riquadro di spostamento scegliere **l'oggetto** sito Tutti i file e quindi nella visualizzazione albero scegliere la **cartella images.**

2. Nella barra **multifunzione Tutti i** file scegliere Importa **file,** scegliere un file di propria scelta e quindi fare clic sul **pulsante OK.** In questo esempio il file è denominato **myimg1.png**.

     Facoltativamente, è possibile creare una sottocartella per organizzare le immagini.

3. Chiudere la **finestra di** dialogo Importa.

## <a name="create-a-site-page"></a>Creare una pagina del sito
 Questa pagina del sito di base usa la pagina master personalizzata e visualizza l'immagine aggiunta nel passaggio precedente.

#### <a name="to-create-a-site-page"></a>Per creare una pagina del sito

1. Nel riquadro di spostamento scegliere **l'oggetto Pagine del** sito.

2. Nella barra **multifunzione Pagine** scegliere il **pulsante Pagina,** scegliere il tipo di pagina **ASPX** e quindi assegnare al nuovo file il nome **mycontentpage1.aspx**.

     Facoltativamente, è possibile creare una sottocartella per organizzare le pagine del sito.

3. Nell'elenco delle pagine del sito scegliere **MyContentPage1.aspx** per aprire la pagina delle proprietà e quindi nella parte inferiore della pagina scegliere il **collegamento Modifica file.**

     Se viene visualizzato un messaggio che indica che questa pagina non contiene aree modificabili in modalità provvisoria e chiede se si vuole aprire la pagina in modalità avanzata, scegliere il **pulsante** Sì.

4. Nella parte inferiore della pagina scegliere il **pulsante** Codice.

5. Sostituire il markup esistente con il markup seguente.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6. Salvare la pagina del sito aggiornata.

## <a name="export-the-items-from-sharepoint"></a>Esportare gli elementi da SharePoint
 Esportare gli elementi SharePoint in un file SharePoint soluzione *(con estensione wsp).*

#### <a name="to-export-items-from-sharepoint-designer"></a>Per esportare elementi da SharePoint Designer

1. In SharePoint Designer scegliere l'oggetto Sito del **team** nel riquadro di  spostamento e quindi scegliere Salva come modello sulla barra multifunzione **Sito.**

2. Nella finestra **di dialogo Salva** come modello immettere un  nome di file e un nome di modello, selezionare la casella di controllo Includi contenuto e quindi scegliere **OK.**

     Il contenuto del sito viene salvato nel file *con estensione wsp.*

3. Dopo aver esportato la soluzione, scegliere il **collegamento Raccolta** soluzioni per visualizzare l'elenco dei file di soluzione disponibili.

4. Aprire il menu di scelta rapida per il nuovo file *con estensione wsp* e quindi scegliere Salva destinazione **con nome** per salvarlo nel sistema.

## <a name="import-the-items-into-visual-studio"></a>Importare gli elementi in Visual Studio
 Importare il file *con estensione wsp* in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Dopo aver importato il contenuto, è possibile personalizzarlo, aggiungere altri elementi e quindi distribuirlo.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Per importare elementi dal file con estensione wsp in Visual Studio

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto Importa SharePoint pacchetto della soluzione **2010.**

2. Nella pagina **Selezione elementi da importare** in **Modulo** nella colonna **Tipo** selezionare le caselle di controllo solo per i file nella tabella seguente per l'importazione.

   | File Name | Descrizione |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Pagina master personalizzata. |
   | images_ | File di immagine nel SharePoint file system. |
   | SitePages_ | Pagina del sito. |

3. Scegliere il **pulsante** Fine per importare gli elementi selezionati.

4. In **Esplora soluzioni** scegliere il nodo catalogsmasterpage e impostare il valore della relativa proprietà Risoluzione conflitti \_ di distribuzione su \_ **Automatico.** 

    Ciò consente di assicurarsi che eventuali conflitti di distribuzione siano risolti automaticamente.

5. Se la nuova pagina master ha lo stesso nome di una pagina esistente, assicurarsi che la pagina esistente non sia contrassegnata come pagina master predefinita o pagina master personalizzata in progettazione SharePoint progettazione.

    Se una pagina master esistente è contrassegnata come Pagina master predefinita o Pagina master personalizzata, verrà visualizzato un errore di distribuzione che indica che la pagina master non può essere eliminata. Per evitare questo problema, eseguire questa operazione:

   - Se la pagina master esistente è impostata come Pagina master predefinita, impostare temporaneamente un'altra pagina master come Pagina master predefinita. Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master su Pagina master predefinita.

   - Se la pagina master esistente è impostata come Pagina master personalizzata, impostare temporaneamente un'altra pagina master come Pagina master personalizzata. Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master su Pagina master personalizzata.

6. Sulla barra dei menu scegliere **Compila**  >  **distribuisci soluzione**.

7. Aprire il SharePoint per visualizzare gli elementi distribuiti.

   Un modo alternativo per importare i file in e distribuirli in SharePoint consiste nell'aggiungere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i file nei moduli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Procedura: Importare una pagina master o un tema e](../sharepoint/how-to-import-a-master-page-or-theme.md) Usare moduli per includere file nella [soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vedi anche
- [Importazione di elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
