---
title: Modelli di supporto di siti Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c22cbb5ca39e48e488851f26786955c9704fda
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961598"
---
# <a name="web-site-support-templates"></a>Modelli di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] I modelli di progetto ed elemento di sito Web forniscono gli stub progetti ed elementi riutilizzabili e personalizzabili sito Web che permettono di velocizzare il processo di sviluppo, eliminando la necessità di creare nuovi progetti di siti Web e gli elementi da zero. Per ulteriori informazioni sul [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelli, vedere [creazione Project and Item Templates](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Cartella dei modelli di progetto
 Modelli di progetto Web vengono in genere installati in [*percorso di installazione di Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, ciascuno di essi in una sottocartella denominata dopo il linguaggio di programmazione web.

## <a name="project-file"></a>File di progetto
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) richiede un'estensione di file di progetto come un modo per eseguire il mapping di un modello per il tipo di progetto corretto. Poiché i progetti Web non è un file di progetto, è registrato il webproj estensione file di progetto fittizio per eseguire il mapping del modello per il tipo di progetto.

 Facoltativamente, una stringa del nome della lingua può essere aggiunto al modello, per abilitare il sistema di progetto Web impostare la lingua predefinita **Aggiungi nuovo elemento** finestra di dialogo per gli elementi in base al modello. La stringa deve essere la prima riga del file. Deve corrispondere al nome registrato in AddItemLanguageName nella registrazione del motore di IntelliSense e il nome registrato nel progetto Subtype(VsTemplate). Per altre informazioni, vedere [attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md).

 Se la stringa non è presente, il sistema del progetto Web tenta di determinare la lingua predefinita dipendono dalle estensioni di file attributi e linguaggio delle pagine aggiunte al progetto Web dal modello di progetto.

## <a name="project-templates"></a>Modelli di progetto
 Modelli di progetto sito Web vengono utilizzati per creare nuovi siti Web in risposta al **nuovo sito Web** comando le **File** menu. Attualmente sono supportati tre tipi di progetto di sito Web:

-   Progetti di sito Web vuoto

-   Progetti di siti Web

-   Progetti di servizi Web

### <a name="empty-web-site-projects"></a>Progetti di sito Web vuoto
 Questi file creano un nuovo sito Web vuoto in risposta al **sito Web vuoto** comando, che è disponibile dopo aver scelto **File** > **nuovo sito Web**:

-   EmptyWeb.vstemplate

     Il file di modello che descrive la creazione del nuovo sito Web vuoto.

-   EmptyWeb.webproj

     Questo file è un elemento del sistema del modello di progetto. Il riferimento al file di progetto nel file EmptyWeb.vstemplate soddisfa.

### <a name="web-site-projects"></a>Progetti di siti Web
 Questi file creano un nuovo sito Web in risposta al **sito Web ASP.NET** comando, che è disponibile dopo aver scelto **File** > **nuovo sito Web**:

-   Default.aspx

     La home page predefinita per il nuovo sito Web. L'attributo della lingua specifica la lingua di codebehind e l'attributo CodeFile specifica il file dipendente che contiene il codice di codebehind associato a questa pagina.

-   Default. aspx. *estensione*

     Il file dipendente che contiene il codice sottostante per la home page predefinita. La lingua di codebehind determina la *estensione* di questo file.

-   web.config

     Il file di configurazione web.site radice.

-   WebApplication.vstemplate

     Il file di modello che determina il contenuto della soluzione di siti Web e forza la creazione della cartella App_Data.

-   WebApplication.webproj

     Questo file è un elemento del sistema del modello di progetto. Il riferimento al file di progetto nel file WebApplication.vstemplate soddisfa.

### <a name="web-service-projects"></a>Progetti di servizi Web
 Questi file creano un nuovo sito Web in risposta al **servizio Web ASP.NET** comando, che è disponibile dopo aver scelto **File** > **nuovo sito Web**:

-   Service.asmx

     La pagina HTML per il nuovo servizio Web. L'attributo della lingua specifica la lingua di codebehind e l'attributo CodeBehind specifica il file dipendente che contiene il codice di codebehind associato al servizio.

-   Servizio. *extension*

     Il file dipendente che implementa la classe del servizio. La lingua di codebehind determina la *estensione* di questo file.

-   web.config

-   Il file di configurazione web.site radice.

