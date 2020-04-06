---
title: Modelli di supporto per siti Web Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703459"
---
# <a name="web-site-support-templates"></a>Modelli di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]I modelli di progetto e di elemento del sito Web forniscono stub di progetto e di elemento di sito Web riutilizzabili e personalizzabili che accelerano il processo di sviluppo eliminando la necessità di creare nuovi progetti di sito Web ed elementi da zero. Per ulteriori [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informazioni sui modelli, vedere Creazione di modelli di [progetto e di elemento](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Cartella dei modelli di progetto
 I modelli di progetto Web vengono in genere installati in [ Percorso\\di installazione di Visual*Studio*] , Common7 , IDE , ProjectTemplates , ognuno in una sottocartella denominata in base al linguaggio di programmazione Web.

## <a name="project-file"></a>File di progetto
 L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE) richiede un'estensione di file di progetto per eseguire il mapping di un modello al tipo di progetto corretto. Poiché i progetti Web non dispongono di un file di progetto, l'estensione del file di progetto fittizio .webproj viene registrata per eseguire il mapping del modello al tipo di progetto.

 Facoltativamente, è possibile aggiungere una stringa del nome della lingua al modello, per consentire al sistema del progetto Web di impostare la lingua predefinita nella finestra di dialogo **Aggiungi nuovo elemento** per gli elementi basati sul modello. La stringa deve essere la prima riga del file. Deve corrispondere sia al nome registrato in AddItemLanguageName nella registrazione del motore IntelliSense che al nome registrato in Project Subtype(VsTemplate). Per ulteriori informazioni, vedere [Attributi di supporto del sito Web](../../extensibility/internals/web-site-support-attributes.md).

 Se la stringa non è presente, il sistema del progetto Web tenta di determinare la lingua predefinita in base all'attributo Language e alle estensioni di file delle pagine aggiunte al progetto Web dal modello di progetto.

## <a name="project-templates"></a>Modelli di progetto
 I modelli di progetto di sito Web vengono utilizzati per creare nuovi siti Web in risposta al comando **Nuovo sito Web** del menu **File.** Sono attualmente supportati tre tipi di progetto di sito Web:

- Progetti di sito Web vuoti

- Progetti di sito Web

- Progetti di servizio Web

### <a name="empty-web-site-projects"></a>Progetti di sito Web vuoti
 Questi file creano un nuovo sito Web vuoto in risposta al comando **Sito Web vuoto,** disponibile dopo aver scelto **File** > **nuovo sito Web**:

- Modello EmptyWeb.vstemplate

     File modello che guida la creazione del nuovo sito Web vuoto.

- EmptyWeb.webproj

     Questo file è un elemento del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Progetti di sito Web
 Questi file creano un nuovo sito Web in risposta al comando **ASP.NET sito Web,** disponibile dopo aver scelto **File** > **nuovo sito Web**:

- Default.aspx

     Home page predefinita per il nuovo sito Web. L'attributo Language specifica il linguaggio codebehind e l'attributo CodeFile specifica il file dipendente che contiene il codice codebehind associato a questa pagina.

- Aspx. *estensione*

     Il file dipendente che contiene il codice codebehind per la home page predefinita. Il linguaggio codebehind determina *l'estensione* di questo file.

- web.config

     File di configurazione web.site radice.

- WebApplication.vstemplate (informazioni in lingua inlingua in stato di sviluppo)

     Il file modello che determina il contenuto della soluzione del sito Web e forza la creazione della cartella App_Data.

- WebApplication.webproj

     Questo file è un elemento del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file WebApplication.vstemplate.

### <a name="web-service-projects"></a>Progetti di servizio Web
 Questi file creano un nuovo sito Web in risposta al comando **ASP.NET Servizio Web,** disponibile dopo aver scelto **File** > **nuovo sito Web**:

- Service.asmx (servizio service)

     Pagina HTML per il nuovo servizio Web. L'attributo Language specifica il linguaggio codebehind e l'attributo CodeBehind specifica il file dipendente che contiene il codice codebehind associato a questo servizio.

- Service. *Estensione*

     File dipendente che implementa la classe del servizio. Il linguaggio codebehind determina *l'estensione* di questo file.

- web.config

- File di configurazione web.site radice.

