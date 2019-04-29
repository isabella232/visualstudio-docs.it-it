---
title: 'Procedura: Includere file mediante un modulo | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5813a6f89062bf53f7f8c0b57b4ed3a8ef9c4edf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813644"
---
# <a name="how-to-include-files-by-using-a-module"></a>Procedura: Includere file mediante un modulo
  *I moduli* (non deve essere confusa con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli) sono contenitori che consentono di distribuire i file, ad esempio le pagine master ASPX, file di testo o immagini in SharePoint.

 È possibile distribuire un file in una raccolta documenti o come un normale file (ad esempio default. aspx) all'esterno di una raccolta documenti. Per aggiungere un file in una raccolta documenti, specificare `Type="GhostableInLibrary"` come attributo nel **File** elemento. Questa impostazione indica a SharePoint per creare un elemento di elenco per passare con il file quando viene aggiunto alla raccolta. Per distribuire un file all'esterno di una raccolta documenti, specificare `Type="Ghostable"` oppure omettere semplicemente il **tipo** attributo.

## <a name="add-a-module-to-a-sharepoint-solution"></a>Aggiungere un modulo a una soluzione di SharePoint

#### <a name="to-add-a-module"></a>Per aggiungere un modulo

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire o creare un progetto SharePoint.

     Per altre informazioni, vedere [SharePoint modelli di elemento di progetto e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Nelle **Esplora soluzioni**, scegliere il nodo del progetto e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.

     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

3. Nell'elenco dei modelli di SharePoint, scegliere il **modulo** modello, quindi scegliere il **Add** pulsante.

     Con questo passaggio viene creato un nodo nel progetto denominato Module1.

4. In Module1 eliminare il *Sample. txt* file.

     Sample è incluso in tutti i nuovi moduli, ad esempio a scopo e non è necessaria. (Si noti che l'eliminazione del file del modulo rimuove anche la voce corrispondente *Elements* file.)

5. Se si desidera che i file vengano distribuiti a una determinata struttura di cartelle in SharePoint, creare le cartelle in Module1 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliendo il nodo Module1, quindi nella barra dei menu, scegliendo **Project**, **New Cartella**.

6. Scegliere la cartella in cui si desidera aggiungere il file e quindi nella barra dei menu scegliere **Project**, **Aggiungi elemento esistente**.

7. Scegliere uno o più file che si desidera distribuire in SharePoint e quindi scegliere il **Add** pulsante.

     Quando si aggiunge un file al progetto, viene automaticamente aggiunta una voce per tale file Elements. XML del modulo. Quando viene distribuito il progetto, i file vengono copiati nel server SharePoint, relativo alla directory radice del progetto, specificato mediante il **File** dell'elemento **Url** attributo, ad esempio `Url="Module1/New Folder/SomeFile.doc`. Se si desidera modificare il percorso di distribuzione per un file, uno spostarlo in un'altra cartella **Esplora soluzioni** o modificare relativo **Url** impostazione.

8. Per tutti i file che si desidera visualizzare in una raccolta documenti, aggiungere il `Type="GhostableInLibrary"` dell'attributo relativa voce in *Elements*. Ad esempio,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Distribuire il progetto.

     Il file vengono copiati nei percorsi specificati in SharePoint.

## <a name="see-also"></a>Vedere anche
- [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
