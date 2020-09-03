---
title: Modelli di supporto per siti Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dca7768f31219328648d457d188086e0185e2ffc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200970"
---
# <a name="web-site-support-templates"></a>Modelli di supporto per siti Web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] I modelli di progetto e di elemento del sito Web forniscono stub di elementi e progetti di siti Web riutilizzabili e personalizzabili che accelerano il processo di sviluppo eliminando la necessità di creare nuovi progetti ed elementi di siti Web da zero. Per ulteriori informazioni sui [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modelli, vedere [creazione di modelli di progetti e di elementi](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Cartella del modello di progetto  
 I modelli di modello di progetto Web vengono in genere installati in [*percorso di installazione di Visual Studio*] \Common7\IDE\ProjectTemplates\Web \\ , ognuno in una sottocartella denominata dopo il linguaggio di programmazione Web.  
  
## <a name="project-file"></a>File di progetto  
 Per eseguire il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mapping di un modello al tipo di progetto corretto, il Integrated Development Environment (IDE) richiede un'estensione del file di progetto. Poiché i progetti Web non dispongono di un file di progetto, l'estensione del file di progetto fittizio. webproj è registrata per supportare questa operazione.  
  
 Facoltativamente, è possibile aggiungere una stringa del nome del linguaggio al modello per consentire al sistema del progetto Web di impostare l'impostazione predefinita della lingua nella finestra di dialogo **Aggiungi nuovo elemento** per gli elementi in base al modello. La stringa deve essere la prima riga del file e deve corrispondere al nome registrato in AddItemLanguageName nella registrazione del motore di IntelliSense e al nome registrato nel sottotipo di progetto (VsTemplate). Per ulteriori informazioni, vedere [attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md).  
  
 Se la stringa non è presente, il sistema del progetto Web tenterà di determinare la lingua predefinita in base all'attributo del linguaggio e alle estensioni di file delle pagine aggiunte al progetto Web dal modello di modello di progetto.  
  
## <a name="project-templates"></a>Modelli di progetto  
 I modelli di progetto di sito Web vengono utilizzati per creare nuovi siti Web in risposta al **nuovo comando sito Web** nel menu **file** . Sono attualmente supportati tre tipi di progetto di sito Web:  
  
- Progetti di siti Web vuoti  
  
- Progetti di siti Web  
  
- Progetti di servizi Web  
  
### <a name="empty-web-site-projects"></a>Progetti di siti Web vuoti  
 Questi file creano un nuovo sito Web vuoto in risposta al comando **sito Web vuoto** , disponibile dopo aver puntato a **nuovo sito Web** dal menu **file** :  
  
- EmptyWeb. vstemplate  
  
     File modello che guida la creazione del nuovo sito Web vuoto.  
  
- EmptyWeb. webproj  
  
     Questo file è un elemento del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file EmptyWeb. vstemplate.  
  
### <a name="web-site-projects"></a>Progetti di siti Web  
 Questi file creano un nuovo sito Web in risposta al comando **sito web ASP.NET** , disponibile dopo aver puntato a **nuovo sito Web** dal menu **file** :  
  
- Default.aspx  
  
     Home page predefinito per il nuovo sito Web. L'attributo Language specifica il linguaggio codebehind e l'attributo CodeFile specifica il file dipendente che contiene il codice codebehind associato a questa pagina.  
  
- Default. aspx. *estensione* di  
  
     Il file dipendente che contiene il codice codebehind per la home page predefinita. Il linguaggio codebehind determina l' *estensione* del file.  
  
- web.config  
  
     File di configurazione Web. site radice.  
  
- WebApplication. vstemplate  
  
     Il file modello che determina il contenuto della soluzione del sito Web e impone la creazione della cartella App_Data.  
  
- WebApplication. webproj  
  
     Questo file è un elemento del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file WebApplication. vstemplate.  
  
### <a name="web-service-projects"></a>Progetti di servizi Web  
 Questi file creano un nuovo sito Web in risposta al comando del **servizio Web ASP.NET** , disponibile dopo aver puntato a **nuovo sito Web** dal menu **file** :  
  
- Service. asmx  
  
     Pagina HTML per il nuovo servizio Web. L'attributo Language specifica il linguaggio codebehind e l'attributo CodeBehind specifica il file dipendente che contiene il codice codebehind associato a questo servizio.  
  
- Service. *extension*  
  
     File dipendente che implementa la classe del servizio. Il linguaggio codebehind determina l' *estensione* del file.  
  
- web.config  
  
- File di configurazione Web. site radice.  
  
