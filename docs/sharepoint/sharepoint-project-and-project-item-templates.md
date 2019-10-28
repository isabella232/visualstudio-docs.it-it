---
title: Modelli di progetto e di elementi di progetto SharePoint | Microsoft Docs
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
ms.openlocfilehash: 825e985820ac7a4d72bf321133491e312adb0a0e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981946"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modelli di progetto e di elementi di progetto SharePoint
  Le sezioni seguenti descrivono i modelli di progetto e di elemento di progetto SharePoint disponibili e il modo in cui vengono usati.

## <a name="project-and-project-item-templates-overview"></a>Panoramica sui modelli di progetti e di elementi di progetto
 Quando si crea un nuovo progetto SharePoint in Visual Studio, un progetto SharePoint viene aggiunto alla soluzione insieme a tutti gli elementi del progetto richiesti da tale tipo di progetto. Se, ad esempio, si crea un progetto Web part Silverlight, Visual Studio crea una soluzione che contiene un elemento di progetto Web part visiva e un elemento del progetto di applicazione Silverlight insieme a tutti i file richiesti da tali elementi del progetto. I modelli di elementi di progetto vengono utilizzati per aggiungere elementi di progetto a un progetto SharePoint esistente, ad esempio l'aggiunta di un ricevitore di eventi, una colonna del sito o un elenco.

 Per informazioni sui concetti fondamentali di SharePoint, vedere la pagina relativa ai [blocchi predefiniti di SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Gli utenti avanzati possono creare modelli di progetto e di elementi di progetto personalizzati. Per ulteriori informazioni, vedere [estensione del sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modelli di progetto
 Di seguito è riportato un elenco di modelli di progetto SharePoint. Per visualizzare i modelli di progetto SharePoint in Visual Studio, nella finestra di dialogo **nuovo progetto** espandere il nodo **SharePoint** sotto **Visual C#**  o **Visual Basic**, quindi selezionare **2010**.

### <a name="sharepoint-2010-project"></a>Progetto SharePoint 2010
 Il contenuto di un *progetto sharepoint 2010* è incluso in ogni modello di progetto SharePoint. Un progetto SharePoint 2010 contiene:

- Un file di progetto.

- Pagina delle proprietà di un progetto.

- Una cartella **References** che elenca tutti i riferimenti ad assembly nel progetto.

- Una cartella **features** che contiene un file di configurazione con *estensione feature* utilizzato per distribuire le funzionalità di in SharePoint Server.

- Cartella del **pacchetto** che contiene un file *Package. Package* usato per distribuire la soluzione in SharePoint.

- File Key. snk (chiave con nome sicuro) utilizzato per firmare l'assembly con un nome sicuro, per una maggiore sicurezza.

### <a name="sharepoint-2010-silverlight-web-part"></a>Web part Silverlight di SharePoint 2010
 I progetti *Web part Silverlight di sharepoint 2010* consentono di creare Web part per SharePoint che visualizzano le applicazioni Silverlight. Quando si crea questo progetto, è possibile specificare se aggiungere una nuova applicazione Silverlight o farvi riferimento. Per ulteriori informazioni, vedere la pagina relativa alla creazione di [Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [procedura dettagliata: creazione di una Web part Silverlight che visualizza OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Web part visiva di SharePoint 2010
 Un progetto *Web part visiva di SharePoint 2010* include un file di definizione *Elements. XML* , un elemento **Web part** e un elemento del **controllo utente** . È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio alla superficie del controllo utente. Per ulteriori informazioni, vedere [procedura: creare una Web part di SharePoint tramite una finestra di progettazione e un](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importa pacchetto della soluzione SharePoint 2010
 I progetti di *pacchetti della soluzione sharepoint 2010* consentono di importare tutto o parte di un sito di SharePoint 2010 esistente, esportato in un file di soluzione SharePoint (con*estensione wsp*) in Visual Studio. Una volta importato in Visual Studio, è possibile personalizzarne gli elementi e ridistribuirli. Per ulteriori informazioni, vedere [importare elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importa flusso di lavoro riutilizzabile di SharePoint 2010
 L'importazione di progetti di *flusso di lavoro di SharePoint 2010 riutilizzabili* consente di importare un flusso di lavoro dichiarativo riutilizzabile creato in sharepoint designer 2010 in Visual Studio. Il flusso di lavoro viene esportato dal sito di SharePoint come file con estensione *WSP* . Una volta importato in Visual Studio, è possibile personalizzarlo, aggiungervi codice e distribuirlo in un sito di SharePoint. Per ulteriori informazioni, vedere [procedura dettagliata: importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Modelli di elementi di progetto
 Di seguito è riportato un elenco di modelli di elementi di progetto SharePoint. I modelli di elemento di progetto aggiungono file alla soluzione SharePoint per supportare funzionalità di SharePoint quali colonne del sito, elenchi e tipi di contenuto. Se ad esempio si aggiunge una colonna del sito alla soluzione, viene aggiunto un progetto di colonna del sito contenente un file di definizione *Elements. XML* . L'aggiunta di una Web part visiva consente di aggiungere un progetto Web part visiva alla soluzione contenente un file *Elements. XML* , un elemento di controllo utente e un elemento Web part visiva.

 Per visualizzare i modelli di elementi di progetto SharePoint, in **Esplora soluzioni**aprire il menu di scelta rapida per un progetto SharePoint, quindi scegliere **Aggiungi**, **nuovo elemento**. Espandere il nodo **SharePoint** sotto **Visual C#**  o **Visual Basic**, quindi selezionare **2010**.

### <a name="application-page-farm-solution-only"></a>Pagina applicazione (solo soluzione farm)
 L'elemento **pagina applicazione (solo soluzione farm)** consente di progettare una pagina Web [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] per un sito di SharePoint. Le pagine delle applicazioni possono essere utilizzate solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo alle soluzioni farm. Per altre informazioni, vedere [procedura: creare una pagina dell'applicazione e un tipo di](../sharepoint/how-to-create-an-application-page.md) [pagina _layouts dell'applicazione](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modello di integrazione applicativa dei dati (solo soluzione farm)
 Un elemento **modello di integrazione applicativa dei dati (solo soluzione farm)** consente di integrare i dati aziendali in SharePoint. I dati aziendali possono provenire da applicazioni server back-end, ad esempio [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel e Service Advertising Protocol (SAP). I modelli di integrazione applicativa dei dati possono essere utilizzati solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo alle soluzioni farm. Per altre informazioni, vedere [procedura: creare un modello di integrazione applicativa](../sharepoint/how-to-create-a-bdc-model.md)dei dati, [procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)e novità [: Servizi di connettività aziendale](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Tipo di contenuto
 Gli elementi del *tipo di contenuto* consentono di creare tipi di contenuto personalizzati basati su un tipo di contenuto (base) esistente, ad esempio un documento, un annuncio o un'attività. Un tipo di contenuto personalizzato fornisce gli stessi attributi e campi del tipo di contenuto di base insieme a tutte le colonne del sito (campi) definite. Ad esempio, è possibile creare un tipo di contenuto contatto personalizzato basato sul tipo di contenuto contatto di base incluso in SharePoint. È possibile personalizzare il tipo di contenuto modificando le colonne del sito esistenti o aggiungendo altre colonne del sito a quelle già incluse nel tipo di contenuto di base.

> [!NOTE]
> A causa di una limitazione di SharePoint, non è possibile creare un tipo di contenuto della soluzione farm basato su un tipo di contenuto della soluzione creata mediante sandbox.

 Per ulteriori informazioni, vedere [procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: tipo di contenuto](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Elemento vuoto
 *Gli elementi vuoti* vengono spesso utilizzati per definire gli elementi del progetto SharePoint che non dispongono di un modello di progetto o di elemento di progetto in Visual Studio. Quando si aggiunge un elemento vuoto al progetto, viene creato un nodo denominato EmptyElement [x] (dove [x] è un numero univoco\). EmptyElement [x] contiene un singolo file denominato *Elements. XML.* Utilizzare le istruzioni [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] per definire gli elementi desiderati in *Elements. XML*.

### <a name="event-receiver"></a>Ricevitore di eventi
 I *ricevitori di eventi* gestiscono gli eventi per gli elementi nel sito di SharePoint, ad esempio quando un elemento viene aggiunto a un elenco, quando viene eliminato un elemento Web o quando un flusso di lavoro viene avviato. Il modello di elemento del progetto ricevitore di eventi consente di gestire

- Elenca eventi

- Eventi elemento elenco

- Elencare gli eventi di posta elettronica

- eventi Web

- Elenca eventi flusso di lavoro

  L'elemento del progetto ricevitore di eventi crea una cartella del **ricevitore di eventi** con un unico file di classe che contiene i gestori eventi per tutti gli eventi specificati al momento della creazione del progetto nella **procedura guidata di personalizzazione di SharePoint**. La classe del ricevitore di eventi può gestire gli eventi che si verificano nel sito di SharePoint quando vengono aggiunti, aggiornati, eliminati o rimossi elementi quali file, campi, elementi, elenchi, allegati, Web part e flussi di lavoro. Per altre informazioni, vedere [procedura: creare un ricevitore di eventi e un](../sharepoint/how-to-create-an-event-receiver.md) [blocco predefinito: gestione degli eventi](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>List
 Un elenco è un'istanza di una definizione di elenco di SharePoint di base riutilizzabile, ad esempio un calendario o un elenco di attività. Dopo l'aggiunta di un elenco alla soluzione, la finestra di progettazione elenco consente di aggiungere le colonne del sito all'elenco e creare colonne elenco personalizzate. Sono incluse le colonne del sito dei tipi di contenuto. È possibile specificare la *visualizzazione* per l'elenco, che determina le colonne che verranno visualizzate nell'elenco. Per ulteriori informazioni, vedere [procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: elenchi e raccolte documenti](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modulo
 I *moduli* (da non confondere con i moduli [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]) contengono tutti i file che si desidera distribuire nel server SharePoint, ad esempio immagini o note. L'elemento del progetto di modulo contiene un nodo del **modulo** . Il nodo modulo contiene due modelli di elemento di progetto: un file di definizione XML, che funge da manifesto per il modulo e un file *Sample. txt* , un file segnaposto. Per altre informazioni, vedere [usare i moduli per includere file nella soluzione e nei](../sharepoint/using-modules-to-include-files-in-the-solution.md) [moduli](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Flusso di lavoro sequenziale (solo soluzione farm)
 Un *flusso di lavoro sequenziale* è una serie di passaggi della logica di business, eseguiti in sequenza, fino al completamento dell'ultimo passaggio. I flussi di lavoro sequenziali vengono utilizzati per gestire i processi che coinvolgono elementi di SharePoint, ad esempio elenchi e documenti. È possibile creare flussi di lavoro a livello di sito (globali) o flussi di lavoro a livello di elenco (locale) ed è possibile scegliere se un flusso di lavoro viene avviato automaticamente o manualmente. Questo elemento del progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flussi di lavoro in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e novità [: miglioramenti del flusso di lavoro](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Web part Silverlight
 Gli elementi del progetto *Web part Silverlight* consentono di creare Web part per SharePoint che visualizzano le applicazioni Silverlight. Quando si aggiunge questo elemento di progetto alla soluzione, è possibile scegliere se aggiungere una nuova applicazione Silverlight o farvi riferimento in un secondo momento. Per ulteriori informazioni, vedere la pagina relativa alla creazione di [Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [procedura dettagliata: creazione di una Web part Silverlight che visualizza OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Colonna del sito
 Una *colonna del sito*, nota anche come *campo*, è uno degli elementi più semplici che è possibile aggiungere a un progetto SharePoint. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento di testo o il nome della città di un contatto in un elenco di contatti. Per ulteriori informazioni, vedere [la pagina relativa alla creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definizione del sito (solo soluzione farm)
 Gli elementi del progetto di *definizione sito* contengono una cartella di definizione sito che include i file seguenti:

- Una pagina default. aspx, utilizzata come pagina Web predefinita per il sito.

- Un file *Onet. XML* che definisce i componenti del sito.

- Un file webtemp XML che specifica le configurazioni di definizione del sito visualizzate nella sezione **Selezione modello** della pagina **nuovo sito di SharePoint** .

  Dopo aver aggiunto una definizione di sito, aggiungere il codice e i file per introdurre la funzionalità. Questo elemento del progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [la pagina relativa alla creazione di definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [definizioni e configurazioni di siti](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Flusso di lavoro macchina a stati (solo soluzione farm)
 Un *flusso di lavoro* di una macchina a Stati è un set di Stati, transizioni e azioni della logica di business. I passaggi nel flusso di lavoro di una macchina a Stati non vengono eseguiti in sequenza; vengono invece attivati da azioni e Stati. Analogamente a un flusso di lavoro sequenziale, i flussi di lavoro macchina a Stati sono associati a elementi di SharePoint, ad esempio elenchi e documenti. Ancora una volta, è possibile creare flussi di lavoro a livello di sito (globali) o flussi di lavoro a livello di elenco (locale). È inoltre possibile specificare se un flusso di lavoro viene avviato automaticamente o manualmente. Questo elemento del progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flussi di lavoro in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e novità [: miglioramenti del flusso di lavoro](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Controllo utente (solo soluzione farm)
 Un *controllo utente* è un controllo personalizzato e riutilizzabile a cui è possibile aggiungere altri controlli ASP.NET e controlli di SharePoint. Il controllo utente può essere aggiunto alle pagine dell'applicazione e alle web part eseguite in SharePoint. Questo elemento del progetto può essere utilizzato solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo alle soluzioni farm. Per ulteriori informazioni, vedere [creazione di controlli riutilizzabili per Web part o pagine dell'applicazione](/visualstudio/sharepoint/creating-reusable-controls-for-web-parts-or-application-pages&view=vs-2019).

### <a name="visual-web-part"></a>Web part visiva
 Un elemento del progetto *Web part visiva* include un file di definizione *Elements. XML* , un elemento **Web part** e un elemento del **controllo utente** . È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio alla superficie del controllo utente. Per ulteriori informazioni, vedere [procedura: creare una Web part di SharePoint tramite una finestra di progettazione e un](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web part
 Una *Web part* è un controllo lato server che viene eseguito all'interno di un tipo speciale di pagina denominata Web Part Page. Sono i blocchi predefiniti di pagine visualizzate in un sito di SharePoint. L'elemento Web part fornisce file che consentono di progettare una Web part per un sito di SharePoint. Per ulteriori informazioni, vedere [procedura: creare una Web part di SharePoint e un](../sharepoint/how-to-create-a-sharepoint-web-part.md) [blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Prodotti e tecnologie SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
