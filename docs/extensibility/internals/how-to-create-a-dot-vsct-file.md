---
title: 'Procedura: creare un oggetto. File vsct | Microsoft Docs'
description: Informazioni su come creare manualmente un file con estensione vsct, un file di configurazione tabella comandi di Visual Studio basato su XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66174d5de1abb4f5bdd23eeab0155a795cf0b634
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879982"
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: creare un file con estensione vsct

Esistono diversi modi per creare un file di configurazione tabella comandi di Visual Studio (con *estensione vsct*) basato su XML.

- È possibile creare un nuovo VSPackage nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto.

- Per generare un file da un file con *estensione CTC* esistente, è possibile usare il compilatore di configurazione della tabella dei comandi basato su XML, *Vsct.exe*.

- È possibile utilizzare *Vsct.exe* per generare un file con estensione *vsct* da un file *CTO* esistente.

- È possibile creare manualmente un nuovo file con *estensione vsct* .

  Questo articolo illustra come creare manualmente un nuovo file con *estensione vsct* .

### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file con estensione vsct

1. Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.

3. Nel riquadro **modelli** fare clic su **file XML** e quindi su **Apri**.

4. Scegliere **Proprietà** dal menu **Visualizza** per visualizzare le proprietà del file XML.

5. Nella finestra **Proprietà** fare clic sul pulsante **Sfoglia** nella proprietà **schemi** .

6. Nell'elenco degli schemi XSD selezionare lo schema *vsct. xsd* . Se non è presente nell'elenco, fare clic su **Aggiungi** e quindi individuare il file in un'unità locale. Al termine, fare clic su **OK** .

7. Nel file XML digitare *<CommandTable* , quindi premere **Tab**. Chiudere il tag digitando *>* .

    Questa azione crea un file con *estensione vsct* di base.

8. Inserire gli elementi del file XML che si desidera aggiungere, in base al [riferimento XML Schema vsct](../../extensibility/vsct-xml-schema-reference.md). Per ulteriori informazioni, vedere la pagina relativa ai [file Author. vsct](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: creare un file con estensione vsct da un file CTC esistente

È possibile creare un file con *estensione vsct* basato su XML da un file di origine *CTC* esistente della tabella dei comandi. In questo modo, si può sfruttare il nuovo formato basato su XML del compilatore della tabella comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC

1. Ottenere una copia del linguaggio Perl.

2. Ottenere una copia dello script Perl *ConvertCTCToVSCT.pl*, che si trova in genere nella cartella *\<Visual Studio SDK installation path> \VisualStudioIntegration\Tools\bin*

3. Ottenere una copia del file di origine con *estensione CTC* che si desidera convertire.

4. Inserire i file nella stessa directory.

5. Nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra del prompt dei comandi passare alla directory.

6. Tipo

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    dove *PkgCmd. CTC* è il nome del file con *estensione CTC* e *PkgCmd. vsct* è il nome del file con *estensione vsct* che si vuole creare.

    Questa azione crea un nuovo file di origine della tabella di comandi XML *. vsct* . È possibile compilare il file usando *Vsct.exe*, il compilatore vsct, come qualsiasi altro file *. vsct* .

   > [!NOTE]
   > È possibile migliorare la leggibilità del file con *estensione vsct* riformattando i commenti XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: creare un file con estensione vsct da un file CTO esistente

È possibile creare un file con estensione *vsct* basato su XML da un file *CTO* binario esistente. Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il file *CTO* è stato compilato da un file *CTC* . È possibile modificare e compilare il file con estensione *vsct* in un altro file CTO.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO

1. Ottenere copie del file *CTO* e del corrispondente file *ctsym* .

2. Inserire i file nella stessa directory del compilatore *vsct.exe* .

3. Al prompt dei comandi di Visual Studio passare alla directory che contiene i file con *estensione CTO* e *ctsym* .

4. Tipo

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     dove \<ctofilename\> è il nome del file *CTO* , \<vsctfilename\> è il nome del file con *estensione vsct* che si vuole creare e \<symfilename\> è il nome del file *. ctsym* .

     Questo processo crea un nuovo file del compilatore della tabella comandi XML *. vsct* . È possibile modificare e compilare il file con *vsct.exe*, il compilatore vsct, come qualsiasi altro file *. vsct* .

## <a name="compile-the-code"></a>Compilare il codice
 La semplice aggiunta di un file con *estensione vsct* a un progetto non ne comporta la compilazione. È necessario incorporarlo nel processo di compilazione.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file con estensione vsct alla compilazione del progetto

1. Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario scaricarlo per primo.

2. Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un `VSCTCompile` elemento, come illustrato nell'esempio seguente.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     L' `ResourceName` elemento deve essere sempre impostato su `Menus.ctmenu` .

3. Se il progetto contiene un file con *estensione resx* , aggiungere un `EmbeddedResource` elemento che contiene un `MergeWithCTO` elemento, come illustrato nell'esempio seguente:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Questo markup deve entrare nell' `ItemGroup` elemento che contiene risorse incorporate.

4. Aprire il file del pacchetto, in genere denominato *\<ProjectName\> Package.cs* o *\<ProjectName\> Package. vb*, nell'editor.

5. Aggiungere un `ProvideMenuResource` attributo alla classe del pacchetto, come illustrato nell'esempio seguente.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Il primo valore del parametro deve corrispondere al valore dell' `ResourceName` attributo definito nel file di progetto.

## <a name="see-also"></a>Vedi anche
- [Crea file con estensione vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimento XML Schema VSCT](../../extensibility/vsct-xml-schema-reference.md)
