---
title: 'Procedura: importare una pagina master o un tema | Microsoft Docs'
description: Creare modelli per pagine master e temi in SharePoint Designer, quindi importarli in Visual Studio per assegnare un aspetto coerente alle pagine del sito di SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 331ae3964de40e6590345aadae59776fe37f467a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913670"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Procedura: importare una pagina master o un tema
  È possibile assegnare a pagine del sito di SharePoint un aspetto coerente creando e utilizzando pagine e temi master. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non fornisce modelli per questi elementi, ma è possibile crearli in SharePoint Designer e quindi importarli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per ulteriori informazioni, vedere [blocco predefinito: pagine e interfaccia utente](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) nel sito Web Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Per importare una pagina master o un tema

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare o aprire un progetto SharePoint.

     Per informazioni sulla creazione di un progetto SharePoint, vedere [modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nell'elenco dei modelli di SharePoint scegliere il modello di **modulo** e quindi specificare un nome per il modulo.

     Un modulo contiene file (ad esempio, pagina master o file di tema) per la distribuzione in un percorso specificato in SharePoint.

5. Nel modulo eliminare il file predefinito, denominato *Sample.txt*.

6. Scegliere il nodo del modulo.

7. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi elemento esistente**, quindi scegliere la pagina master o il file del tema.

     I file della pagina master hanno un'estensione. master e i file del tema hanno estensione thmx.

8. Se è stata aggiunta una pagina master, modificare la relativa impostazione di **risoluzione dei conflitti di distribuzione** su **automatico** nelle proprietà del modulo.

    > [!NOTE]
    > È possibile che si verifichino errori se il nome della pagina master corrisponde al nome di una pagina master esistente contrassegnata come pagina master predefinita o pagina master personalizzata. Per informazioni su come risolvere questo problema, vedere [procedura dettagliata: importare una pagina master personalizzata e una pagina del sito con un'immagine](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. Nel modulo aprire *Elements.xml*.

     Per fare riferimento alla pagina master o al tema aggiunto, è necessario aggiornare il file di *Elements.xml* .

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

     L'attributo `Type="GhostableInLibrary"` indica che l'elemento viene aggiunto al database del contenuto e l' `Url` attributo del modulo specifica dove archiviare il file nel database del contenuto di SharePoint.

11. Per modificare l'ambito di distribuzione per una pagina master, in **Esplora soluzioni** aprire il file di funzionalità in progettazione funzionalità, quindi scegliere un nuovo ambito di distribuzione dall'elenco **ambito** .

     Il valore **Web** indica che la pagina master si applica solo al sito Web attualmente specificato nel progetto. Il valore **site** indica che la pagina master viene applicata alla raccolta di siti corrente, che include tutti i siti secondari e il Web radice. Gli altri valori non sono applicabili.

    > [!NOTE]
    > Poiché i temi si applicano solo al livello della raccolta siti, è consigliabile non impostare l'ambito di un tema su un valore diverso da **sito**. Se un tema viene usato in un sito secondario, possono verificarsi errori.

12. Sulla barra dei menu scegliere **Compila**  >  **distribuzione soluzione**.

13. Per verificare se i file sono stati distribuiti correttamente, aprire il sito di SharePoint, scegliere il menu **Azioni sito** , scegliere il comando **Impostazioni sito** , quindi scegliere il collegamento **pagine master** o il collegamento **temi** .

     Viene visualizzato l'elenco di pagine master o temi che contiene la pagina master o il tema importato.

## <a name="see-also"></a>Vedi anche
- [Pagine master](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Creazione di pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Usare i moduli per includere i file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)
