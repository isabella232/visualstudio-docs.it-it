---
title: 'Procedura: includere file mediante un modulo | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ada86be30e207e36c7e0d84d3fd5dd877605e4d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016297"
---
# <a name="how-to-include-files-by-using-a-module"></a>Procedura: includere file mediante un modulo
  I *moduli* (da non confondere con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] i moduli) sono contenitori che consentono di distribuire file, ad esempio pagine master aspx, file di testo o immagini, in SharePoint.

 È possibile scegliere di distribuire un file in una raccolta documenti o come file normale, ad esempio default. aspx, al di fuori di una raccolta documenti. Per aggiungere un file a una raccolta documenti, specificare `Type="GhostableInLibrary"` come attributo nell'elemento **file** . Questa impostazione indica a SharePoint di creare un elemento di elenco da usare con il file quando viene aggiunto alla libreria. Per distribuire un file all'esterno di una raccolta documenti, specificare `Type="Ghostable"` o omettere solo l'attributo **Type** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Aggiungere un modulo a una soluzione SharePoint

#### <a name="to-add-a-module"></a>Per aggiungere un modulo

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire o creare un progetto SharePoint.

     Per ulteriori informazioni, vedere [modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. In **Esplora soluzioni**scegliere il nodo del progetto, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

3. Nell'elenco dei modelli di SharePoint scegliere il modello di **modulo** , quindi scegliere il pulsante **Aggiungi** .

     Con questo passaggio viene creato un nodo nel progetto denominato Module1.

4. In Module1 eliminare il file di *Sample.txt* .

     Sample.txt è incluso in tutti i nuovi moduli a scopo esemplificativo e non è necessario. Si noti che l'eliminazione del file comporta anche la rimozione della relativa voce dal file *Elements.xml* del modulo.

5. Se si desidera che i file vengano distribuiti in una struttura di cartelle specifica in SharePoint, creare le cartelle in Module1 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliendo il nodo Module1, quindi sulla barra dei menu scegliere **progetto**, **nuova cartella**.

6. Scegliere la cartella in cui si desidera aggiungere il file, quindi nella barra dei menu scegliere **progetto**, **Aggiungi elemento esistente**.

7. Scegliere uno o più file che si desidera distribuire in SharePoint, quindi scegliere il pulsante **Aggiungi** .

     Quando si aggiunge un file al progetto, una voce per esso viene aggiunta automaticamente al file di Elements.xml del modulo. Quando il progetto viene distribuito, i file vengono copiati in SharePoint Server, relativi alla directory radice del progetto, specificata dall'attributo **URL** dell'elemento **file** , ad esempio `Url="Module1/New Folder/SomeFile.doc` . Se si desidera modificare il percorso di distribuzione per un file, spostarlo in un'altra cartella in **Esplora soluzioni** o modificarne l'impostazione **URL** .

8. Per tutti i file che si desidera visualizzare in una raccolta documenti, aggiungere l' `Type="GhostableInLibrary"` attributo alla relativa voce in *Elements.xml*. Ad esempio:

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Distribuire il progetto.

     I file vengono copiati nei percorsi specificati in SharePoint.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
