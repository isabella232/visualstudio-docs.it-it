---
title: 'Procedura: creare un oggetto. File vsct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158347"
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: Creare un file con estensione vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esistono diversi modi per creare un file di configurazione tabella comandi di Visual Studio (con estensione vsct) basato su XML.  
  
- È possibile creare un nuovo VSPackage nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modello di pacchetto.  
  
- Per generare un file da un file con estensione CTC esistente, è possibile usare il compilatore di configurazione della tabella dei comandi basato su XML, Vsct.exe.  
  
- È possibile utilizzare Vsct.exe per generare un file con estensione vsct da un file CTO esistente.  
  
- È possibile creare manualmente un nuovo file con estensione vsct.  
  
  In questo argomento viene illustrato come creare manualmente un nuovo file con estensione vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file con estensione vsct  
  
1. Avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.  
  
3. Nel riquadro **modelli** fare clic su **file XML** e quindi su **Apri**.  
  
4. Scegliere **finestra Proprietà** dal menu **Visualizza** per visualizzare le proprietà del file XML.  
  
5. Nella finestra **Proprietà** fare clic sul pulsante Sfoglia (...) nella proprietà schemi.  
  
6. Nell'elenco degli schemi XSD selezionare lo schema vsct. xsd. Se non è presente nell'elenco, fare clic su **Aggiungi** e quindi individuare il file in un'unità locale. Al termine, fare clic su **OK** .  
  
7. Nel file XML digitare `<CommandTable` e quindi premere TAB. Chiudere il tag digitando `>` .  
  
     Verrà creato un file con estensione vsct di base.  
  
8. Inserire gli elementi del file XML che si desidera aggiungere, in base allo [schema vsct](../../extensibility/vsct-xml-schema-reference.md). Per ulteriori informazioni, vedere [creazione e modifica. File vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 La semplice aggiunta di un file con estensione vsct a un progetto non ne comporta la compilazione. È necessario incorporarlo nel processo di compilazione.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file con estensione vsct alla compilazione del progetto  
  
1. Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario scaricarlo per primo.  
  
2. Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un elemento VSCTCompile, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L'elemento resourceName deve essere sempre impostato su `Menus.ctmenu` .  
  
3. Se il progetto contiene un file con estensione resx, aggiungere un elemento EmbeddedResource che contiene un elemento MergeWithCTO, come illustrato nell'esempio seguente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Questo markup dovrebbe andare all'interno dell'elemento ItemGroup che contiene risorse incorporate.  
  
4. Aprire il file del pacchetto, in genere denominato *nomeprogetto*Package.cs o *NomeProgetto*Package. vb, nell'editor.  
  
5. Aggiungere un attributo ProvideMenuResource alla classe del pacchetto, come illustrato nell'esempio seguente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Il primo valore del parametro deve corrispondere al valore dell'attributo resourceName definito nel file di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Authoring. File vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabella comandi di Visual Studio (. File vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Procedura: creare un oggetto. File vsct da un esistente. File CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Procedura: creare un oggetto. File vsct da un esistente. File CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
