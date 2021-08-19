---
title: 'Procedura dettagliata: Importare elementi da un sito SharePoint esistente | Microsoft Docs'
titleSuffix: ''
description: In questa procedura dettagliata importare elementi da un sito SharePoint esistente in un Visual Studio SharePoint progetto.
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
ms.openlocfilehash: 17f16b02749fe1431f1016334c96855ee505a0a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115356"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procedura dettagliata: Importare elementi da un sito SharePoint esistente
  Questa procedura dettagliata illustra come importare elementi da un sito SharePoint esistente in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint progetto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Personalizzazione di SharePoint sito web aggiungendo una colonna del sito personalizzata (nota anche come *campo*.

- Esportazione di un SharePoint in un file con estensione wsp.

- L'importazione del file con estensione wsp [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint usando il progetto Import con estensione wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Personalizzare un SharePoint di lavoro
 Per questo esempio si creerà e si personalizza un sito secondario SharePoint aggiungendo una nuova colonna del sito e creando un altro sito secondario da usare in un secondo momento. Successivamente, si esporterà il primo sito secondario in un file con estensione wsp e quindi si importerà la colonna del sito personalizzata nel secondo sito secondario usando il progetto Import con estensione wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Per creare e personalizzare un sito SharePoint sito

1. Aprire un sito SharePoint usando un Web browser, ad esempio http://<em>nome</em>di sistema /SitePages/Home.aspx.

2. Creare un sito secondario all'SharePoint sito principale aprendo il menu **Azioni** sito e scegliendo **Nuovo sito.**

3. Nella finestra di dialogo **Crea** del sito scegliere il **tipo Sito** vuoto.

4. Nella casella **Titolo** immettere **Site Column Test 1**. Nella casella **Nome URL** immettere **columntest1**; Lasciare i valori predefiniti per le altre impostazioni. e quindi scegliere **il pulsante** Crea.

5. Dopo aver creato il sito, tornare al sito principale nel browser http://<em>sistema</em>/SitePages/Home.aspx.

6. Anche in questo caso, creare un sito secondario vuoto all'interno del sito SharePoint principale aprendo il **menu** Azioni sito, scegliendo **Nuovo** sito e quindi scegliendo il **tipo Sito** vuoto.

7. Nella casella **Titolo** immettere **Site Column Test 2**. Nella casella **Nome URL** immettere **columntest2**; Lasciare i valori predefiniti per le altre impostazioni. e quindi scegliere **il pulsante** Crea.

8. Tornare al primo sito secondario, http://<em>NomeSistema</em>/columntest1/default.aspx.

9. Nel menu **Azioni sito** scegliere Impostazioni **sito** per visualizzare la pagina Impostazioni sito.

10. Nella sezione **Raccolte** scegliere il collegamento **Colonne del** sito.

11. Nella parte superiore della **pagina Raccolta colonne del** sito scegliere il **pulsante** Crea.

12. Nella casella **Nome colonna** immettere **Test colonna**, mantenere gli altri valori predefiniti e quindi scegliere il **pulsante OK.**

13. La **colonna Colonna** di test viene visualizzata sotto l'intestazione Colonne personalizzate nella Raccolta colonne del sito.

## <a name="exporting-the-sharepoint-site"></a>Esportazione del SharePoint sito
 Ottenere quindi un file SharePoint di installazione (con estensione wsp) che contiene gli elementi SharePoint e gli elementi da importare nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint progetto. Se non si dispone già di un file con estensione wsp, è necessario crearne uno da un sito SharePoint esistente. Per questo esempio, si esporterà il SharePoint predefinito in un file con estensione wsp.

> [!IMPORTANT]
> Se si riceve un errore di runtime durante l'esecuzione della procedura seguente, è necessario eseguire la procedura in un sistema che abbia accesso al SharePoint sito.

### <a name="to-export-an-existing-sharepoint-site"></a>Per esportare un sito SharePoint esistente

1. Nel sito SharePoint sito scegliere  Impostazioni sito nella  scheda Azioni sito per visualizzare la pagina Impostazioni sito.

2. Nella sezione **Azioni sito** della pagina Impostazioni sito scegliere il collegamento Salva **sito come** modello.

3. Nella casella **Nome file** immettere **ExampleSite** e nella casella **Nome modello** immettere Sito **di esempio**.

4. Per questo esempio, lasciare deselezionata **la casella** di controllo Includi contenuto .

     Se si seleziona questa casella, salva tutti gli elenchi e le raccolte documenti e il relativo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] contenuto nel file con estensione wsp. Sebbene ciò sia utile in alcune circostanze, non è necessario per questo esempio.

