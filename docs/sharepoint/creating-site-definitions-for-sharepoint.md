---
title: Creazione di definizioni di sito per SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66e3566b7bfabb7ec2049632937beaa697246403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868326"
---
# <a name="create-site-definitions-for-sharepoint"></a>Creare definizioni di sito per SharePoint
  Il progetto di definizione del sito di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ti permette di creare un *definizione sito*, che funge da base per un nuovo sito di SharePoint. Queste definizioni determinano non solo l'aspetto e il comportamento del sito di SharePoint, ma anche il contenuto predefinito e funzionalità. Nella definizione è possibile inserire elenchi preconfigurati, tipi di contenuto, ricevitori di eventi, immagini e altri elementi. In SharePoint sono incluse alcune definizioni di sito come BLOG, ad esempio. Quando si crea un sito basato sulla definizione di sito BLOG, il sito contiene gli elenchi, le Web part e altri elementi richiesti da un sito blog.  
  
 Per altre informazioni sulle definizioni di sito, vedere [definizioni e modelli di sito](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Progetti di definizione sito
 Progetti di definizione del sito [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornisce solo i file di base che necessita di un sito di SharePoint, non forniscono alcuna funzionalità predefinite. È necessario aggiungere i file e il contenuto per fornire la funzionalità che si desidera. È possibile creare il sito manualmente, creando e aggiungendo i file necessari.  
  
## <a name="feature-stapling"></a>Associazione delle funzionalità
 Uno dei vantaggi della creazione di definizioni di sito nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene automaticamente utilizzati *associazione delle funzionalità*. L'associazione delle funzionalità collega una funzionalità a una definizione di sito anziché incorporare le funzionalità nella definizione del sito stesso. In questo modo è possibile aggiungere la funzionalità per qualsiasi sito creato mediante la definizione del sito senza modificare la definizione di sito originale. Per altre informazioni, vedere [associazione delle funzionalità](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Componenti del progetto definizione sito
 Quando si crea una soluzione di definizione del sito, i seguenti file predefiniti vengono aggiunti al relativo **SiteDefinition** nodo.  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|*Default. aspx*|La pagina home ASPX predefinita per il nuovo sito di SharePoint.|  
|*Onet. Xml*|Specifica la configurazione del nuovo sito, i componenti del modello di definizione sito e il comportamento predefinito. Queste impostazioni possono includere attributi come i tipi di contenuto che sono abilitati, le visualizzazioni elenco predefinite, i file di modello di documento e le Web part incluse con il sito. Per impostazione predefinita, il `Modules` sezione sono elencati i file da aggiungere al sito di SharePoint e come vengono configurate.|  
|*webtemp_\<SiteDefinitionName >. Xml*|Specifica le configurazioni di definizioni di sito che viene visualizzato nei **selezione modello** sezione del **nuovo sito di SharePoint** pagina.|  
  
 Per impostazione predefinita, tutte le definizioni di sito vengono archiviate nel  *\<unità: > \Programmi\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* cartella. Ogni definizione del sito ha la propria sottocartella.  
  
## <a name="related-topics"></a>Argomenti correlati
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: Creare un progetto di definizione sito di base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Illustra la procedura dettagliata tramite la creazione di un progetto di definizione sito di base in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Procedura: Creare una definizione di sito personalizzato e configurazione](http://go.microsoft.com/fwlink/?LinkId=183309)|Viene descritto come creare una definizione di sito personalizzato in SharePoint copiando una definizione di sito esistente e quindi modificando la copia.|  
|[*Webtemp*](http://go.microsoft.com/fwlink/?LinkId=183310)|Descrive il file originale che specifica le definizioni del sito disponibile nel **selezione modello** sezione il **nuovo sito di SharePoint** pagina.|  
|[Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Viene descritto come preparare le soluzioni di SharePoint per l'utilizzo globale.|  
|[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Viene descritto come creare parti di una pagina di SharePoint che gli utenti possono modificare.|  
|[Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Viene descritto come creare controlli riutilizzabili che vengono eseguiti nelle pagine dell'applicazione e le Web part.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Viene descritto come utilizzare la finestra di progettazione viene visualizzata quando si apre una pagina Web nel progetto.|  
|[Cenni preliminari sulle pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Fornisce informazioni generali sulla struttura dei [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] delle pagine Web, come le pagine vengono elaborate [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]e in che modo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] le pagine vengono visualizzate codice conforme agli standard XHTML.|  
|[Sintassi di pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Descrive gli elementi di markup che costituiscono una pagina ASP.NET.|  
|[Programmazione di ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178728)|Vengono fornite informazioni su come creare gestori eventi in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine e le modalità di utilizzo di script client.|  
|[Programmazione di Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Viene descritto come utilizzare il modello a oggetti gestito che viene fornito in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Vedere anche
 [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
