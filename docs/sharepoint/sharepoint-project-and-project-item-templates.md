---
title: Modelli di progetti e di elementi di progetto di SharePoint - Documenti Microsoft
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649230"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modelli di progetto e di elemento di progetto SharePointSharePoint project and project item templates
  Nelle sezioni seguenti vengono descritti i modelli di progetto e di elemento di progetto SharePoint disponibili e il modo in cui vengono utilizzati.

## <a name="project-and-project-item-templates-overview"></a>Panoramica dei modelli di progetto e di elemento di progetto
 Quando si crea un nuovo progetto SharePoint in Visual Studio, un progetto SharePoint viene aggiunto alla soluzione insieme a tutti gli elementi di progetto richiesti da tale tipo di progetto. Ad esempio, se si crea un progetto Web Part Silverlight, Visual Studio crea una soluzione che contiene un elemento di progetto Visual Web Part e un elemento di progetto di applicazione Silverlight insieme a tutti i file richiesti da tali elementi di progetto. I modelli di elemento di progetto vengono utilizzati per aggiungere elementi di progetto a un progetto SharePoint esistente, ad esempio l'aggiunta di un ricevitore di eventi, una colonna del sito o un elenco.

 Per informazioni sulle nozioni fondamentali di SharePoint, vedere [Blocchi predefiniti di SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Gli utenti avanzati possono creare modelli di progetto e di elemento di progetto personalizzati. Per ulteriori informazioni, vedere [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modelli di progetto
 Di seguito è riportato un elenco di modelli di progetto SharePoint.Following is a list of SharePoint project templates. Per visualizzare i modelli di progetto SharePoint in Visual Studio, nella finestra di dialogo **Nuovo progetto** espandere il nodo **SharePoint** in **Visual Cè** o **Visual Basic**, quindi scegliere **2010**.

### <a name="sharepoint-2010-project"></a>Progetto SharePoint 2010
 Il contenuto di un *progetto SharePoint 2010* è incluso in ogni modello di progetto SharePoint. Un progetto SharePoint 2010 contiene:

- Un file di progetto.

- Una pagina delle proprietà del progetto.

- Una cartella **Riferimenti** che elenca tutti i riferimenti all'assembly nel progetto.

- Una cartella **Features** che contiene un file di configurazione *con estensione feature,* utilizzato per distribuire le funzionalità nel server SharePoint.

- Una cartella **Package** che contiene un file *Package.package,* usato per distribuire la soluzione in SharePoint.

- Un file key.snk (chiave con nome sicuro) utilizzato per firmare l'assembly con un nome sicuro, per una maggiore sicurezza.

### <a name="sharepoint-2010-silverlight-web-part"></a>Web part Silverlight di SharePoint 2010
 I progetti web part Silverlight di *SharePoint 2010* consentono di creare web part per SharePoint che visualizzano applicazioni Silverlight. Quando si crea questo progetto, è possibile specificare se aggiungervi una nuova applicazione Silverlight o farvi riferimento a una esistente. Per ulteriori informazioni, vedere [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e Procedura [dettagliata: Creare una web part Silverlight che visualizza OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Web part visiva di SharePoint 2010
 Un progetto di web part visiva di *SharePoint 2010* include un file di definizione *Elements.xml,* un elemento **Web part** e un elemento **Controllo utente.** È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla Casella degli strumenti di Visual Studio all'area del controllo utente. Per ulteriori informazioni, vedere Procedura: creare una web part di [SharePoint tramite una finestra](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) di progettazione e un [blocco predefinito: web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importare il pacchetto della soluzione SharePoint 2010
 Importare progetti *di pacchetto della soluzione SharePoint 2010* consente di importare tutto o parte di un sito di SharePoint 2010 esistente, esportato in un file di soluzione SharePoint ( con estensione*wsp)* in Visual Studio. Una volta importati in Visual Studio, è possibile personalizzarne gli elementi e ridistribuirli. Per ulteriori informazioni, vedere Importare elementi da un sito di [SharePoint esistente.](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importare il flusso di lavoro riutilizzabile di SharePoint 2010
 Importare progetti flusso di *lavoro riutilizzabili di SharePoint 2010* consente di importare un flusso di lavoro riutilizzabile e dichiarativo creato in SharePoint Designer 2010 in Visual Studio. Il flusso di lavoro viene esportato dal sito di SharePoint come file *con estensione wsp.* Dopo l'importazione in Visual Studio, è possibile personalizzarlo, aggiungervi codice e quindi distribuirlo in un sito di SharePoint. Per ulteriori informazioni, vedere Procedura dettagliata: importare un flusso di lavoro [riutilizzabile](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)di SharePoint Designer in Visual Studio .

## <a name="project-item-templates"></a>Modelli di elemento di progetto
 Di seguito è riportato un elenco di modelli di elemento di progetto SharePoint.Following is a list of SharePoint project item templates. I modelli di elemento di progetto aggiungono file alla soluzione SharePoint per supportare le funzionalità di SharePoint, ad esempio colonne del sito, elenchi e tipi di contenuto. Ad esempio, l'aggiunta di una colonna del sito alla soluzione aggiunge un progetto di colonna del sito che contiene un file di definizione *Elements.xml.For* example, adding a site column to your solution adds a site column project that contains an Elements.xml definition file. L'aggiunta di una web part visiva aggiunge un progetto web part visiva alla soluzione che contiene un file *Elements.xml,* un elemento del controllo utente e un elemento web part visiva.

 Per visualizzare i modelli di elemento di progetto SharePoint, in **Esplora soluzioni**aprire il menu di scelta rapida per un progetto SharePoint, quindi scegliere **Aggiungi**, **Nuovo elemento**. Espandere il nodo **SharePoint** in **Visual C,** Visual Basic o **Visual Basic**, quindi scegliere **2010**.

### <a name="application-page-farm-solution-only"></a>Pagina dell'applicazione (solo soluzione farm)
 Un elemento **Pagina applicazione (solo soluzione farm)** consente di progettare una [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina Web per un sito di SharePoint. Le pagine delle applicazioni possono essere utilizzate solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere Procedura: creare una [pagina dell'applicazione](../sharepoint/how-to-create-an-application-page.md) e [Tipo di pagina _layouts applicazione](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modello di integrazione applicativa dei dati (solo soluzione farm)
 Un elemento **Modello di integrazione applicativa dei dati (solo soluzione farm)** consente di integrare i dati business in SharePoint.A Business Data Connectivity Model (Farm Solution Only) item enables you to Integrate business data into SharePoint. I dati aziendali possono provenire da [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]applicazioni server back-end, ad esempio , Siebel e Service Advertising Protocol (SAP). I modelli di integrazione applicativa dei dati possono essere utilizzati solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [Procedura: creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md), Procedura: utilizzare un file di risorse [per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)e Novità: Servizi di [integrazione applicativa](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Tipo di contenuto
 *Gli* elementi Tipo di contenuto consentono di creare tipi di contenuto personalizzati basati su un tipo di contenuto esistente (di base), ad esempio un documento, un annuncio o un'attività. Un tipo di contenuto personalizzato fornisce gli stessi attributi e campi del tipo di contenuto di base insieme a tutte le colonne del sito (campi) definite. Ad esempio, è possibile creare un tipo di contenuto Contatto personalizzato basato sul tipo di contenuto Contatto di base disponibile in SharePoint.For example, you can create a custom Contact content type that is based on the base Contact content type that comes in SharePoint. È possibile personalizzare il tipo di contenuto modificando le colonne del sito esistenti o aggiungendo altre colonne del sito a quelle già incluse nel tipo di contenuto di base.

> [!NOTE]
> A causa di una limitazione di SharePoint, non è possibile creare un tipo di contenuto della soluzione farm basato su un tipo di contenuto della soluzione in modalità sandbox.

 Per ulteriori informazioni, vedere Procedura dettagliata: creare una colonna del [sito, un tipo di contenuto ed un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: tipo di contenuto](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Elemento vuoto
 *Gli elementi vuoti* vengono spesso utilizzati per definire gli elementi di progetto SharePoint che non dispongono di un modello di progetto o di elemento di progetto in Visual Studio.Empty elements are most often used to define SharePoint project items that lack a project or project item template in Visual Studio. Quando si aggiunge un elemento vuoto al progetto, viene creato un nodo denominato\) EmptyElement[x](dove [x] è un numero univoco. EmptyElement[x] contiene un singolo file denominato *Elements.xml.* Utilizzare [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] le istruzioni per definire gli elementi desiderati in *Elements.xml*.

### <a name="event-receiver"></a>Ricevitore di eventi
 *I ricevitori di* eventi gestiscono gli eventi per gli elementi nel sito di SharePoint, ad esempio quando un elemento viene aggiunto a un elenco, quando viene eliminato un elemento Web o all'avvio di un flusso di lavoro. Il modello di elemento di progetto del ricevitore di eventi consente di gestire

- Elenca gli eventi

- Eventi voci di elenco

- Elencare gli eventi di posta elettronica

- eventi Web

- Elencare gli eventi del flusso di lavoroList workflow events

  L'elemento di progetto del ricevitore di eventi crea una cartella **Ricevitore** di eventi con un singolo file di classe contenente gestori eventi per tutti gli eventi specificati al momento della creazione del progetto nella **Personalizzazione guidata SharePoint.** La classe del ricevitore di eventi può gestire gli eventi che si verificano nel sito di SharePoint quando elementi quali file, campi, elementi, elenchi, allegati, web part e flussi di lavoro vengono aggiunti, aggiornati, eliminati o rimossi. Per ulteriori informazioni, vedere [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md) e [Blocco predefinito: gestione degli](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))eventi .

### <a name="list"></a>Elenco
 Un elenco è un'istanza di una definizione di elenco di SharePoint di base riutilizzabile, ad esempio un calendario o un elenco di attività. Dopo aver aggiunto un elenco alla soluzione, Progettazione elenchi consente di aggiungere colonne del sito all'elenco e creare colonne di elenco personalizzate. Sono incluse le colonne del sito dai tipi di contenuto. È possibile specificare la *visualizzazione* per l'elenco, che determina le colonne che verranno visualizzate nell'elenco. Per ulteriori informazioni, vedere Procedura dettagliata: creazione di una colonna del [sito, di un tipo di contenuto e](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) di un elenco per SharePoint e Blocco [predefinito: elenchi e raccolte documenti](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modulo
 *I moduli* (da [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] non confondere con i moduli) contengono i file che si desidera distribuire nel server SharePoint, ad esempio immagini o note. L'elemento di progetto modulo contiene un **Module** nodo. Il nodo module contiene due modelli di elemento di progetto: un file di definizione XML, che funge da manifesto per il modulo, e un file *sample.txt,* un file segnaposto. Per ulteriori informazioni, vedere [Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md) e nei [moduli](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Flusso di lavoro sequenziale (solo soluzione farm)
 Un *flusso di lavoro sequenziale* è una serie di passaggi della logica di business, eseguiti in sequenza, fino al completamento dell'ultimo passaggio. I flussi di lavoro sequenziali vengono utilizzati per gestire i processi che coinvolgono elementi di SharePoint, ad esempio elenchi e documenti. È possibile creare flussi di lavoro a livello di sito (globale) o a livello di elenco (locale) e selezionare se un flusso di lavoro viene avviato automaticamente o manualmente. Questo elemento di progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [Create SharePoint workflow solutions](../sharepoint/creating-sharepoint-workflow-solutions.md), Workflows in [SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [What's New: Workflow Improvements](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Web part Silverlight
 *Gli* elementi del progetto Web part Silverlight consentono di creare web part per SharePoint che visualizzano le applicazioni Silverlight. Quando si aggiunge questo elemento di progetto alla soluzione, è possibile scegliere se aggiungere una nuova applicazione Silverlight o fare riferimento a una esistente in un secondo momento. Per ulteriori informazioni, vedere [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e Procedura [dettagliata: Creare una web part Silverlight che visualizza OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Colonna sito
 Una colonna del *sito*, nota anche come *campo*, è uno degli elementi di base che è possibile aggiungere a un progetto SharePoint. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento di testo o il nome della città di un contatto in un elenco di contatti. Per ulteriori informazioni, vedere [Creare colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [Colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definizione di sito (solo soluzione farm)
 Gli elementi di progetto *di definizione di sito* contengono una cartella di definizione di sito che include i file seguenti:Site definition project items contain a site definition folder that includes the following files:

- Una pagina aspx predefinita, utilizzata come pagina Web predefinita per il sito.

- Un file *onet.xml* che definisce i componenti del sito.

- Un file XML webtemp che specifica le configurazioni delle definizioni di sito visualizzate nella sezione **Selezione modello** della pagina **Nuovo sito di SharePoint.**

  Dopo aver aggiunto una definizione di sito, aggiungere codice e file per introdurre funzionalità. Questo elemento di progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [Creare definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [Definizioni e configurazioni](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14))di sito .

### <a name="state-machine-workflow-farm-solution-only"></a>Flusso di lavoro macchina a stati (solo soluzione farm)
 Un *flusso di lavoro* macchina a stati è un set di stati, transizioni e azioni della logica di business. I passaggi in un flusso di lavoro della macchina a stati non vengono eseguiti in sequenza. vengono invece attivati da azioni e stati. Analogamente a un flusso di lavoro sequenziale, i flussi di lavoro macchina a stati sono associati a elementi di SharePoint, ad esempio elenchi e documenti. Ancora una volta, è possibile creare flussi di lavoro a livello di sito (globale) o a livello di elenco (locale). È inoltre possibile selezionare se un flusso di lavoro viene avviato automaticamente o manualmente. Questo elemento di progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [Create SharePoint workflow solutions](../sharepoint/creating-sharepoint-workflow-solutions.md), Workflows in [SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [What's New: Workflow Improvements](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Controllo utente (solo soluzione farm)
 Un *controllo utente* è un controllo personalizzato e riutilizzabile a cui è possibile aggiungere altri controlli ASP.NET e controlli di SharePoint.A user control is a custom, reusable control to which you can add other ASP.NET controls and SharePoint controls. Il controllo utente può essere aggiunto alle pagine dell'applicazione e alle web part eseguite in SharePoint.The user control can be added to application pages and web parts that run in SharePoint. Questo elemento di progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento di progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [Creazione di controlli riutilizzabili per web part o pagine di applicazioni](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Web part visiva
 Un elemento di progetto *Web part visiva* include un file di definizione *Elements.xml,* un elemento **web part** e un elemento **Controllo utente.** È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla Casella degli strumenti di Visual Studio all'area del controllo utente. Per ulteriori informazioni, vedere Procedura: creare una web part di [SharePoint tramite una finestra](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) di progettazione e un [blocco predefinito: web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web part
 Una *web part* è un controllo lato server che viene eseguito all'interno di un tipo speciale di pagina denominato pagina web part. Sono i blocchi predefiniti delle pagine visualizzate in un sito di SharePoint. L'elemento web part fornisce file che consentono di progettare una web part per un sito di SharePoint. Per ulteriori informazioni, vedere [Procedura: creare una web part](../sharepoint/how-to-create-a-sharepoint-web-part.md) di SharePoint e Blocco [predefinito: web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Prodotti e tecnologie SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
