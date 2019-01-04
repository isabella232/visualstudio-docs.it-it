---
title: Modelli di elemento di progetto SharePoint e Project | Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71590e2cd5ece2a025b2aef3dfa0baf612fb2808
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936295"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Progetto SharePoint e i modelli di progetto
  Le sezioni seguenti descrivono il progetto SharePoint disponibili e i modelli e come vengono usati di elemento di progetto. 
  
## <a name="project-and-project-item-templates-overview"></a>Cenni preliminari sui modelli di elemento di progetto e progetto
 Quando si crea un nuovo progetto di SharePoint in Visual Studio, un progetto SharePoint viene aggiunto alla soluzione insieme a tutti gli elementi del progetto richiesti dal tipo di progetto. Ad esempio, se si crea un progetto di Web Part Silverlight, Visual Studio crea una soluzione che contiene un elemento del progetto Web Part visiva e un elemento di progetto dell'applicazione Silverlight insieme a tutti i file necessari per tali elementi di progetto. I modelli di progetto consentono di aggiungere elementi del progetto a un progetto di SharePoint esistente, ad esempio l'aggiunta di un ricevitore di eventi, colonne del sito o elenco.  
  
 Per informazioni sui concetti fondamentali di SharePoint, vedere [blocchi predefiniti di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Gli utenti esperti possono creare progetto personalizzato e i modelli di progetto. Per altre informazioni, vedere [estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
## <a name="project-templates"></a>Modelli di progetto
 Seguito è riportato un elenco di modelli di progetto SharePoint. Per visualizzare i modelli di progetto SharePoint in Visual Studio nel **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo sotto **Visual C#**  o  **Visual Basic**, quindi scegliere **2010**.  
  
### <a name="sharepoint-2010-project"></a>Progetto di SharePoint 2010
 Il contenuto di un *progetto SharePoint 2010* sono inclusi in ogni modello di progetto SharePoint. Contiene un progetto SharePoint 2010:  
  
-   Un file di progetto.  
  
-   Una pagina delle proprietà di progetto.  
  
-   Oggetto **riferimenti** cartella Elenca tutti i riferimenti all'assembly nel progetto.  
  
-   Oggetto **caratteristiche** cartella che contiene un *feature* file di configurazione, usato per distribuire le funzionalità in server SharePoint.  
  
-   Oggetto **Package** cartella che contiene un *package. package* file, usato per distribuire la soluzione in SharePoint.  
  
-   Un file snk (chiave con nome sicuro) utilizzato per firmare l'assembly con un nome sicuro, per maggiore sicurezza.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Web part Silverlight di SharePoint 2010
 *Web Part Silverlight di SharePoint 2010* progetti consentono di creare web part per SharePoint che consentono di visualizzare le applicazioni Silverlight. Quando si crea il progetto, è possibile specificare se si desidera aggiungere una nuova applicazione Silverlight o fare riferimento a uno esistente. Per altre informazioni, vedere [creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [procedura dettagliata: Creare una web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Visual web part di SharePoint 2010
 Oggetto *Web Part visiva di SharePoint 2010* progetto include un *Elements. XML* file di definizione, una **Web Part** elemento e un **controllo utente** elemento . È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio alla superficie del controllo utente. Per altre informazioni, vedere [Procedura: Creare una web part di SharePoint usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importa pacchetto di soluzione SharePoint 2010
 *Importa pacchetto di soluzione SharePoint 2010* progetti consentono di importare tutto o parte di un sito di SharePoint 2010 esistente, esportato in una soluzione di SharePoint (*wsp*) file in Visual Studio. Una volta importato in Visual Studio, è possibile personalizzare gli elementi e ridistribuirle. Per altre informazioni, vedere [importare gli elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Importa flusso di lavoro riutilizzabile di SharePoint 2010
 *Importare riutilizzabili flusso di lavoro di SharePoint 2010* progetti consentono di importare un flusso di lavoro dichiarativo e riutilizzabile creato in SharePoint Designer 2010 in Visual Studio. Il flusso di lavoro viene esportato dal sito di SharePoint come un *wsp* file. Una volta importato in Visual Studio, è possibile personalizzarlo, aggiungere codice al file e quindi distribuirla in un sito di SharePoint. Per altre informazioni, vedere [Procedura dettagliata: Importa un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
## <a name="project-item-templates"></a>I modelli di progetto
 Seguito è riportato un elenco di modelli di elemento di progetto SharePoint. I modelli di progetto aggiungono file alla soluzione di SharePoint per supportare la funzionalità di SharePoint, ad esempio le colonne del sito, elenchi e tipi di contenuto. Ad esempio, l'aggiunta di una colonna del sito per la soluzione aggiunge un progetto colonna del sito che contiene un' *Elements* file di definizione. Aggiunta di una web part visiva viene aggiunto un progetto web part visiva alla soluzione che contiene un' *Elements* file, un elemento del controllo utente e un elemento web part visiva.  
  
 Per visualizzare i modelli di elemento di progetto SharePoint, in **Esplora soluzioni**, aprire il menu di scelta rapida per un progetto SharePoint e quindi scegliere **Add**, **nuovo elemento**. Espandere la **SharePoint** nodo sotto **Visual c#** oppure **Visual Basic**, quindi scegliere **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Pagina dell'applicazione (solo soluzione farm)
 Un' **(solo soluzione Farm) pagina dell'applicazione** elemento consente di progettare un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina web per un sito di SharePoint. Le pagine di applicazioni sono utilizzabile solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo per soluzioni farm. Per altre informazioni, vedere [Procedura: Creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md) e [applicazione layouts tipo pagina](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Modello di integrazione applicativa dei dati aziendali (solo soluzione farm)
 Oggetto **Business Data Connectivity Model (solo soluzione Farm)** elemento consente di integrare i dati aziendali in SharePoint. I dati aziendali possono provenire da applicazioni server back-end, ad esempio [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel e servizi pubblicitari protocollo (SAP). Modelli di connettività dei dati aziendali sono utilizzabile solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo per soluzioni farm. Per altre informazioni, vedere [Procedura: Creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md), [come: Usare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), e [novità recenti: Servizi di integrazione applicativa](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Tipo di contenuto
 *Tipo di contenuto* elementi consentono di creare tipi di contenuto personalizzati basati su un tipo di contenuto (base), ad esempio un documento, un annuncio o un'attività. Un tipo di contenuto personalizzato offre gli stessi attributi e i campi come tipo di contenuto base insieme a tutte le colonne del sito (campi) si definisce. Ad esempio, è possibile creare un tipo di contenuto contatto personalizzato basato sul tipo di base contatto contenuto è disponibile in SharePoint. È possibile personalizzare il tipo di contenuto modificando le colonne del sito esistente o aggiungendo ulteriori colonne del sito a quelli già inclusi nel tipo di contenuto base.  
  
> [!NOTE]  
>  A causa di una limitazione di SharePoint, è possibile creare un tipo di contenuto soluzioni farm basato sul tipo di contenuto di una soluzione creata mediante sandbox.  
  
 Per altre informazioni, vedere [Procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: Tipo di contenuto](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Elemento vuoto
 *Gli elementi vuoti* vengono spesso usate per definire elementi di progetto SharePoint che non dispongono di un progetto o un modello di elemento di progetto in Visual Studio. Quando si aggiunge un elemento vuoto al progetto, un nodo denominato EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] contiene un singolo file che è denominata *Elements. Xml.* Uso [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni per definire gli elementi desiderati nel *Elements*.  
  
### <a name="event-receiver"></a>Ricevitore di eventi
 *Ricevitori di eventi* gestire gli eventi per gli elementi nel sito di SharePoint, ad esempio quando un elemento viene aggiunto a un elenco, quando viene eliminato un elemento web o quando un flusso di lavoro avviato. Il modello di elemento del progetto ricevitore di eventi ti permette di gestire  
  
- Elenco eventi  
  
- Eventi elementi elenco  
  
- Elenco eventi di posta elettronica  
  
- eventi Web  
  
- Elenco eventi di flusso di lavoro  
  
  L'elemento di progetto di ricevitore di eventi consente di creare un **ricevitore di eventi** cartella con un file di classe singola che contiene i gestori eventi per tutti gli eventi specificati quando si crea il progetto nel **personalizzazione di SharePoint Procedura guidata**. Classe del ricevitore di eventi può gestire eventi che si verificano nel sito di SharePoint quando gli elementi, ad esempio file, i campi, elementi, elenchi, allegati, le web part e flussi di lavoro vengono aggiunti, aggiornati, eliminati o rimosso. Per altre informazioni, vedere [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md) e [blocco predefinito: Gestione degli eventi](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>List  
 Un elenco è un'istanza di una base SharePoint elenco definizione riutilizzabile, ad esempio un calendario o di un elenco di attività. Dopo aver aggiunto un elenco per la soluzione, la finestra di progettazione di elenco consente di aggiungere le colonne del sito all'elenco e creare colonne elenco personalizzato. Ciò include le colonne del sito da tipi di contenuto. È possibile specificare il *vista* per un elenco, che determina le colonne che verranno visualizzati nell'elenco. Per altre informazioni, vedere [Procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: Gli elenchi e raccolte documenti](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Modulo  
 *I moduli* (non deve essere confusa con [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli) contiene file che si desidera distribuire nel server di SharePoint, ad esempio immagini o note. L'elemento di progetto del modulo contiene un **modulo** nodo. Il nodo del modulo contiene due modelli di elemento di progetto: un file di definizione XML, che agisce come un manifesto del modulo, e un *Sample. txt* file, un file segnaposto. Per altre informazioni, vedere [usare i moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md) e [moduli](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Flusso di lavoro sequenza (solo soluzione farm)
 Oggetto *flusso di lavoro sequenza* è una serie di passaggi per la logica di business, eseguite in sequenza, fino al completamento dell'ultimo passaggio. Flussi di lavoro sequenziali sono usati per gestire i processi che coinvolgono elementi quali elenchi e documenti di SharePoint. È possibile creare flussi di lavoro a livello di sito (globale) o (local) flussi di lavoro a livello di elenco e può specificare se un flusso di lavoro viene avviata automaticamente o manualmente. Questo elemento del progetto è utilizzabile solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo per soluzioni farm. Per altre informazioni, vedere [soluzioni di flusso di lavoro di SharePoint creare](../sharepoint/creating-sharepoint-workflow-solutions.md), [flussi di lavoro in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e [What ' s New: Miglioramenti del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Web part Silverlight
 *Web part Silverlight* gli elementi del progetto consentono di creare web part per SharePoint che consentono di visualizzare le applicazioni Silverlight. Quando si aggiunge questo elemento del progetto alla soluzione, è possibile scegliere se aggiungere una nuova applicazione Silverlight o fare riferimento a uno esistente in un secondo momento. Per altre informazioni, vedere [creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [procedura dettagliata: Creare una web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Colonna del sito
 Oggetto *colonne del sito*, noto anche come una *campo*, è uno degli elementi più semplici che è possibile aggiungere a un progetto SharePoint. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento di testo o il nome della città di un contatto in un elenco di contatti. Per altre informazioni, vedere [creare le colonne del sito, i tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [colonne](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Definizione di sito (solo soluzione farm)
 *Definizione sito* gli elementi di progetto contengono una cartella di definizione di sito che include i file seguenti:  
  
- Una pagina aspx di impostazione predefinita, usata come pagina web predefinita per il sito.  
  
- Un' *onet* file che definisce i componenti del sito.  
  
- Un file xml webtemp che specifica le configurazioni di definizioni di sito visualizzati nella **selezione modello** sezione il **nuovo sito di SharePoint** pagina.  
  
  Dopo aver aggiunto una definizione di sito, aggiungere codice e i file di introdurre funzionalità. Questo elemento del progetto è utilizzabile solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo per soluzioni farm. Per altre informazioni, vedere [creazione di site definitions per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [definizioni di sito e le configurazioni](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Flusso di lavoro macchina a stati (solo soluzione farm)
 Oggetto *lavoro macchina a stati* è un set di stati per la logica di business, transizioni e le azioni. La procedura descritta in un flusso di lavoro macchina non viene eseguita in sequenza. al contrario, vengono attivate da azioni e gli stati. Ad esempio un flusso di lavoro sequenza di flussi sono associati a elementi quali elenchi e documenti di SharePoint. Ancora una volta, è possibile creare flussi di lavoro (globale) a livello di sito o a livello di elenco (locale). È anche possibile selezionare se un flusso di lavoro viene avviata automaticamente o manualmente. Questo elemento del progetto è utilizzabile solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo per soluzioni farm. Per altre informazioni, vedere [soluzioni di flusso di lavoro di SharePoint creare](../sharepoint/creating-sharepoint-workflow-solutions.md), [flussi di lavoro in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e [What ' s New: Miglioramenti del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Controllo utente (solo soluzione farm)
 Oggetto *controllo utente* è un controllo personalizzato e riutilizzabile in cui è possibile aggiungere altri controlli ASP.NET e i controlli di SharePoint. Il controllo utente può essere aggiunto per le pagine dell'applicazione e le web part eseguite in SharePoint. Questo elemento del progetto è utilizzabile solo nelle soluzioni farm. È possibile aggiungere questo elemento del progetto solo per soluzioni farm. Per altre informazioni, vedere [creazione di controlli riutilizzabili per Web part o pagine applicazione](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Web part visiva
 Oggetto *web part visiva* elemento del progetto include un *Elements. XML* file di definizione, una **Web Part** elemento e un **controllo utente** elemento. È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio alla superficie del controllo utente. Per altre informazioni, vedere [Procedura: Creare una web part di SharePoint usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Web part
 Oggetto *web part* è un controllo lato server che viene eseguito all'interno di un tipo speciale di pagina detta pagina Web Part. Sono i blocchi predefiniti di pagine visualizzate in un sito di SharePoint. L'elemento web part fornisce i file che consentono di progettare una web part per un sito di SharePoint. Per altre informazioni, vedere [Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) e [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Vedere anche
 [Lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Prodotti e tecnologie SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
