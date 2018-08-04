---
title: 'Procedura: creare una. File Vsct | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 266b3c4154c10f537cdc9dec78b0f0a036d94503
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512592"
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: creare un file con estensione vsct  
  
Esistono diversi modi per creare una configurazione di tabella comandi di Visual Studio basate su XML (*vsct*) file.  
  
-   È possibile creare un nuovo VSPackage nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto.  
  
-   È possibile usare il compilatore di configurazione di tabella comandi basati su XML, *Vsct.exe*per generare un file da un oggetto esistente *CTC* file.  
  
-   È possibile usare *Vsct.exe* per generare un *con estensione vsct* file da un oggetto esistente *CTO* file.  
  
-   È possibile creare manualmente una nuova *vsct* file.  
  
 Questo articolo illustra come creare manualmente una nuova *vsct* file.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file con estensione vsct  
  
1.  Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Nel **File** dal menu **New**, quindi fare clic su **File**.  
  
3.  Nel **modelli** riquadro, fare clic su **File XML** e quindi fare clic su **Open**.  
  
4.  Nel **View** menu, fare clic su **proprietà** per visualizzare le proprietà del file XML.  
  
5.  Nel **delle proprietà** finestra, fare clic sul **Sfoglia** pulsante il **schemi** proprietà.  
  
6.  Nell'elenco degli schemi XSD, selezionare la *vsct.xsd* dello schema. Se non è nell'elenco, fare clic su **Add** e quindi individuare il file in un'unità locale. Fare clic su **OK** al termine.  
  
7.  Nel file XML, digitare *< CommandTable* e quindi premere **scheda**. Chiudere il tag digitando *>*.  
  
     Questa azione viene creata una semplice *vsct* file.  
  
8.  Inserire gli elementi del file XML che si desidera aggiungere, in base al [riferimenti allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md). Per altre informazioni, vedere [creare i file con estensione vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: creare un File con estensione vsct da un file CTC esistente  
  
È possibile creare un XML basato *vsct* file da una tabella esistente di comando *CTC* file di origine. In questo modo, è possibile sfruttare i vantaggi del nuovo basato su XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando nel formato del compilatore tabella (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC  
  
1.  Ottenere una copia del linguaggio Perl.  
  
2.  Ottenere una copia dello script Perl *ConvertCTCToVSCT.pl*, in genere all'interno di  *\<percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.* cartella.  
  
3.  Ottenere una copia del *CTC* file di origine che si desidera convertire.  
  
4.  Inserire i file nella stessa directory.  
  
5.  Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra prompt dei comandi, passare alla directory.  
  
6.  Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     in cui *Pkgcmd* è il nome del *CTC* file e *Pkgcmd* è il nome del *vsct* file che si desidera creare.  
  
     Questa azione crea un nuovo *vsct* file di origine di tabella comandi XML. È possibile compilare il file usando *Vsct.exe*, il compilatore VSCT, come si procederebbe per un *con estensione vsct* file.  
  
    > [!NOTE]
    >  È possibile migliorare la leggibilità del *vsct* file riformattando i commenti XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: creare un file con estensione vsct da un file CTO esistente  
  
È possibile creare un XML basato *vsct* file da un file binario esistente *CTO* file. Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il *CTO* file è stato compilato da un *CTC* file. È possibile modificare e compilare il *vsct* file in un altro file CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO  
  
1.  Ottenere copie dei *CTO* file e il corrispondente *ctsym* file.  
  
2.  Inserire i file nella stessa directory di *vsct.exe* compilatore.  
  
3.  Al prompt dei comandi di Visual Studio, passare alla directory che contiene il *CTO* e *ctsym* file.  
  
4.  Tipo  

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     in cui \<ctofilename\> è il nome del *CTO* file \<vsctfilename\> è il nome del *vsct* file che si desidera creare e \<symfilename\> è il nome del *ctsym* file.  
  
     Questo processo crea una nuova *vsct* file del compilatore della tabella comandi XML. È possibile modificare e compilare il file con *vsct.exe*, il compilatore vsct, come si procederebbe per un *con estensione vsct* file.  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Aggiungendo semplicemente una *vsct* file a un progetto non viene spostato da compilare. È necessario includerlo nel processo di compilazione.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file con estensione vsct per la compilazione del progetto  
  
1.  Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario prima scaricarlo.  
  
2.  Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un `VSCTCompile` elemento, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Il `ResourceName` elemento deve essere impostato sempre su `Menus.ctmenu`.  
  
3.  Se il progetto contiene un *resx* Aggiungi un' `EmbeddedResource` elemento contenente un `MergeWithCTO` elemento, come illustrato nell'esempio seguente:  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Questo markup deve essere inseriti i `ItemGroup` elemento che contiene risorse incorporate.  
  
4.  Aprire il file del pacchetto, in genere denominato  *\<NomeProgetto\>Package.cs* oppure  *\<ProjectName\>Package.vb*, nell'editor.  
  
5.  Aggiungere un `ProvideMenuResource` attributo alla classe del pacchetto, come illustrato nell'esempio seguente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Il primo valore del parametro deve corrispondere al valore della `ResourceName` attributo è definito nel file di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [File con estensione vsct autore](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [File di Visual Studio comando table (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)