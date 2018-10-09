---
title: 'Procedura: creare una. File Vsct | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79d2c0c059d9e257fc0239731fb013a56c6dd6a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532270"
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: creare una. File Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: creare una. File Vsct](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-create-a-dot-vsct-file).  
  
Esistono diversi modi per creare un file di configurazione (con estensione vsct) basato su XML di Visual Studio Command Table.  
  
-   È possibile creare un nuovo VSPackage nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modello di pacchetto.  
  
-   È possibile usare il compilatore comando basato su XML di configurazione di tabella, Vsct.exe, per generare un file da un file con estensione CTC esistente.  
  
-   È possibile usare Vsct.exe per generare un file con estensione vsct da un file CTO esistente.  
  
-   È possibile creare manualmente un nuovo file con estensione vsct.  
  
 Questo argomento illustra come creare manualmente un nuovo file con estensione vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file con estensione vsct  
  
1.  Avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2.  Nel **File** dal menu **New**, quindi fare clic su **File**.  
  
3.  Nel **modelli** riquadro, fare clic su **File XML** e quindi fare clic su **Open**.  
  
4.  Nel **View** menu, fare clic su **finestra proprietà** per visualizzare le proprietà del file XML.  
  
5.  Nel **proprietà** finestra, fare clic sul pulsante Sfoglia (...) della proprietà di schemi.  
  
6.  Nell'elenco di schemi XSD, selezionare lo schema vsct.xsd. Se non è nell'elenco, fare clic su **Add** e quindi individuare il file in un'unità locale. Fare clic su **OK** al termine.  
  
7.  Nel file XML, digitare `<CommandTable` e quindi premere TAB. Chiudere il tag digitando `>`.  
  
     Verrà creato un file con estensione vsct base.  
  
8.  Inserire gli elementi del file XML che si desidera aggiungere, in base al [VSCT Schema](../../extensibility/vsct-xml-schema-reference.md). Per altre informazioni, vedere [creazione e modifica. File Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Semplicemente aggiungendo un file con estensione vsct da un progetto non viene spostato da compilare. È necessario includerlo nel processo di compilazione.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file con estensione vsct per la compilazione del progetto  
  
1.  Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario prima scaricarlo.  
  
2.  Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un elemento VSCTCompile, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L'elemento ResourceName deve sempre essere impostata su `Menus.ctmenu`.  
  
3.  Se il progetto contiene un file con estensione resx, aggiungere un elemento risorsa incorporata contenente un elemento MergeWithCTO, come illustrato nell'esempio seguente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Questo markup deve passare all'interno dell'elemento ItemGroup che contiene risorse incorporate.  
  
4.  Aprire il file del pacchetto, in genere denominato *ProjectName*Package.cs oppure *ProjectName*Package.vb, nell'editor.  
  
5.  Aggiungere un attributo ProvideMenuResource alla classe del pacchetto, come illustrato nell'esempio seguente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Il primo valore del parametro deve corrispondere al valore dell'attributo ResourceName che è definito nel file di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione. File Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Procedura: creare una. File Vsct da un oggetto esistente. File CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Procedura: creare una. File Vsct da un oggetto esistente. File CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