- WebService.vstemplate (informazioni in lingua inlingua in stato di <a0

     Il file modello che determina il contenuto della soluzione del sito Web e impone la creazione delle cartelle App_Data e App_Code. Il servizio. *file* di estensione viene copiato nella cartella App_Code.

- WebService.webproj

     Questo file è un elemento del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file WebService.vstemplate.

## <a name="project-item-template-folder"></a>Cartella modello di elemento di progettoProject Item Template Folder
 I modelli di elemento di progetto Web vengono in genere installati in [*Percorso di installazione*di Visual Studio ] , Common7 , IDE , ItemTemplates , in una sottocartella denominata in base al relativo linguaggio di programmazione Web.\\

## <a name="project-item-templates"></a>Modelli di elemento di progettoProject Item Templates
 I modelli di elemento di progetto di sito Web vengono utilizzati per aggiungere nuove pagine Web a un sito Web in risposta al comando **Aggiungi elemento esistente.** Questi tipi di pagine Web sono attualmente supportati:

- Nuova classe

- Nuova pagina HTML

- Nuovo modulo Web

- Nuova pagina master

### <a name="new-class"></a>Nuova classe
 Questo modello crea un nuovo file di origine che definisce una classe vuota in risposta al comando **Aggiungi nuova classe.**

- Class. *Estensione*

     File di origine che implementa la classe vuota. Il linguaggio codebehind determina *l'estensione* di questo file.

- Class.vstemplate (modello)

     File modello che crea il file di origine e ne determina il contenuto.

### <a name="new-html-page"></a>Nuova pagina HTML
 Questo modello crea una nuova pagina Web in risposta al comando **Aggiungi nuova pagina HTML.**

- HTMLPage.htm

     Contenuto iniziale della pagina Web. A questa pagina Web non è in genere associato alcun file dipendente codebehind. Per creare una pagina intelligente con un file codebehind associato, utilizzare invece il modello Web Form.

- HTMLPage.vstemplate (informazioni in lingua inlingua in lingua senza estensione)

     File modello che crea la pagina Web e ne determina il contenuto.

### <a name="new-webform"></a>Nuovo WebForm
 Questo modello crea una nuova pagina Web intelligente in risposta al comando **Aggiungi nuovo Web Form.**

 Per creare un file di origine codebehind dipendente, selezionare **Inserisci codice in un file separato.** In caso contrario, viene creata una singola \<pagina Web con un blocco di script vuoto e nessuna direttiva % di pagina % > per associare un file dipendente.

 Per creare una pagina di contenuto per una pagina master selezionata, selezionate **Seleziona pagina master**.

- WebForm.aspx

     Contenuto iniziale della pagina Web. Alla pagina Web non è associato alcun file dipendente codebehind.

- WebForm_cb.aspx

     Contenuto iniziale della pagina Web. A questa pagina Web è associato un file dipendente codebehind.

- Codebehind. *Estensione*

     File dipendente che implementa la classe webform. Il linguaggio codebehind determina *l'estensione* di questo file.

- ContentPage.aspx

     Contenuto iniziale della pagina Web come pagina di contenuto. Alla pagina Web non è associato alcun file dipendente codebehind.

- ContentPage_cb.aspx

     Contenuto iniziale della pagina Web come pagina di contenuto. A questa pagina Web è associato un file dipendente codebehind.

- WebForm.vstemplate

     Il file modello che determina il contenuto della nuova pagina Web e il relativo file dipendente, se presente.

### <a name="new-master-page"></a>Nuova pagina master
 Questo modello crea una nuova pagina master in risposta al comando **Aggiungi nuova pagina master.**

 Per creare un file di origine codebehind dipendente, selezionare **Inserisci codice in un file separato.** In caso contrario, viene creata una singola \<pagina Web con un blocco di script vuoto e nessuna direttiva % % di pagina % > per associare un file dipendente.

- Pagina MasterPage.master

     Contenuto iniziale della pagina master. Questa pagina master non ha alcun file dipendente codebehind associato.

- MasterPage_cb.master

     Contenuto iniziale della pagina master. A questa pagina master è associato un file dipendente codebehind.

- Codebehind. *estensione*

     File dipendente che implementa la classe della pagina master. Il linguaggio codebehind determina *l'estensione* di questo file.

- MasterPage.vstemplate

     File modello che determina il contenuto della nuova pagina master e del relativo file dipendente, se presente.

## <a name="see-also"></a>Vedere anche
- [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
