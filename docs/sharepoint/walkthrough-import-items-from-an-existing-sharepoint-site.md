---
title: 'Procedura dettagliata: Importare gli elementi da un sito di SharePoint esistente | Microsoft Docs'
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
ms.openlocfilehash: a2727f0f3a5f2b46c5110a33e63b102f9d26bdaf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446617"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procedura dettagliata: Importare gli elementi da un sito di SharePoint esistente
  Questa procedura dettagliata illustra come importare elementi da un sito di SharePoint esistente in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Personalizzazione di un sito di SharePoint tramite l'aggiunta di una colonna di sito personalizzato (noto anche come un *campo*.

- Esportazione di un sito di SharePoint in un file con estensione wsp.

- L'importazione del file con estensione wsp nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint usando il progetto di importazione di wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Personalizzare un sito di SharePoint
 Per questo esempio, si crea e personalizzare un sito secondario di SharePoint mediante l'aggiunta una nuova colonna di sito e la creazione di un altro sito secondario per un uso successivo. Verrà successivamente, esportare il primo sito secondario in un file con estensione wsp e quindi importare la colonna di sito personalizzato nel secondo sito secondario usando il progetto di importazione di wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Per creare e personalizzare un sito di SharePoint

1. Aprire un sito di SharePoint usando un Web browser, ad esempio http://<em>il nome del sistema</em>/SitePages/Home.aspx.

2. Creare un sito secondario dal sito di SharePoint principale, aprire il **Azioni sito** dal menu e scegliendo **nuovo sito**.

3. Del sito **Create** finestra di dialogo scegliere la **Blank Site** tipo.

4. Nel **titolo** casella, immettere **Test 1 delle colonne del sito**; nella **nome URL** immettere **columntest1**; lasciare le altre impostazioni in base all'impostazione predefinita valori; e quindi scegliere il **Create** pulsante.

5. Dopo aver creato il sito, passare nel browser tornare al sito principale, http://<em>il nome del sistema</em>/SitePages/Home.aspx.

6. Anche in questo caso, creare un sito secondario vuoto dal sito di SharePoint principale aprendo il **Azioni sito** menu, scegliendo **nuovo sito**e quindi scegliendo il **Blank Site** tipo.

7. Nel **titolo** casella, immettere **Test 2 delle colonne del sito**; nella **nome URL** immettere **columntest2**; lasciare le altre impostazioni in base all'impostazione predefinita valori; e quindi scegliere il **Create** pulsante.

8. Tornare al primo sito secondario, http://<em>NomeSistema</em>/columntest1/default.aspx.

9. Nel **Azioni sito** menu, scegliere **Impostazioni sito** per visualizzare la pagina Impostazioni sito.

10. Nel **Galleries** keychains le **le colonne del sito** collegamento.

11. Nella parte superiore del **raccolta di colonne del sito** pagina, scegliere il **crea** pulsante.

12. Nel **nome della colonna** casella, immettere **Test colonna**, mantenere gli altri valori predefiniti e quindi scegliere il **OK** pulsante.

13. Il **Test colonna** colonna vengono visualizzate sotto le colonne personalizzate sull'intestazione nella raccolta di colonne del sito.

## <a name="exporting-the-sharepoint-site"></a>Esportare il sito di SharePoint
 Successivamente, ottenere un file di installazione (con estensione wsp) di SharePoint che contiene gli elementi di SharePoint e gli elementi che si desidera importare le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint. Se si dispone già di un file con estensione wsp, quindi è necessario crearne uno da un sito di SharePoint esistente. Per questo esempio, si esporterà il sito di SharePoint predefinito in un file con estensione wsp.

> [!IMPORTANT]
> Se si riceve un errore di runtime eseguendo la procedura seguente, è necessario eseguire la procedura in un sistema che ha accesso al sito di SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Per esportare un sito di SharePoint esistente

1. Nel sito di SharePoint, scegliere **Impostazioni sito** nel **Azioni sito** scheda per visualizzare la pagina Impostazioni sito.

2. Nel **Azioni sito** sezione della pagina Impostazioni sito, scegliere il **sito Salva come modello** collegamento.

3. Nel **nome File** immettere **ExampleSite**e nel **nome modello** immettere **esempio sito**.

