---
title: Creazione di Web part per SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eff779f70cb5b17d03befddce971a4bbb15ca142
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865885"
---
# <a name="create-web-parts-for-sharepoint"></a>Creazione di web part per SharePoint
  Utilizzando le web part, è possibile modificare il contenuto, l'aspetto e comportamento delle pagine di un sito di SharePoint utilizzando un browser. Web part sono controlli sul lato server che vengono eseguiti all'interno di una web part page: sono i blocchi predefiniti di pagine visualizzate in un sito di SharePoint. Vedere [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 È possibile creare ed eseguire il debug di web part in un sito di SharePoint utilizzando i modelli di Visual Studio.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Creare una web part in Visual Studio
 Creare una web part aggiungendo un **Web Part** elemento a qualsiasi progetto SharePoint. È possibile usare una **Web Part** elemento in una soluzione creata mediante sandbox o una soluzione farm.  
  
 Se si desidera progettare visivamente una web part tramite una finestra di progettazione, creare un **Web Part visiva** del progetto oppure aggiungere **Web Part visiva** elemento a qualsiasi progetto SharePoint. È possibile usare una **Web Part visiva** articolo in solo una soluzione farm.  
  
### <a name="web-part-item"></a>Elemento Web part
 Oggetto **Web Part** elemento fornisce i file che è possibile utilizzare per progettare una web part per un sito di SharePoint. Quando si aggiunge un **Web Part** item, Visual Studio crea una cartella nel progetto e quindi vengono aggiunti alcuni file nella cartella. La tabella seguente descrive ogni file.  
  
|File|Descrizione|  
|----------|-----------------|  
|*Elements.xml*|Contiene informazioni che usa il file di definizione di funzionalità nel progetto per distribuire la web part.|  
|file con estensione WebPart|Vengono fornite informazioni richieste da SharePoint per visualizzare la web part in una raccolta web part.|  
|File di codice|Contiene metodi che aggiungono controlli alla web part e generano contenuto personalizzato all'interno della web part.|  
  
 Per altre informazioni, vedere [Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Elemento web part visiva
 Una web part visiva è una web part creati usando la finestra di progettazione di Visual Web Developer in Visual Studio. Una web part visiva funziona esattamente come qualsiasi altra web part. Per aggiungere controlli, quali pulsanti e caselle di testo a una web part, aggiungere codice in un file XML. Tuttavia, si aggiungere controlli a una web part visiva trascinando o copiandoli nella web part da Visual Studio **casella degli strumenti**. La finestra di progettazione genera quindi il codice richiesto nel file XML. Vedere [Procedura: Creare web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Controlli di SharePoint
 Visual Studio fornisce alcuni controlli per la creazione di pagine di SharePoint, ad esempio le pagine dell'applicazione. Questi controlli vengono visualizzati nei **casella degli strumenti** sotto **controlli di SharePoint**. La funzionalità per questi controlli deriva dal [WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) dello spazio dei nomi, che contiene i controlli server ASP.NET utilizzati nelle pagine di siti ed elenchi di SharePoint.  
  
|Nome controllo|Descrizione|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Inserisce un menu ASP. Per altre informazioni, vedere [Cenni preliminari sul controllo Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Inserisce un **LINK** elemento nel *aspx* pagina e si applica uno o più fogli di stile esterni definiti da **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Inserisce un controllo DateTime nel *aspx* pagina.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Inserisce una convalida di sicurezza nel *aspx* pagina|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Restituisce una proprietà di un elenco specificato.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Restituisce una proprietà globale del sito Web corrente.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Inserisce un collegamento a un feed RSS nella *aspx* pagina.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fornisce proprietà e metodi per registrare le risorse, ad esempio script, in una pagina in modo che possano essere richieste quando viene eseguito il rendering della pagina.|  
|[Tema](http://go.microsoft.com/fwlink/?LinkId=235314)|Si applica un tema per il *aspx* pagina.|  
  
## <a name="debug-a-web-part"></a>Eseguire il debug di una web part
 È possibile eseguire il debug di un progetto SharePoint contenente una web part procedendo come altri progetti di Visual Studio. Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.  
  
 Per avviare il debug del codice, aggiungere la web part a una pagina web part in SharePoint.  
  
 Per altre informazioni su come eseguire il debug di progetti SharePoint, vedere [risolvere i problemi di SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Limitazioni della Visual web part
 A partire da Visual Studio, è possibile aggiungere web part visive per soluzioni di SharePoint in modalità sandbox e soluzioni farm. Tuttavia, le web part visive hanno le limitazioni seguenti:  
  
- Web part visive non supportano parametri sostituibili. Per altre informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
- Controlli utente o le web part visive non può essere trascinata ed eliminate o sono state copiate su web part visive. Questa azione causa un errore di compilazione.  
  
- Web part visive non supportano direttamente i token di SharePoint server, ad esempio $SPUrl. Per altre informazioni, vedere "Token limitazioni in modalità sandbox Web part visive" nell'argomento [risolvere i problemi di SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
- Web part visive in una soluzione creata mediante sandbox ricevono occasionalmente l'errore, "la richiesta di esecuzione di codice in modalità sandbox è stata rifiutata perché il relativo servizio Host era troppo occupato per gestire la richiesta". Per altre informazioni su questo errore, vedere il post nel [blog del Team di SharePoint per gli sviluppatori](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
- Debug di JavaScript lato server non è supportato in Visual Studio, ma è supportato il debug di JavaScript lato client.  
  
   Sebbene sia possibile aggiungere JavaScript inline per un file di markup lato server, il debug non è supportato per i punti di interruzione aggiunti al markup. Per eseguire il debug JavaScript, fare riferimento a un file JavaScript esterno nel file di markup e quindi impostare i punti di interruzione nel file JavaScript.  
  
- Debug di codice inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] codice deve essere eseguito nel file di codice generato anziché nel file di markup.  
  
- Web part visive non supportano l'uso del `<@ Assembly Src=` direttiva.  
  
- I controlli e alcuni web di SharePoint [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] controlli non sono supportati nell'ambiente sandbox di SharePoint. Se i controlli non supportati vengono utilizzati in una web part visiva in una soluzione creata mediante sandbox, l'errore, viene visualizzato "Il nome tipo o spazio dei nomi 'Theme' non esiste nello spazio dei nomi 'WebControls'".  
  
  Per altre informazioni sulle soluzioni create mediante sandbox, vedere [differenze tra modalità sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Crea stile meno recente web part basate su SharePoint
 È possibile usare i modelli in Visual Studio per creare personalizzato [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web part per SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web part vengono compilate in cima il [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastruttura delle web part e corrispondono al tipo consigliato per i nuovi progetti.  
  
 In pochissimi casi, potrebbe essere necessario creare una web part utilizzando la web part basata su SharePoint nello stile precedente. È possibile usare Visual Studio per creare questi tipi di web part, ma Visual Studio non fornisce alcun modello progettate appositamente per consentirvi di crearli.  
  
 Per altre informazioni su quando si potrebbe desiderare di creare una web part basata su SharePoint nello stile meno recente, vedere [infrastruttura delle Web Part in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Per altre informazioni su come creare una web part utilizzando la web part basata su SharePoint nello stile meno recente, vedere [scenario: creazione di una Web Part di SharePoint base](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Argomenti correlati
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Illustra come creare web part per pagine di SharePoint.|  
|[Procedura: Creare una web part di SharePoint usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Illustra come creare web part per SharePoint usando una superficie di progettazione visiva.|  
|[Procedura: Creare un controllo utente per una parte di pagina o web dell'applicazione SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Illustra come creare controlli personalizzati riutilizzabili che possono essere utilizzati dalle pagine dell'applicazione e dalle web part eseguite in SharePoint.|  
|[Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint.|  
|[Procedura dettagliata: Creare una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Viene descritto come progettare una web part per SharePoint trascinando i controlli in un'area di progettazione visiva.|  
|[Procedura dettagliata: Creare web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint che ospita un'applicazione Silverlight e visualizza i dati dagli elenchi di SharePoint.|  