- WebService. vstemplate  
  
     Il file modello che determina il contenuto della soluzione del sito Web e impone la creazione delle cartelle App_Data e App_Code. Il servizio. il file di *estensione* viene copiato nella cartella App_Code.  
  
- WebService. webproj  
  
     Questo file è un elemento del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file WebService. vstemplate.  
  
## <a name="project-item-template-folder"></a>Cartella del modello di elemento di progetto  
 I modelli di modello di elemento di progetto Web sono in genere installati in [*percorso di installazione di Visual Studio*] \Common7\IDE\ItemTemplates\Web \\ , ognuno in una sottocartella denominata dopo il linguaggio di programmazione Web.  
  
## <a name="project-item-templates"></a>Modelli di elementi di progetto  
 I modelli di elemento del progetto del sito Web vengono utilizzati per aggiungere nuove pagine Web a un sito Web in risposta al comando **Aggiungi elemento esistente** . Attualmente sono supportati questi tipi di pagine Web:  
  
- Nuova classe  
  
- Nuova pagina HTML  
  
- Nuovo Web Form  
  
- Nuova pagina master  
  
### <a name="new-class"></a>Nuova classe  
 Questo modello consente di creare un nuovo file di origine che definisce una classe vuota in risposta al comando **Aggiungi nuova classe** .  
  
- Class. *extension*  
  
     Il file di origine che implementa la classe vuota. Il linguaggio codebehind determina l' *estensione* del file.  
  
- Classe. vstemplate  
  
     Il file modello che crea il file di origine e ne determina il contenuto.  
  
### <a name="new-html-page"></a>Nuova pagina HTML  
 Questo modello consente di creare una nuova pagina Web in risposta al comando **Aggiungi nuova pagina HTML** .  
  
- HTMLPage.htm  
  
     Contenuto iniziale della pagina Web. Questa pagina Web non dispone in genere di un file dipendente codebehind associato. Per creare una pagina intelligente con un file codebehind associato, utilizzare invece il modello Web Form.  
  
- Pagina HTML. vstemplate  
  
     Il file modello che crea la pagina Web e ne determina il contenuto.  
  
### <a name="new-webform"></a>Nuovo Web Form  
 Questo modello consente di creare una nuova pagina Web intelligente in risposta al comando **Aggiungi nuovo modulo Web** .  
  
 Per creare un file di origine codebehind dipendente, selezionare **Inserisci codice in un file separato**. In caso contrario, viene creata un'unica pagina Web con un blocco di scripting vuoto e nessuna \<% Page %> direttiva per associare un file dipendente.  
  
 Per creare una pagina di contenuto per una pagina master selezionata, selezionare **Seleziona pagina master**.  
  
- WebForm. aspx  
  
     Contenuto iniziale della pagina Web. A questa pagina Web non è associato alcun file dipendente codebehind.  
  
- WebForm_cb. aspx  
  
     Contenuto iniziale della pagina Web. A questa pagina Web è associato un file dipendente codebehind.  
  
- Codebehind. *extension*  
  
     File dipendente che implementa la classe WebForm. Il linguaggio codebehind determina l' *estensione* del file.  
  
- ContentPage. aspx  
  
     Contenuto iniziale della pagina Web come pagina di contenuto. A questa pagina Web non è associato alcun file dipendente codebehind.  
  
- ContentPage_cb. aspx  
  
     Contenuto iniziale della pagina Web come pagina di contenuto. A questa pagina Web è associato un file dipendente codebehind.  
  
- Web Form. vstemplate  
  
     File modello che determina il contenuto della nuova pagina Web e del relativo file dipendente, se presente.  
  
### <a name="new-master-page"></a>Nuova pagina master  
 Questo modello consente di creare una nuova pagina master in risposta al comando **Aggiungi nuova pagina master** .  
  
 Per creare un file di origine codebehind dipendente, selezionare **Inserisci codice in un file separato**. In caso contrario, viene creata un'unica pagina Web con un blocco di scripting vuoto e nessuna \<% Page %> direttiva per associare un file dipendente.  
  
- MasterPage. master  
  
     Contenuto iniziale della pagina master. A questa pagina master non è associato alcun file dipendente codebehind.  
  
- MasterPage_cb. master  
  
     Contenuto iniziale della pagina master. A questa pagina master è associato un file dipendente codebehind.  
  
- Codebehind. *estensione* di  
  
     File dipendente che implementa la classe della pagina master. Il linguaggio codebehind determina l' *estensione* del file.  
  
- MasterPage. vstemplate  
  
     File modello che determina il contenuto della nuova pagina master e del relativo file dipendente, se presente.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
