---
title: Modelli di supporto per siti Web | Microsoft Docs
description: Informazioni sui modelli di supporto del sito Web. Visual Studio modelli di progetto e di elemento del sito Web forniscono stub di progetti e elementi del sito Web riutilizzabili e personalizzabili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6480b21cc4907e45b174b69418f1d10177f36440597949fd8a1806246016dc27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414155"
---
# <a name="web-site-support-templates"></a>Modelli di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] I modelli di progetto e di elemento del sito Web forniscono stub di progetti ed elementi del sito Web riutilizzabili e personalizzabili che accelerano il processo di sviluppo eliminando la necessità di creare nuovi progetti ed elementi di siti Web da zero. Per altre informazioni sui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelli, vedere [Creating Project and Item Templates](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Project Cartella modello
 I modelli di progetto Web vengono in genere installati in [*Visual Studio Installation Path*]\Common7\IDE\ProjectTemplates\Web , ognuno in una sottocartella denominata in base al linguaggio di programmazione \\ Web.

## <a name="project-file"></a>File di progetto
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'ambiente di sviluppo integrato (IDE) richiede un'estensione di file di progetto per eseguire il mapping di un modello al tipo di progetto corretto. Poiché i progetti Web non hanno un file di progetto, l'estensione di file di progetto fittizia .webproj viene registrata per eseguire il mapping del modello al tipo di progetto.

 Facoltativamente, è possibile aggiungere una stringa del nome di lingua al modello per  consentire al sistema del progetto Web di impostare il valore predefinito della lingua nella finestra di dialogo Aggiungi nuovo elemento per gli elementi basati sul modello. La stringa deve essere la prima riga del file. Deve corrispondere sia al nome registrato in AddItemLanguageName nella registrazione del motore IntelliSense che al nome registrato in Project Subtype(VsTemplate). Per altre informazioni, vedere [Attributi di supporto del sito Web.](../../extensibility/internals/web-site-support-attributes.md)

 Se la stringa non è presente, il sistema del progetto Web tenta di determinare la lingua predefinita in base all'attributo Language e alle estensioni di file delle pagine aggiunte al progetto Web dal modello Project.

## <a name="project-templates"></a>Modelli di progetto
 I modelli di progetto di sito Web vengono usati per compilare nuovi siti Web in risposta al **comando Nuovo sito Web** del menu **File** . Sono attualmente supportati tre tipi di progetto di sito Web:

- Progetti di siti Web vuoti

- Progetti di siti Web

- Progetti di servizio Web

### <a name="empty-web-site-projects"></a>Progetti di siti Web vuoti
 Questi file creano un nuovo sito Web vuoto in risposta al comando **Sito Web** vuoto, disponibile dopo aver **scelto File** New Web Site  >  **(File nuovo sito Web):**

- EmptyWeb.vstemplate

     File modello che guida la creazione del nuovo sito Web vuoto.

- EmptyWeb.webproj

     Questo file è un artefatto del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Progetti di sito Web
 Questi file creano un nuovo sito Web in risposta al comando **ASP.NET Sito Web,** disponibile dopo aver **scelto File** New Web  >  **Site (Nuovo sito Web):**

- Default.aspx

     Valore predefinito home page per il nuovo sito Web. L'attributo Language specifica il linguaggio codebehind e l'attributo CodeFile specifica il file dipendente che contiene il codice codebehind associato a questa pagina.

- Aspx. *estensione*

     File dipendente che contiene il codice codebehind per l'oggetto home page. Il linguaggio codebehind determina *l'estensione* di questo file.

- web.config

     File di configurazione web.site radice.

- WebApplication.vstemplate

     File modello che determina il contenuto della soluzione del sito Web e forza la creazione della App_Data cartella.

- WebApplication.webproj

     Questo file è un artefatto del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file WebApplication.vstemplate.

### <a name="web-service-projects"></a>Progetti di servizio Web
 Questi file creano un nuovo sito Web in risposta al comando **servizio Web ASP.NET,** disponibile dopo aver **scelto File** New Web Site  >  **(File nuovo sito Web):**

- Service.asmx

     Pagina HTML per il nuovo servizio Web. L'attributo Language specifica il linguaggio codebehind e l'attributo CodeBehind specifica il file dipendente che contiene il codice codebehind associato a questo servizio.

- Service. *extension*

     File dipendente che implementa la classe del servizio. Il linguaggio codebehind determina *l'estensione* di questo file.

