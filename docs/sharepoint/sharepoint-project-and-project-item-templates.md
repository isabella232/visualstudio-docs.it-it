---
title: SharePoint Project e Project modelli di elemento | Microsoft Docs
description: Esaminare le descrizioni dei modelli di SharePoint e degli elementi di progetto disponibili e come vengono usati.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2949bf27910f90cee2e109e64d0d6741439806fc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636835"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint di progetto e di elemento di progetto
  Le sezioni seguenti descrivono i modelli di SharePoint progetto e di elemento di progetto disponibili e il modo in cui vengono usati.

## <a name="project-and-project-item-templates-overview"></a>panoramica Project modelli di elemento di progetto e di progetto
 Quando si crea un nuovo progetto SharePoint in Visual Studio, un progetto SharePoint viene aggiunto alla soluzione insieme a tutti gli elementi di progetto richiesti dal tipo di progetto. Ad esempio, se si crea un progetto web part Silverlight, Visual Studio crea una soluzione che contiene un elemento di progetto Web part visiva e un elemento di progetto applicazione Silverlight insieme a tutti i file richiesti da tali elementi di progetto. Project modelli di elemento vengono usati per aggiungere elementi di progetto a un progetto SharePoint esistente, ad esempio l'aggiunta di un ricevitore di eventi, una colonna del sito o un elenco.

 Per informazioni sui SharePoint fondamentali, vedere SharePoint [di base.](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)) Gli utenti avanzati possono creare modelli di progetto e di elemento di progetto personalizzati. Per altre informazioni, vedere [Estendere il sistema SharePoint progetto](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modelli di progetto
 Di seguito è riportato un elenco di SharePoint di progetto. Per visualizzare i modelli di progetto SharePoint in Visual Studio, nella finestra di dialogo Nuovo **Project** espandere il nodo **SharePoint in** **Visual C#** o **Visual Basic** e quindi scegliere **2010.**

### <a name="sharepoint-2010-project"></a>SharePoint 2010
 Il contenuto di un *SharePoint 2010 Project* sono inclusi in ogni SharePoint di progetto. Un SharePoint 2010 Project contiene:

- Un file di progetto.

- Pagina delle proprietà del progetto.

- Cartella **Riferimenti** che elenca tutti i riferimenti all'assembly nel progetto.

- Cartella **Features** che contiene un file di configurazione con estensione *feature,* usato per distribuire le funzionalità SharePoint server.

- Cartella **Package** che contiene un file *Package.package,* usato per distribuire la soluzione in SharePoint.

- File key.snk (chiave con nome sicuro) usato per firmare l'assembly con un nome sicuro, per una sicurezza avanzata.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint web part Silverlight 2010
 SharePoint progetti web *part Silverlight 2010* consentono di creare web part per SharePoint che visualizzano le applicazioni Silverlight. Quando si crea questo progetto, è possibile specificare se aggiungervi una nuova applicazione Silverlight o fare riferimento a una esistente. Per altre informazioni, vedere [Create web parts for SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) and [Walkthrough: Create a Silverlight web part that displays OData for SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint web part visiva 2010
 Un SharePoint web *part visuale 2010* include un file diElements.xml, un **elemento web part** e un elemento **Controllo** utente.  È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti Visual Studio alla superficie del controllo utente. Per altre informazioni, vedere [Procedura: Creare una web part SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) usando una finestra di progettazione e un blocco [predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importare SharePoint pacchetto della soluzione 2010
 Importare SharePoint progetti del pacchetto della soluzione *2010* consente di importare tutto o parte di un sito di SharePoint 2010 esistente, esportato in un file della soluzione SharePoint (con estensione *wsp)* in Visual Studio. Dopo l'importazione in Visual Studio, è possibile personalizzarne gli elementi e ridistribuirli. Per altre informazioni, vedere [Importare elementi da un sito SharePoint esistente.](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importare un flusso di lavoro SharePoint 2010
 I progetti Di importazione SharePoint flusso di lavoro *2010* consentono di importare un flusso di lavoro riutilizzabile e dichiarativo creato in SharePoint Designer 2010 in Visual Studio. Il flusso di lavoro viene esportato dal SharePoint come file *con estensione wsp.* Dopo l'importazione in Visual Studio, è possibile personalizzarlo, aggiungervi codice e quindi distribuirlo in un SharePoint sito. Per altre informazioni, vedere [Procedura dettagliata: Importare un flusso di lavoro riutilizzabile](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)SharePoint Designer in Visual Studio .

## <a name="project-item-templates"></a>Project modelli di elemento
 Di seguito è riportato un elenco di SharePoint di elementi di progetto. Project i modelli di elemento aggiungono file alla soluzione SharePoint per supportare SharePoint funzionalità quali colonne del sito, elenchi e tipi di contenuto. Ad esempio, l'aggiunta di una colonna del sito alla soluzione aggiunge un progetto di colonna del sito che contiene un file *Elements.xml* di definizione. L'aggiunta di una web part visiva aggiunge un progetto web part visivo alla soluzione che contiene un file *Elements.xml,* un elemento di controllo utente e un elemento web part visivo.

 Per visualizzare i modelli SharePoint elemento di progetto, **in** Esplora soluzioni aprire il menu di scelta rapida per un progetto SharePoint e quindi scegliere **Aggiungi**, **Nuovo elemento**. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere **2010**.

### <a name="application-page-farm-solution-only"></a>Pagina applicazione (solo soluzione farm)
 Un **elemento Pagina applicazione (solo** soluzione farm) consente di progettare una pagina Web per un SharePoint [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sito. Le pagine delle applicazioni possono essere usate solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per altre informazioni, vedere Procedura: Creare una pagina [dell'applicazione](../sharepoint/how-to-create-an-application-page.md) e Tipo di [_layouts applicazione](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modello di connettività dei dati business (solo soluzione farm)
 Un **elemento Modello di connettività dati business (solo** soluzione farm) consente di integrare i dati aziendali in SharePoint. I dati aziendali possono derivare da applicazioni server back-end, ad esempio [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] , Siebel e Service Advertising Protocol (SAP). I modelli di connettività dei dati aziendali possono essere usati solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per altre informazioni, vedere Procedura: Creare un modello [BDC,](../sharepoint/how-to-create-a-bdc-model.md)Procedura: Usare un file di risorse per specificare nomi [localizzati,](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)proprietà e autorizzazioni e Novità: Servizi di connettività [aziendale.](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))

### <a name="content-type"></a>Tipo di contenuto
 *Gli elementi tipo* di contenuto consentono di creare tipi di contenuto personalizzati in base a un tipo di contenuto esistente (di base), ad esempio un documento, un annuncio o un'attività. Un tipo di contenuto personalizzato fornisce gli stessi attributi e campi del tipo di contenuto di base insieme alle colonne del sito (campi) definite. Ad esempio, è possibile creare un tipo di contenuto Contact personalizzato basato sul tipo di contenuto Contact di base disponibile SharePoint. È possibile personalizzare il tipo di contenuto modificando le colonne del sito esistenti o aggiungendo altre colonne del sito a quelle già incluse nel tipo di contenuto di base.

> [!NOTE]
> A causa di una SharePoint, non è possibile creare un tipo di contenuto della soluzione farm in base a un tipo di contenuto della soluzione in modalità sandbox.

 Per altre informazioni, vedere [Procedura dettagliata: Creare una](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) colonna del sito, un tipo di contenuto ed un elenco per SharePoint e Blocco [predefinito: Tipo di contenuto](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Elemento vuoto
 *Gli elementi vuoti* vengono spesso usati per definire SharePoint di progetto che non dispongono di un modello di progetto o di elemento di progetto Visual Studio. Quando si aggiunge un elemento vuoto al progetto, viene creato un nodo denominato EmptyElement[x](dove [x] è un numero \) univoco. EmptyElement[x] contiene un singolo file denominato *Elements.xml.* Usare [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] le istruzioni per definire gli elementi desiderati in *Elements.xml*.

### <a name="event-receiver"></a>Ricevitore di eventi
 *I ricevitori di* eventi gestiscono gli eventi per gli elementi nel sito SharePoint, ad esempio quando un elemento viene aggiunto a un elenco, quando un elemento Web viene eliminato o quando viene avviato un flusso di lavoro. Il modello di elemento di progetto del ricevitore di eventi consente di gestire

- Elenca gli eventi

- Elencare gli eventi degli elementi

- Elencare gli eventi di posta elettronica

- eventi Web

- Elencare gli eventi del flusso di lavoro

  L'elemento di progetto  ricevitore di eventi crea una cartella ricevitore di eventi con un singolo file di classe che contiene i gestori eventi per tutti gli eventi specificati al momento della creazione del **progetto nella Personalizzazione** guidata SharePoint . La classe ricevitore di eventi può gestire gli eventi che si verificano nel sito SharePoint quando vengono aggiunti, aggiornati, eliminati o rimossi elementi quali file, campi, elementi, elenchi, allegati, web part e flussi di lavoro. Per altre informazioni, vedere [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md) e [Blocco predefinito: Gestione degli eventi](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Elenco
 Un elenco è un'istanza di una definizione di elenco SharePoint base riutilizzabile, ad esempio un calendario o un elenco attività. Dopo aver aggiunto un elenco alla soluzione, Progettazione elenchi consente di aggiungere colonne del sito all'elenco e di creare colonne di elenco personalizzate. Sono incluse le colonne del sito dei tipi di contenuto. È possibile specificare la *visualizzazione* per l'elenco, che determina le colonne che verranno visualizzate nell'elenco. Per altre informazioni, vedere [Procedura dettagliata: Creare](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) una colonna del sito, un tipo di contenuto ed un elenco per SharePoint e [Blocco predefinito:](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))elenchi e raccolte documenti .

### <a name="module"></a>Modulo
 *I* moduli (da non confondere con i moduli) contengono tutti i file che si desidera distribuire nel server SharePoint, ad esempio [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] immagini o note. L'elemento di progetto module contiene un **nodo Module.** Il nodo del modulo contiene due modelli di elemento di progetto: un file di definizione XML, che funge da manifesto per il modulo, e un *file* sample.txt, un file segnaposto. Per altre informazioni, vedere [Usare moduli per includere file nella soluzione e](../sharepoint/using-modules-to-include-files-in-the-solution.md) nei [moduli](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Flusso di lavoro sequenziale (solo soluzione farm)
 Un *flusso di lavoro sequenziale* è una serie di passaggi della logica di business, eseguiti in sequenza, fino al completamento dell'ultimo passaggio. I flussi di lavoro sequenziali vengono usati per gestire i processi che coinvolgono SharePoint elementi, ad esempio elenchi e documenti. È possibile creare flussi di lavoro a livello di sito (globali) o a livello di elenco (locale) ed è possibile selezionare se un flusso di lavoro viene avviato automaticamente o manualmente. Questo elemento di progetto può essere usato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per altre informazioni, vedere Creare soluzioni SharePoint flusso di [lavoro,](../sharepoint/creating-sharepoint-workflow-solutions.md)Flussi di lavoro [in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [Novità: Miglioramenti del](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))flusso di lavoro .

### <a name="silverlight-web-part"></a>Web part Silverlight
 *Gli elementi di progetto* web part Silverlight consentono di creare web part per SharePoint che visualizzano le applicazioni Silverlight. Quando si aggiunge questo elemento di progetto alla soluzione, è possibile scegliere se aggiungere una nuova applicazione Silverlight o fare riferimento a una esistente in un secondo momento. Per altre informazioni, vedere [Create web parts for SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) and [Walkthrough: Create a Silverlight web part that displays OData for SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Colonna del sito
 Una *colonna del sito,* nota anche come campo *,* è uno degli elementi di base che è possibile aggiungere a un SharePoint progetto. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento di testo o il nome della città di un contatto in un elenco contatti. Per altre informazioni, vedere [Creare colonne del sito,](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) tipi di contenuto ed elenchi per SharePoint [colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definizione del sito (solo soluzione farm)
 *Gli elementi del progetto* di definizione del sito contengono una cartella di definizione del sito che include i file seguenti:

- Pagina aspx predefinita, utilizzata come pagina Web predefinita per il sito.

- Un *onet.xml* file che definisce i componenti del sito.

- File xml webtemp che specifica le configurazioni  della definizione del sito visualizzate nella sezione Selezione modello della pagina **SharePoint Sito.**

  Dopo aver aggiunto una definizione del sito, aggiungere codice e file per introdurre funzionalità. Questo elemento di progetto può essere usato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per altre informazioni, vedere [Creare definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [Definizioni e configurazioni del sito](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Flusso di lavoro macchina a stati (solo soluzione farm)
 Un *flusso di lavoro della macchina* a stati è un set di stati, transizioni e azioni della logica di business. I passaggi in un flusso di lavoro macchina a stati non vengono eseguiti in sequenza. vengono invece attivati da azioni e stati. Analogamente a un flusso di lavoro sequenziale, i flussi di lavoro delle macchine a stati sono associati SharePoint elementi quali elenchi e documenti. Ancora una volta, è possibile creare flussi di lavoro a livello di sito (globali) o flussi di lavoro a livello di elenco (locale). È anche possibile scegliere se un flusso di lavoro viene avviato automaticamente o manualmente. Questo elemento di progetto può essere usato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per altre informazioni, vedere Creare soluzioni SharePoint flusso di [lavoro,](../sharepoint/creating-sharepoint-workflow-solutions.md)Flussi di lavoro [in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [Novità: Miglioramenti del](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))flusso di lavoro .

### <a name="user-control-farm-solution-only"></a>Controllo utente (solo soluzione farm)
 Un *controllo utente* è un controllo personalizzato e riutilizzabile a cui è possibile aggiungere altri controlli ASP.NET e SharePoint controllo. Il controllo utente può essere aggiunto alle pagine dell'applicazione e alle web part eseguite in SharePoint. Questo elemento di progetto può essere usato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per altre informazioni, vedere [Creating Reusable Controls for Web part or Application Pages](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Web part visiva
 Un *elemento di progetto web part* visivo include un *Elements.xml* di definizione, un elemento web **part** e un elemento **Controllo** utente. È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti Visual Studio alla superficie del controllo utente. Per altre informazioni, vedere [Procedura: Creare una web part SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) usando una finestra di progettazione e un blocco [predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web part
 Una *web part è* un controllo lato server che viene eseguito all'interno di un tipo speciale di pagina denominata pagina web part. Si tratta dei blocchi predefiniti delle pagine che vengono visualizzati in un SharePoint sito. L'elemento web part fornisce file che consentono di progettare una web part per un SharePoint sito. Per altre informazioni, vedere [Procedura: Creare una web part SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) e Blocco [predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Prodotti e tecnologie SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