5. Al termine dell'operazione, scegliere il collegamento **alla raccolta di soluzioni** per visualizzare il file con estensione wsp.

     Per visualizzare la pagina della raccolta di soluzioni in un secondo momento, aprire il menu Azioni  sito, scegliere Impostazioni sito, scegliere il collegamento Vai **alle** impostazioni del sito di livello superiore nella sezione Amministrazione raccolta siti e quindi scegliere il collegamento Soluzioni nella sezione **Raccolte.**   

6. Nella raccolta di soluzioni scegliere il **collegamento ExampleSite.**

7. Nella finestra **di dialogo** Download  file scegliere il pulsante Salva per salvare il file nel sistema locale, per impostazione predefinita, nella cartella Download.

## <a name="import-the-wsp-file"></a>Importare il file con estensione wsp
 Ora che si dispone di un file con estensione *wsp* che contiene un elemento che si vuole riutilizzare (la colonna del sito personalizzata Colonna test), importare il file con estensione *wsp* per accedervi.

### <a name="to-import-a-wsp-file"></a>Per importare un file con estensione wsp

1. In scegliere Nuovo file sulla barra dei menu Project per visualizzare la finestra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di dialogo   >    >   **Project** nuova cartella. Se l'IDE è impostato per l'Visual Basic di sviluppo, sulla barra dei menu scegliere **Nuovo**  >  **file Project**.

2. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Scegliere il modello SharePoint 2010 Solution Package  (Importa pacchetto soluzione **2010)** nel riquadro Modelli, lasciare il nome del progetto WspImportProject1 e quindi scegliere **il pulsante OK.**

    Verrà **visualizzata SharePoint personalizzazione** guidata.

4. Nella pagina **Specificare il sito e il livello** di sicurezza per il debug immettere per il secondo sito secondario SharePoint creato in [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] precedenza. Si aggiungerà il nuovo elemento Campo personalizzato, http://<em>nome di sistema</em>/columntest2, a tale sito secondario.

5. Nella sezione **What is the trust level for this SharePoint solution?** (Qual è il livello di attendibilità per questa soluzione? ) lasciare selezionata l'opzione Deploy as a sandboxed solution (Distribuisci come soluzione **sandbox).**

6. Nella pagina **Specificare l'origine del** nuovo progetto passare al percorso nel sistema in cui è stato salvato il file con estensione *wsp* in precedenza e quindi scegliere **il pulsante** Avanti.

   > [!NOTE]
   > Se si sceglie il **pulsante** Fine in questa pagina, verranno importati tutti gli elementi disponibili nel file con estensione *wsp.*

7. Nella casella **Seleziona elementi da importare** deselezionare tutte le caselle di controllo dell'elenco, ad eccezione di **Colonna** test , quindi scegliere **il pulsante** Fine .

    Poiché l'elenco contiene molti elementi, è possibile premere **CTRL** A per scegliere tutti gli elementi nell'elenco, premere LA BARRA SPAZIATRICE per deselezionare tutte le caselle di controllo e quindi selezionare solo la casella di controllo accanto all'elemento Colonna di +  test. 

    Al termine dell'operazione di importazione, viene creato un nuovo progetto **denominato WspImportProject1** che contiene una cartella denominata **Campi**. In questa cartella è presente la colonna del sito personalizzata **Colonna test e** il relativo file di definizione *Elements.xml*.

## <a name="deploy-the-project"></a>Distribuire il progetto
 Infine, distribuire **WspImportProject1** nel secondo SharePoint sito secondario creato in precedenza per visualizzare la colonna del sito personalizzato.

### <a name="to-deploy-the-project"></a>Per distribuire il progetto

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premere **F5 per** distribuire ed eseguire il progetto di importazione con estensione *wsp.*

2. Nel sito SharePoint, aprire il menu **Azioni** sito e quindi scegliere Impostazioni sito **per** visualizzare la pagina Impostazioni sito.

3. Nella sezione **Raccolte** scegliere il collegamento **Colonne del** sito.

4. Scorrere verso il basso fino **alla sezione Colonne** personalizzate.

     Si noti che la colonna del sito personalizzato importata dal primo sito SharePoint viene visualizzata nell'elenco.

## <a name="see-also"></a>Vedi anche
- [Importare elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