- web.config

- File di configurazione web.site radice.

- WebService.vstemplate

     File modello che determina il contenuto della soluzione del sito Web e forza la creazione delle App_Data e App_Code web. Servizio. *il* file di estensione viene copiato nella App_Code cartella .

- WebService.webproj

     Questo file è un artefatto del sistema di modelli di progetto. Soddisfa il riferimento al file di progetto nel file WebService.vstemplate.

## <a name="project-item-template-folder"></a>Project Cartella del modello di elemento
 I modelli di elemento di progetto Web vengono in genere installati in [ percorso di installazione di *Visual Studio*]\Common7\IDE\ItemTemplates\Web , ognuno in una sottocartella denominata in base al linguaggio di programmazione \\ Web.

## <a name="project-item-templates"></a>Project Modelli di elemento
 I modelli di elemento del progetto di sito Web vengono usati per aggiungere nuove pagine Web a un sito Web in risposta al **comando Aggiungi elemento** esistente. Questi tipi di pagine Web sono attualmente supportati:

- Nuova classe

- Nuova pagina HTML

- Nuovo Web Form

- Nuova pagina master

### <a name="new-class"></a>Nuova classe
 Questo modello crea un nuovo file di origine che definisce una classe vuota in risposta al **comando Aggiungi nuova** classe.

- Class. *extension*

     File di origine che implementa la classe vuota. Il linguaggio codebehind determina *l'estensione* di questo file.

- Class.vstemplate

     File modello che crea il file di origine e ne determina il contenuto.

### <a name="new-html-page"></a>Nuova pagina HTML
 Questo modello crea una nuova pagina Web in risposta al **comando Aggiungi nuova pagina HTML.**

- HTMLPage.htm

     Contenuto iniziale della pagina Web. A questa pagina Web non è in genere associato alcun file dipendente da codebehind. Per creare una smart page con un file codebehind associato, usare invece il modello Web Form.

- HTMLPage.vstemplate

     File modello che crea la pagina Web e ne determina il contenuto.

### <a name="new-webform"></a>Nuovo WebForm
 Questo modello crea una nuova pagina Web intelligente in risposta al **comando Aggiungi nuovo Web Form.**

 Per creare un file di origine codebehind dipendente, selezionare **Inserisci codice in un file separato.** In caso contrario, viene creata una singola pagina Web con un blocco di scripting vuoto e nessuna \<% Page %> direttiva per associare un file dipendente.

 Per creare una pagina di contenuto per una pagina master selezionata, selezionare **Seleziona pagina master**.

- WebForm.aspx

     Contenuto iniziale della pagina Web. A questa pagina Web non è associato alcun file dipendente da codebehind.

- WebForm_cb.aspx

     Contenuto iniziale della pagina Web. A questa pagina Web è associato un file dipendente da codebehind.

- Codebehind. *extension*

     File dipendente che implementa la classe webform. Il linguaggio codebehind determina *l'estensione* di questo file.

- ContentPage.aspx

     Contenuto iniziale della pagina Web come pagina di contenuto. A questa pagina Web non è associato alcun file dipendente da codebehind.

- ContentPage_cb.aspx

     Contenuto iniziale della pagina Web come pagina di contenuto. A questa pagina Web è associato un file dipendente da codebehind.

- WebForm.vstemplate

     File modello che determina il contenuto della nuova pagina Web e il relativo file dipendente, se presente.

### <a name="new-master-page"></a>Nuova pagina master
 Questo modello crea una nuova pagina master in risposta al **comando Aggiungi nuova pagina** master.

 Per creare un file di origine codebehind dipendente, selezionare **Inserisci codice in un file separato.** In caso contrario, viene creata una singola pagina Web con un blocco di scripting vuoto e nessuna direttiva per \<% Page %> associare un file dipendente.

- MasterPage.master

     Contenuto iniziale della pagina master. A questa pagina master non è associato alcun file dipendente codebehind.

- MasterPage_cb.master

     Contenuto iniziale della pagina master. A questa pagina master è associato un file dipendente da codebehind.

- Codebehind. *estensione*

     File dipendente che implementa la classe della pagina master. Il linguaggio codebehind determina *l'estensione* di questo file.

- MasterPage.vstemplate

     File modello che determina il contenuto della nuova pagina master e il relativo file dipendente, se presente.

## <a name="see-also"></a>Vedi anche
- [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
