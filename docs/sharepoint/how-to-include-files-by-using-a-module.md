---
title: 'Procedura: Includere file tramite un modulo | Microsoft Docs'
description: Informazioni su come includere file tramite un modulo, ovvero un contenitore che consente di distribuire file come pagine master ASPX, file di testo o immagini in SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d5f229d09ea5a4cceaa0f85dc89612636c072471
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130962"
---
# <a name="how-to-include-files-by-using-a-module"></a>Procedura: Includere file usando un modulo
  *I* moduli (da non confondere con i moduli) sono contenitori che consentono di distribuire file come pagine master ASPX, file di testo [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] o immagini in SharePoint.

 È possibile scegliere di distribuire un file in una raccolta documenti o come file normale ,ad esempio default.aspx, all'esterno di una raccolta documenti. Per aggiungere un file a una raccolta documenti, `Type="GhostableInLibrary"` specificare come attributo **nell'elemento File** . Questa impostazione indica SharePoint creare un elemento elenco da aggiungere al file quando viene aggiunto alla libreria. Per distribuire un file all'esterno di una raccolta documenti, `Type="Ghostable"` specificare o semplicemente omettere l'attributo **Type.**

## <a name="add-a-module-to-a-sharepoint-solution"></a>Aggiungere un modulo a una SharePoint soluzione

#### <a name="to-add-a-module"></a>Per aggiungere un modulo

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire o creare un progetto SharePoint.

     Per altre informazioni, vedere Modelli [SharePoint progetto e di elemento di progetto.](../sharepoint/sharepoint-project-and-project-item-templates.md)

2. In **Esplora soluzioni** scegliere il nodo del progetto e quindi nella barra dei menu **scegliere** Project Aggiungi  >  **nuovo elemento.**

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento .

3. Nell'elenco di SharePoint modelli scegliere il **modello Modulo** e quindi scegliere il **pulsante** Aggiungi.

     Con questo passaggio viene creato un nodo nel progetto denominato Module1.

4. In Module1 eliminare il file *Sample.txt.*

     Sample.txt è incluso in tutti i nuovi moduli a scopo di esempio e non è necessario. Si noti che l'eliminazione del file rimuove anche la relativa voce dal file *Elements.xml* modulo.

5. Se si vuole distribuire i file in una particolare struttura di cartelle in SharePoint, creare tali cartelle in Module1 in scegliendo il nodo Module1 e quindi sulla barra dei menu scegliere Project [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , Nuova **cartella**. 

6. Scegliere la cartella in cui si vuole aggiungere il file, quindi nella barra dei menu **scegliere** Project , **Aggiungi elemento esistente**.

7. Scegliere uno o più file da distribuire in SharePoint e quindi scegliere il **pulsante** Aggiungi.

     Quando si aggiunge un file al progetto, una relativa voce viene aggiunta automaticamente al file Elements.xml modulo. Quando il progetto viene distribuito, i file vengono copiati SharePoint un server, rispetto alla directory radice del progetto, specificata dall'attributo **Url** dell'elemento **File,** ad esempio `Url="Module1/New Folder/SomeFile.doc` . Se si vuole modificare il percorso di distribuzione per un file, spostarlo in un'altra cartella in **Esplora soluzioni** o modificare l'impostazione **URL.**

8. Per tutti i file che si desidera visualizzare in una raccolta documenti, aggiungere l'attributo `Type="GhostableInLibrary"` alla relativa voce in *Elements.xml*. Ad esempio,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Distribuire il progetto.

     I file vengono copiati nei percorsi specificati in SharePoint.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
