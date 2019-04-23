---
title: "Procedura dettagliata: Importare una pagina Master personalizzata e pagina del sito con un'immagine | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 3d99b76e1ca9c67c0cd29bd435759b529d97b348
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665994"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Procedura dettagliata: Importare una pagina master personalizzata e una pagina del sito con un'immagine
  Questa procedura dettagliata illustra come importare una pagina master personalizzata di SharePoint e una pagina del sito con un'immagine in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.

 Questa procedura dettagliata viene illustrato come eseguire le attività seguenti:

- Creare una pagina master personalizzata e una pagina del sito usando un'immagine in SharePoint Designer.

- Esportare una pagina master personalizzata, immagine e pagina del sito in una soluzione di SharePoint (*wsp*) file.

- Importare e distribuire il *wsp* del file in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto di SharePoint usando il progetto Importa pacchetto di soluzione SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Sono necessari i componenti seguenti per completare questa procedura dettagliata:

-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

-   Visual Studio.

-   SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Creare gli elementi in SharePoint Designer
 In questo esempio viene illustrato come creare tre elementi in SharePoint Designer per l'esportazione: una pagina master personalizzata, una pagina del sito che fa riferimento la pagina master personalizzata e un file di immagine da visualizzare nella pagina del sito. L'immagine venga aggiunta alla cartella /images/ in SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Per creare una pagina master personalizzata in SharePoint Designer

1.  In SharePoint Designer, nel riquadro di spostamento, scegliere il **pagine Master** oggetto sito.

2.  Nel **pagine Master** sulla barra multifunzione **pagina Master vuota**.

3.  Scegliere la nuova pagina master e quindi scegliere il **pagine Master** sulla barra multifunzione **modifica il File**.

4.  Nella parte inferiore della finestra di progettazione di SharePoint, scegliere il **codice** scheda.

5.  Sostituire il markup esistente con il markup seguente.

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

6.  Salvare la pagina, scegliere il **pagine Master** scheda e rinominare la pagina master come **mybasic1**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Aggiungere un'immagine per il database del contenuto in SharePoint Designer
 A questo punto è possibile aggiungere un'immagine da visualizzare nella pagina del sito. L'immagine viene distribuita al database del contenuto di SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Per aggiungere un'immagine per il database del contenuto in SharePoint Designer

1.  Nel riquadro di spostamento, scegliere il **tutti i file** oggetto del sito e quindi, nella visualizzazione albero, scegliere il **immagini** cartella.

2.  Nel **tutti i file** sulla barra multifunzione **dei file di importazione**, scegliere un file di propria scelta e quindi scegliere il **OK** pulsante. In questo esempio, il file è denominato **myimg1**.

     Facoltativamente, è possibile creare una sottocartella per organizzare le immagini.

3.  Chiudi il **importazione** nella finestra di dialogo.

## <a name="create-a-site-page"></a>Creare una pagina del sito
 Questa pagina del sito di base viene utilizzata la pagina master personalizzata e visualizza l'immagine che è stato aggiunto nel passaggio precedente.

#### <a name="to-create-a-site-page"></a>Per creare una pagina del sito

1.  Nel riquadro di spostamento, scegliere il **pagine del sito** oggetto.

2.  Nel **pagine** sulla barra multifunzione, scegliere il **pagina** pulsante la **ASPX** tipo di pagina e quindi denominare il nuovo file **MyContentPage1**.

     Facoltativamente, è possibile creare una sottocartella per organizzare le pagine del sito.

3.  Nell'elenco di pagine del sito, scegliere **Mycontentpage1** per aprire la pagina delle proprietà e quindi nella parte inferiore della pagina, scegliere il **Edit file** collegamento.

     Se un messaggio visualizzato indica che questa pagina non contiene tutte le aree che possono essere modificate in modalità provvisoria e chiede se si desidera aprire questa pagina in modalità avanzata, scegliere il **Sì** pulsante.

4.  Nella parte inferiore della pagina, scegliere il **codice** pulsante.

5.  Sostituire il markup esistente con il markup seguente.

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

6.  Salvare la pagina sito aggiornato.

## <a name="export-the-items-from-sharepoint"></a>Esportare gli elementi da SharePoint
 Esportare gli elementi da SharePoint a una soluzione SharePoint (*wsp*) file.

#### <a name="to-export-items-from-sharepoint-designer"></a>Per esportare gli elementi da SharePoint Designer

1.  In SharePoint Designer, nel riquadro di spostamento, scegliere il **sito del Team** oggetti e quindi scegliere il **sito** sulla barra multifunzione **Salva come modello**.

2.  Nel **Salva come modello** finestra di dialogo immettere un nome di file e nome del modello, selezionare la **contenuto da includere** casella di controllo e quindi scegliere il **OK** pulsante.

     Ciò consente di salvare il contenuto del sito nel *wsp* file.

3.  Dopo che la soluzione consente di esportare, scegliere il **raccolta soluzioni** link per visualizzare l'elenco dei file di soluzione disponibile.

4.  Aprire il menu di scelta rapida per il nuovo *wsp* del file e quindi scegliere **Salva come** salvarlo nel sistema.

## <a name="import-the-items-into-visual-studio"></a>Importare gli elementi in Visual Studio
 Importa i *wsp* del file in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Dopo aver importato il contenuto, è possibile personalizzarlo, aggiungere altri elementi e quindi distribuirlo.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Per importare gli elementi dal file con estensione wsp in Visual Studio

1. Nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un **Importa pacchetto di soluzione SharePoint 2010** progetto.

2. Nel **selezionare gli elementi da importare** nella pagina **modulo** nel **tipo** colonna, selezionare le caselle di controllo solo per i file nella tabella seguente per l'importazione.

   | Nome file | Descrizione |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | La pagina master personalizzata. |
   | images_ | Il file di immagine nel file system di SharePoint. |
   | SitePages_ | Pagina del sito. |

3. Scegliere il **fine** pulsante per importare gli elementi selezionati.

4. In **Esplora soluzioni**, scegliere il \_catalogsmasterpage\_ nodo e impostare il valore della relativa **risoluzione conflitti di distribuzione** proprietà **automatica** .

    Ciò garantisce che eventuali conflitti di distribuzione vengono risolti automaticamente.

5. Se la nuova pagina master ha lo stesso nome di una pagina esistente, assicurarsi che la pagina esistente non è contrassegnata come pagina Master predefinita o una pagina Master personalizzata in SharePoint Designer.

    Se una pagina master esistente viene contrassegnata come pagina Master predefinita o pagina Master personalizzata, si otterrà un errore di distribuzione che indica che la pagina master non può essere eliminata. Per evitare questo problema, eseguire questa operazione:

   -   Se la pagina master esistente è impostata come pagina Master predefinita, impostare temporaneamente un'altra pagina master come pagina Master predefinita. Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master come pagina Master predefinita.

   -   Se la pagina master esistente è impostata come pagina Master personalizzata, impostare temporaneamente un'altra pagina master come pagina Master personalizzata. Dopo aver distribuito i file in SharePoint, impostare la nuova pagina master come pagina Master personalizzata.

6. Nella barra dei menu, scegliere **compilare** > **Distribuisci soluzione**.

7. Aprire il sito di SharePoint per visualizzare gli elementi distribuiti.

   Un modo alternativo per importare i file in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuirle in SharePoint consiste nell'aggiungere i file nei moduli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Come si fa: Importare una pagina master o un tema](../sharepoint/how-to-import-a-master-page-or-theme.md) e [usare i moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vedere anche
- [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
