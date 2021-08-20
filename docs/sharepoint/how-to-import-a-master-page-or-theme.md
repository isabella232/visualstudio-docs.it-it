---
title: 'Procedura: Importare una pagina master o un tema | Microsoft Docs'
description: Creare modelli per le pagine master e i temi in SharePoint Designer, quindi importare in Visual Studio per assegnare alle pagine del sito SharePoint un aspetto coerente.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 69d304d476be4b1e0ab97500b1f13b04bd68ff1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093008"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Procedura: Importare una pagina master o un tema
  È possibile assegnare alle pagine SharePoint sito un aspetto coerente creando e usando pagine master e temi. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]non fornisce modelli per questi elementi, ma è possibile crearli in SharePoint Designer e quindi importarli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per altre informazioni, vedere [Blocco predefinito: pagine e Interfaccia utente](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) nel sito Web Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Per importare una pagina master o un tema

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare o aprire un SharePoint progetto.

     Per informazioni su come creare un progetto di SharePoint, vedere creare SharePoint [progetto e modelli di elemento di progetto.](../sharepoint/sharepoint-project-and-project-item-templates.md)

2. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi** nuovo elemento espandere il **SharePoint** e quindi scegliere il **nodo 2010.**

4. Nell'elenco di SharePoint modelli scegliere il **modello Modulo** e quindi specificare un nome per il modulo.

     Un modulo contiene file (ad esempio, file di pagine master o di tema) per la distribuzione in un percorso specificato in SharePoint.

5. Nel modulo eliminare il file predefinito, denominato *Sample.txt*.

6. Scegliere il nodo del modulo.

7. Sulla barra dei menu scegliere aggiungi **Project** elemento esistente e quindi scegliere la pagina master o il  >  file del tema.

     I file di pagine master hanno estensione master e i file di tema hanno estensione thmx.

8. Se è stata aggiunta una pagina master, modificare l'impostazione **risoluzione dei** conflitti di distribuzione in **Automatico** nelle proprietà del modulo.

    > [!NOTE]
    > Possono verificarsi errori se il nome della pagina master corrisponde al nome di una pagina master esistente contrassegnata come Pagina master predefinita o Pagina master personalizzata. Per informazioni su come risolvere questo problema, vedere Procedura dettagliata: Importare una pagina master personalizzata e una pagina [del sito con un'immagine.](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)

9. Nel modulo aprire *Elements.xml*.

     È necessario aggiornare il *fileElements.xml* per fare riferimento alla pagina master o al tema aggiunto.

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

     Assicurarsi di sostituire i valori segnaposto con i nomi effettivi del modulo e della pagina master o del tema.

     L'attributo indica che l'elemento viene aggiunto al database del contenuto e l'attributo del modulo specifica dove archiviare il file nel `Type="GhostableInLibrary"` `Url` database SharePoint contenuto.

11. Per modificare l'ambito di distribuzione per una pagina master, in **Esplora soluzioni** aprire il file della funzionalità in Progettazione funzionalità e quindi scegliere un nuovo ambito di distribuzione dall'elenco **Ambito** .

     Il valore **Web** indica che la pagina master si applica solo al sito Web attualmente specificato nel progetto. Il valore **Sito indica** che la pagina master si applica alla raccolta siti corrente, che include tutti i siti secondari e il Web radice. Gli altri valori non sono applicabili.

    > [!NOTE]
    > Poiché i temi si applicano solo al livello della raccolta siti, è consigliabile non impostare l'ambito di un tema su un valore diverso da **Sito**. Se si usa un tema in un sito secondario, possono verificarsi errori.

12. Nella barra dei menu scegliere Compila  >  **Distribuisci soluzione.**

13. Per verificare se i file sono stati distribuiti correttamente, aprire il sito di SharePoint, scegliere il **menu** Azioni sito, scegliere  il comando **Impostazioni** sito e quindi scegliere il collegamento **Pagine master** o il collegamento Temi.

     Viene visualizzato l'elenco delle pagine master o dei temi che contiene la pagina master o il tema importato.

## <a name="see-also"></a>Vedi anche
- [Pagine master](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Importazione di elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Creare pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Usare i moduli per includere i file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)
