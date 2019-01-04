---
title: 'Procedura: Importare una pagina Master o un tema | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7341d12571143d2725b3dd05e5d8e9f03c7d9125
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952908"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Procedura: Importare una pagina master o un tema
  È possibile assegnare le pagine nel sito di SharePoint un aspetto coerente creando e usando i temi e le pagine master. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non fornisce modelli per questi elementi, ma è possibile crearli in SharePoint Designer e quindi importarli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [blocco predefinito: Interfaccia utente e le pagine](http://go.microsoft.com/fwlink/?LinkID=182095) del sito Web Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Per importare una pagina master o un tema  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare o aprire un progetto SharePoint.  
  
     Per informazioni su come creare un progetto SharePoint, vedere [SharePoint modelli di elemento di progetto e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
4.  Nell'elenco dei modelli di SharePoint, scegliere il **modulo** modello, quindi specificare un nome per il modulo.  
  
     Un modulo contiene file (ad esempio, file di tema o pagina master) per la distribuzione in una posizione specificata in SharePoint.  
  
5.  Nel modulo, eliminare il file predefinito, chiamata ScriptHelpers *Sample. txt*.  
  
6.  Scegliere il nodo del modulo.  
  
7.  Nella barra dei menu, scegliere **Project** > **Aggiungi elemento esistente**, quindi scegliere il file di pagina o un tema master.  
  
     File della pagina master caratterizzati dall'estensione. master, e i file di tema hanno un'estensione di estensione thmx.  
  
8.  Se si aggiunge una pagina master, modificare relativi **risoluzione dei conflitti di distribuzione** se si imposta su **automatica** nelle proprietà del modulo.  
  
    > [!NOTE]  
    >  Se il nome della pagina master è identico al nome di una pagina master esistente che è contrassegnata come pagina Master predefinita o pagina Master personalizzata, possono verificarsi errori. Per informazioni su come risolvere questo problema, vedere [procedura dettagliata: Importare una pagina master personalizzata e una pagina del sito con un'immagine](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Nel modulo, aprire *Elements*.  
  
     È necessario aggiornare il *Elements* file per fare riferimento alla pagina master o un tema che è stato aggiunto.  
  
10. Per una pagina master, sostituire il markup del modulo esistente con il markup seguente.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Per un tema, sostituire il markup del modulo esistente con il markup seguente.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Assicurarsi di sostituire i valori segnaposto con i nomi effettivi del modulo e la pagina master o il tema.  
  
     L'attributo `Type="GhostableInLibrary"` indica che l'elemento viene aggiunto al database del contenuto e il `Url` attributo del modulo specifica la posizione in cui archiviare il file nel database del contenuto di SharePoint.  
  
11. Per modificare l'ambito di distribuzione per una pagina master, in **Esplora soluzioni**, aprire il file delle funzionalità nella finestra di progettazione di funzionalità e quindi scegliere un nuovo ambito di distribuzione dalle **ambito** elenco.  
  
     Un valore pari **Web** significa che la pagina master si applica solo al sito Web che è già specificato nel progetto. Un valore pari **sito** significa che la pagina master si applica alla raccolta di siti corrente, che include tutti i siti secondari e web radice. Gli altri valori non sono applicabili.  
  
    > [!NOTE]  
    >  Poiché i temi si applicano solo a livello di raccolta siti, è consigliabile non impostare l'ambito di un tema su qualsiasi elemento diverso da **sito**. Possono verificarsi errori se viene usato un tema in un sito secondario.  
  
12. Nella barra dei menu, scegliere **compilare** > **Distribuisci soluzione**.  
  
13. Per verificare se i file sono stati distribuiti correttamente, aprire il sito di SharePoint, scegliere il **Azioni sito** menu, scegliere il **le impostazioni del sito** comando e quindi scegliere il **pagine Master**  collegamento o il **temi** collegamento.  
  
     L'elenco di pagine master o temi viene visualizzata e contiene la pagina master o il tema è stato importato.  
  
## <a name="see-also"></a>Vedere anche
 [Pagine master](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Creazione di pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Usare i moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