-   WebService.vstemplate

     Il file di modello che determina il contenuto della soluzione di siti Web e forza la creazione delle cartelle App_Data e App_Code. Il servizio. *estensione* file viene copiato nella cartella App_Code.

-   WebService.webproj

     Questo file è un elemento del sistema del modello di progetto. Il riferimento al file di progetto nel file WebService.vstemplate soddisfa.

## <a name="project-item-template-folder"></a>Cartella del modello di elemento di progetto
 Modelli di elemento di progetto Web vengono in genere installati [*percorso di installazione di Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, ciascuno di essi in una sottocartella denominata dopo il relativo linguaggio di programmazione web.

## <a name="project-item-templates"></a>I modelli di progetto
 I modelli di progetto sito Web consentono di aggiungere nuove pagine Web a un sito Web in risposta al **Aggiungi elemento esistente** comando. Questi tipi di pagine Web sono attualmente supportati:

-   Nuova classe

-   Nuova pagina HTML

-   Nuovo modulo Web

-   Nuova pagina master

### <a name="new-class"></a>Nuova classe
 Questo modello crea un nuovo file di origine che definisce una classe vuota in risposta al **Aggiungi una nuova classe** comando.

-   Class. *extension*

     File di origine che implementa la classe vuota. La lingua di codebehind determina la *estensione* di questo file.

-   Class.vstemplate

     Il file di modello che crea il file di origine e determina il relativo contenuto.

### <a name="new-html-page"></a>Nuova pagina HTML
 Questo modello crea una nuova pagina Web in risposta al **Aggiungi nuova pagina HTML** comando.

-   HTMLPage.htm

     Il contenuto inizio della pagina Web. Questa pagina Web non include in genere alcun file dipendente codebehind associato. Per creare una pagina intelligente con un file codebehind associati, usare invece il modello Web Form.

-   HTMLPage.vstemplate

     Il file di modello che crea la pagina Web e determina il relativo contenuto.

### <a name="new-webform"></a>Nuovo Web Form
 Questo modello crea una nuova pagina Web smart in risposta al **Aggiungi nuovo Web Form** comando.

 Per creare un file di origine dipendente codebehind, selezionare **Inserisci codice in file separati**. In caso contrario, una singola pagina Web viene creata con un blocco di script vuoto e nessun \<% % pagina > direttive per associare un file dipendente.

 Per creare una pagina di contenuto per una pagina master selezionata, selezionare **Seleziona pagina master**.

-   WebForm.aspx

     Il contenuto inizio della pagina Web. Questa pagina Web non dispone di alcun file dipendente codebehind associato.

-   WebForm_cb.aspx

     Il contenuto inizio della pagina Web. Questa pagina Web è un file dipendente codebehind associato.

-   Codebehind. *extension*

     Il file dipendente che implementa la classe di Web Form. La lingua di codebehind determina la *estensione* di questo file.

-   ContentPage.aspx

     Il contenuto inizio della pagina Web come una pagina di contenuto. Questa pagina Web non dispone di alcun file dipendente codebehind associato.

-   ContentPage_cb.aspx

     Il contenuto inizio della pagina Web come una pagina di contenuto. Questa pagina Web è un file dipendente codebehind associato.

-   WebForm.vstemplate

     Il file di modello che determina il contenuto della nuova pagina web e il file dei dipendenti, se presente.

### <a name="new-master-page"></a>Nuova pagina Master
 Questo modello crea una nuova pagina master in risposta al **Aggiungi pagina Master** comando.

 Per creare un file di origine dipendente codebehind, selezionare **Inserisci codice in file separati**. In caso contrario, una singola pagina Web viene creata con un blocco di script vuoto e nessun \<% % pagina > direttive per associare un file dipendente.

-   MasterPage.master

     Il contenuto inizio della pagina master. Questa pagina master non include alcun file dipendente codebehind associato.

-   MasterPage_cb.master

     Il contenuto inizio della pagina master. Questa pagina master è un file dipendente codebehind associato.

-   Codebehind.*extension*

     Il file dipendente che implementa la classe di pagina master. La lingua di codebehind determina la *estensione* di questo file.

-   MasterPage.vstemplate

     Il file di modello che determina il contenuto della nuova pagina master e il file dei dipendenti, se presente.

## <a name="see-also"></a>Vedere anche
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)