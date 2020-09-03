---
title: Importa pagina master personalizzata & pagina del sito con l'immagine
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 311124b2e0b81e70c4c2a7b40754207e6c66b749
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015685"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Procedura dettagliata: importazione di una pagina master personalizzata e di una pagina del sito con un'immagine
  In questa procedura dettagliata viene illustrato come importare una pagina master personalizzata di SharePoint e una pagina del sito con un'immagine in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.

 In questa procedura dettagliata viene illustrato come eseguire le attività seguenti:

- Creazione di una pagina master personalizzata e di una pagina del sito utilizzando un'immagine in SharePoint Designer.

- Esportare una pagina master personalizzata, un'immagine e una pagina del sito in un file di soluzione SharePoint (con*estensione wsp*).

- Importare e distribuire il file con *estensione wsp* in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint utilizzando il progetto Importa pacchetto di soluzione SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Creazione di elementi in SharePoint Designer
 In questo esempio viene illustrato come creare tre elementi in SharePoint Designer per l'esportazione: una pagina master personalizzata, una pagina del sito che fa riferimento alla pagina master personalizzata e un file di immagine da visualizzare nella pagina del sito. L'immagine viene aggiunta alla cartella/images/in SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Per creare una pagina master personalizzata in SharePoint Designer

1. In SharePoint Designer, nel riquadro di spostamento, scegliere l'oggetto sito **pagine master** .

2. Sulla barra multifunzione **pagine master** scegliere **pagina master vuota**.

3. Scegliere la nuova pagina master, quindi nella barra multifunzione **pagine master** scegliere **modifica file**.

4. Nella parte inferiore di SharePoint Designer scegliere la scheda **codice** .

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

6. Salvare la pagina, scegliere la scheda **pagine master** e rinominare la pagina master come **mybasic1. master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Aggiungere un'immagine al database del contenuto in SharePoint Designer
 A questo punto è possibile aggiungere un'immagine da visualizzare nella pagina del sito. L'immagine viene distribuita nel database del contenuto di SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Per aggiungere un'immagine al database del contenuto in SharePoint Designer

1. Nel riquadro di spostamento scegliere l'oggetto sito **tutti i file** , quindi nella visualizzazione albero scegliere la cartella **Immagini** .

2. Sulla barra multifunzione **tutti i file** scegliere **Importa file**, scegliere un file di propria scelta, quindi scegliere il pulsante **OK** . In questo esempio il file è denominato **myimg1.png**.

     Facoltativamente, è possibile creare una sottocartella per organizzare le immagini.

3. Chiudere la finestra di dialogo **Importa** .

## <a name="create-a-site-page"></a>Creare una pagina del sito
 Questa pagina di base del sito usa la pagina master personalizzata e visualizza l'immagine aggiunta nel passaggio precedente.

#### <a name="to-create-a-site-page"></a>Per creare una pagina del sito

1. Nel riquadro di spostamento scegliere l'oggetto **pagine del sito** .

2. Sulla barra multifunzione **pagine** scegliere il pulsante **pagina** , scegliere il tipo di pagina **aspx** , quindi denominare il nuovo file **MyContentPage1. aspx**.

     Facoltativamente, è possibile creare una sottocartella per organizzare le pagine del sito.

3. Nell'elenco pagine sito scegliere **MyContentPage1. aspx** per aprire la relativa pagina delle proprietà e quindi, nella parte inferiore della pagina, scegliere il collegamento **modifica file** .

     Se viene visualizzato un messaggio che indica che questa pagina non contiene aree modificabili in modalità provvisoria e chiede se si vuole aprire questa pagina in modalità avanzata, scegliere il pulsante **Sì** .

4. Nella parte inferiore della pagina scegliere il pulsante **codice** .

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
 Esportare gli elementi da SharePoint in un file di soluzione SharePoint (con*estensione wsp*).

#### <a name="to-export-items-from-sharepoint-designer"></a>Per esportare elementi da SharePoint Designer

1. In SharePoint Designer, nel riquadro di spostamento, scegliere l'oggetto **sito del team** , quindi sulla barra multifunzione **sito** scegliere **Salva come modello**.

2. Nella finestra di dialogo **Salva come modello** immettere un nome file e un nome modello, selezionare la casella di controllo **Includi contenuto** , quindi scegliere il pulsante **OK** .

     In questo modo, il contenuto del sito viene salvato nel file con *estensione wsp* .

3. Dopo l'esportazione della soluzione, scegliere il collegamento **raccolta soluzioni** per visualizzare l'elenco dei file di soluzione disponibili.

4. Aprire il menu di scelta rapida per il nuovo file con *estensione wsp* , quindi scegliere **Salva destinazione con nome** per salvarlo nel sistema.

## <a name="import-the-items-into-visual-studio"></a>Importare gli elementi in Visual Studio
 Importare il file con estensione *WSP* in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Una volta importato il contenuto, è possibile personalizzarlo, aggiungere altri elementi e quindi distribuirlo.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Per importare elementi dal file con estensione wsp in Visual Studio

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di **pacchetto della soluzione di importazione SharePoint 2010** .

2. Nella pagina **selezionare gli elementi da importare** , in **modulo** nella colonna **tipo** , selezionare le caselle di controllo solo per i file nella tabella seguente per l'importazione.

   | File Name | Descrizione |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Pagina master personalizzata. |
   | images_ | Il file di immagine nel file system di SharePoint. |
   | SitePages_ | Pagina del sito. |

3. Scegliere il pulsante **fine** per importare gli elementi selezionati.

4. In **Esplora soluzioni**scegliere il \_ nodo catalogsmasterpage \_ e impostare il valore della proprietà di **risoluzione dei conflitti di distribuzione** su **Automatic**.

    Ciò consente di garantire che eventuali conflitti di distribuzione vengano risolti automaticamente.

5. Se la nuova pagina master ha lo stesso nome di una pagina esistente, assicurarsi che la pagina esistente non sia contrassegnata come pagina master predefinita o come pagina master personalizzata in SharePoint Designer.

    Se una pagina master esistente è contrassegnata come pagina master predefinita o pagina master personalizzata, si otterrà un errore di distribuzione che indica che non è possibile eliminare la pagina master. Per evitare questo problema, effettuare le seguenti operazioni:

   - Se la pagina master esistente è impostata come pagina master predefinita, impostare temporaneamente un'altra pagina master come pagina master predefinita. Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master come pagina master predefinita.

   - Se la pagina master esistente è impostata come pagina master personalizzata, impostare temporaneamente un'altra pagina master come pagina master personalizzata. Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master come pagina master personalizzata.

6. Sulla barra dei menu scegliere **Compila**  >  **distribuzione soluzione**.

7. Aprire il sito di SharePoint per visualizzare gli elementi distribuiti.

   Un metodo alternativo per importare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuire file in SharePoint consiste nell'aggiungere i file ai moduli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Procedura: importare una pagina master o un tema](../sharepoint/how-to-import-a-master-page-or-theme.md) e [utilizzare i moduli per includere i file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vedere anche
- [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