4. Per questo esempio, lasciare il **includere contenuto** casella di controllo.

     Se si seleziona questa casella, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Salva tutti gli elenchi e raccolte documenti e il relativo contenuto nel file con estensione wsp. Anche se ciò è utile in alcuni casi, non è necessario per questo esempio.

5. Quando l'operazione viene completata, scegliere il **raccolta soluzioni** collegamento per visualizzare il file con estensione wsp.

     Per visualizzare la pagina Raccolta soluzioni più avanti, aprire il **Azioni sito** menu, scegliere **le impostazioni del sito**, scegliere il **passa a impostazioni del sito di livello superiore** clic sul collegamento nella  **Amministrazione raccolta siti** sezione e quindi scegliere il **soluzioni** clic sul collegamento nella **raccolte** sezione.

6. Nella raccolta di soluzioni, scegliere il **ExampleSite** collegamento.

7. Nel **del File da scaricare** finestra di dialogo scegliere la **salvare** consente di salvare il file nel sistema locale, per impostazione predefinita, nella cartella download.

## <a name="import-the-wsp-file"></a>Importare il file con estensione wsp
 Dopo aver creato un *wsp* file che contiene un elemento che si desidera riutilizzare (la colonna di Test di colonna di sito personalizzato), importare il *wsp* file per accedervi.

### <a name="to-import-a-wsp-file"></a>Per importare un file con estensione wsp

1. Nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto**finestra di dialogo. Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual Basic, nella barra dei menu, scegliere **File** > **nuovo progetto**.

2. Espandere la **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.

3. Scegliere il **Importa pacchetto di soluzione SharePoint 2010** modello nel **modelli** riquadro, lasciare il nome del progetto WspImportProject1 e quindi scegliere il **OK** pulsante.

    Il **Personalizzazione guidata SharePoint** viene visualizzata.

4. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creato in precedenza. Si aggiungerà l'oggetto personalizzato nuovo campo, http://<em>il nome del sistema</em>/columntest2, a tale sito secondario.

5. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** sezione, lasciare la selezione **Distribuisci come soluzione creata mediante sandbox**.

6. Nel **specificare l'origine del nuovo progetto** pagina, selezionare il percorso nel sistema in cui è stato salvato il *wsp* file in precedenza e quindi scegliere il **Avanti** pulsante.

   > [!NOTE]
   > Se si sceglie la **Finish** pulsante in questa pagina, tutti gli elementi disponibile nel *con estensione wsp* file verrà importato.

7. Nel **selezionare gli elementi da importare** casella, deselezionare tutte le caselle di controllo nell'elenco, ad eccezione di **Test Column**e quindi scegliere il **fine** pulsante.

    Poiché l'elenco contiene molti elementi, è possibile scegliere il **Ctrl**+**oggetto** le chiavi per scegliere tutti gli elementi nell'elenco, premere il tasto barra spaziatrice per cancellare tutte le caselle di controllo e quindi selezionare solo il controllo accanto alla casella di **Test colonna** elemento.

    Una volta completato l'operazione di importazione, un nuovo progetto denominato **WspImportProject1** viene creato che contiene una cartella denominata **campi**. In questa cartella è la colonna di sito personalizzato **Test Column** e il relativo file di definizione *Elements*.

## <a name="deploy-the-project"></a>Distribuire il progetto
 Distribuire infine **WspImportProject1** a SharePoint secondo il sito secondario creato in precedenza per visualizzare la colonna di sito personalizzati.

### <a name="to-deploy-the-project"></a>Per distribuire il progetto

1. Nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], scegliere il **F5** per distribuire ed eseguire il *wsp* importare il progetto.

2. Nel sito di SharePoint, aprire il **Azioni sito** menu, quindi scegliere **Impostazioni sito** per visualizzare la pagina Impostazioni sito.

3. Nel **Galleries** keychains le **le colonne del sito** collegamento.

4. Scorrere verso il basso il **colonne personalizzate** sezione.

     Si noti che la colonna di sito personalizzato che è stato importato dal primo sito di SharePoint viene visualizzato nell'elenco.

## <a name="see-also"></a>Vedere anche
- [Importare gli elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
