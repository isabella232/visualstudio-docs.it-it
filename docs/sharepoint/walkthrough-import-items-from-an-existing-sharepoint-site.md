---
title: 'Procedura dettagliata: importare elementi da un sito di SharePoint esistente | Microsoft Docs'
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
ms.openlocfilehash: 46bc2ceacfde599a70b4e84bba134c4a4d5f9757
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017112"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procedura dettagliata: importare elementi da un sito di SharePoint esistente
  In questa procedura dettagliata viene illustrato come importare elementi da un sito di SharePoint esistente in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Personalizzazione di un sito di SharePoint mediante l'aggiunta di una colonna del sito personalizzata, nota anche come *campo*.

- Esportazione di un sito di SharePoint in un file con estensione wsp.

- Importazione del file con estensione wsp in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint tramite il progetto di importazione con estensione wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Personalizzare un sito di SharePoint
 Per questo esempio, verrà creato e personalizzato un sito secondario di SharePoint aggiungendovi una nuova colonna del sito e creando un altro sito secondario da usare in un secondo momento. Successivamente, si esporterà il primo sito secondario in un file con estensione wsp e quindi si importerà la colonna del sito personalizzata nel secondo sito secondario usando il progetto di importazione con estensione wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Per creare e personalizzare un sito di SharePoint

1. Aprire un sito di SharePoint utilizzando un Web browser, ad esempio http://<em>System Name</em>/SitePages/Home.aspx.

2. Creare un sito secondario dal sito principale di SharePoint aprendo il menu **Azioni sito** e quindi scegliendo **nuovo sito**.

3. Nella finestra di dialogo **Crea** del sito scegliere il tipo di **sito vuoto** .

4. Nella casella **titolo** immettere **Site Column test 1**; nella casella **nome URL** immettere **columntest1**; lasciare invariati i valori predefiniti delle altre impostazioni. quindi scegliere il pulsante **Crea** .

5. Dopo aver creato il sito, passare al sito principale del browser, http://<em>System Name</em>/SitePages/Home.aspx.

6. Anche in questo caso, creare un sito secondario vuoto dal sito principale di SharePoint aprendo il menu **Azioni sito** , scegliendo **nuovo sito**e scegliendo il tipo di **sito vuoto** .

7. Nella casella **titolo** immettere **Site Column test 2**; nella casella **nome URL** immettere **columntest2**; lasciare invariati i valori predefiniti delle altre impostazioni. quindi scegliere il pulsante **Crea** .

8. Tornare al primo sito secondario, http://<em>SystemName</em>/columntest1/default.aspx.

9. Scegliere **Impostazioni sito** dal menu **Azioni sito** per visualizzare la pagina Impostazioni sito.

10. Nella sezione **raccolte** scegliere il collegamento **colonne sito** .

11. Nella parte superiore della pagina **raccolta colonne sito** scegliere il pulsante **Crea** .

12. Nella casella **nome colonna** immettere **colonna test**, Mantieni gli altri valori predefiniti, quindi scegliere il pulsante **OK** .

13. La colonna **test colonna** viene visualizzata sotto l'intestazione colonne personalizzate nella raccolta colonne sito.

## <a name="exporting-the-sharepoint-site"></a>Esportazione del sito di SharePoint
 Ottenere quindi un file di installazione di SharePoint (con estensione wsp) contenente gli elementi e gli elementi di SharePoint che si desidera importare nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint. Se non si dispone già di un file con estensione wsp, è necessario crearne uno da un sito di SharePoint esistente. Per questo esempio, si esporterà il sito di SharePoint predefinito in un file con estensione wsp.

> [!IMPORTANT]
> Se si riceve un errore di runtime eseguendo la procedura riportata di seguito, è necessario eseguire la procedura in un sistema con accesso al sito di SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Per esportare un sito di SharePoint esistente

1. Nel sito di SharePoint scegliere **Impostazioni sito** nella scheda **Azioni sito** per visualizzare la pagina Impostazioni sito.

2. Nella sezione **Azioni sito** della pagina Impostazioni sito scegliere il collegamento **Salva sito come modello** .

3. Nella casella **nome file** immettere **ExampleSite**e nella casella **nome modello** immettere **sito di esempio**.

4. Per questo esempio, lasciare deselezionata la casella di controllo **Includi contenuto** .

     Se si seleziona questa casella, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Salva tutti gli elenchi e le raccolte documenti e il relativo contenuto nel file con estensione wsp. Sebbene questo sia utile in alcune circostanze, non è necessario per questo esempio.

5. Al termine dell'operazione, scegliere il collegamento **raccolta soluzioni** per visualizzare il file con estensione wsp.

     Per visualizzare la pagina raccolta soluzioni in un secondo momento, aprire il menu **Azioni sito** , scegliere **Impostazioni sito**, scegliere il collegamento **Vai a Impostazioni sito di livello superiore** nella sezione **Amministrazione raccolta siti** , quindi scegliere il collegamento **soluzioni** nella sezione **raccolte** .

6. Nella raccolta soluzioni scegliere il collegamento **ExampleSite** .

7. Nella finestra di dialogo **download del file** scegliere il pulsante **Salva** per salvare il file nel sistema locale, per impostazione predefinita, nella cartella Downloads.

## <a name="import-the-wsp-file"></a>Importare il file con estensione wsp
 Ora che si dispone di un file con estensione *WSP* che contiene un elemento che si desidera riutilizzare (la colonna di test della colonna del sito personalizzata), importare il file con *estensione wsp* per accedervi.

### <a name="to-import-a-wsp-file"></a>Per importare un file con estensione wsp

1. Nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] barra dei menu di scegliere **file**  >  **nuovo**  >  **progetto** per visualizzare la finestra di dialogo **nuovo progetto** . Se l'IDE è configurato per usare Visual Basic impostazioni di sviluppo, sulla barra dei menu scegliere **file**  >  **nuovo progetto**.

2. Espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

3. Scegliere il modello **Importa pacchetto di soluzione SharePoint 2010** nel riquadro **modelli** , lasciare il nome del progetto come WspImportProject1, quindi scegliere il pulsante **OK** .

    Viene visualizzata la **personalizzazione guidata SharePoint** .

4. Nella pagina **specificare il sito e il livello di sicurezza per il debug** immettere il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creato in precedenza. Il nuovo elemento campo personalizzato,<em>denominato http://System</em>/columntest2, viene aggiunto al sito secondario.

5. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** , lasciare selezionata l'opzione **Distribuisci come soluzione creata mediante sandbox**.

6. Nella pagina **specificare l'origine del nuovo progetto** passare al percorso nel sistema in cui è stato salvato in precedenza il file con *estensione wsp* , quindi scegliere il pulsante **Avanti** .

   > [!NOTE]
   > Se si sceglie il pulsante **fine** in questa pagina, verranno importati tutti gli elementi disponibili nel file con estensione *WSP* .

7. Nella casella **selezionare gli elementi da importare** deselezionare tutte le caselle di controllo nell'elenco ad eccezione di **colonna test**, quindi scegliere il pulsante **fine** .

    Poiché l'elenco contiene molti elementi, è possibile scegliere i **Ctrl** + **A** tasti CTRL per scegliere tutti gli elementi dell'elenco, scegliere il tasto barra spaziatrice per deselezionare tutte le caselle di controllo, quindi selezionare solo la casella di controllo accanto all'elemento **colonna test** .

    Al termine dell'operazione di importazione, viene creato un nuovo progetto denominato **WspImportProject1** contenente una cartella denominata **Fields**. In questa cartella è la **colonna di test** colonna sito personalizzata e il relativo file di definizione *Elements.xml*.

## <a name="deploy-the-project"></a>Distribuire il progetto
 Infine, distribuire **WspImportProject1** nel secondo sito secondario di SharePoint creato in precedenza per visualizzare la colonna del sito personalizzata.

### <a name="to-deploy-the-project"></a>Per distribuire il progetto

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premere il tasto **F5** per distribuire ed eseguire il progetto di importazione con *estensione wsp* .

2. Nel sito di SharePoint aprire il menu **Azioni sito** , quindi scegliere **Impostazioni sito** per visualizzare la pagina Impostazioni sito.

3. Nella sezione **raccolte** scegliere il collegamento **colonne sito** .

4. Scorrere verso il basso fino alla sezione **colonne personalizzate** .

     Si noti che la colonna del sito personalizzata importata dal primo sito di SharePoint viene visualizzata nell'elenco.

## <a name="see-also"></a>Vedere anche
- [Importa elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
