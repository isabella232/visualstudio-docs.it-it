---
title: 'Procedura: Creare un oggetto . File vsct | Microsoft Docs'
description: Informazioni su come creare manualmente un file con estensione vsct, un file di configurazione della tabella dei comandi basato su XML Visual Studio comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fa80c77a9ed390e55e39b72c0ea5976f0584b25b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709558"
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: Creare un file vsct

Esistono diversi modi per creare un file di configurazione della tabella dei comandi basato Visual Studio XML *(vsct).*

- È possibile creare un nuovo VSPackage nel modello [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di pacchetto.

- È possibile usare il compilatore di configurazione della tabella dei comandi basato su XML, *Vsct.exe*, per generare un file da un file *con estensione ctc* esistente.

- È possibile usare *Vsct.exe* per generare un file *vsct* da un file *con estensione cto* esistente.

- È possibile creare manualmente un nuovo file *con estensione vsct.*

  Questo articolo illustra come creare manualmente un nuovo file con estensione *vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file vsct

1. Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.

3. Nel riquadro **Modelli** fare clic su **File XML** e quindi su **Apri**.

4. Scegliere **Proprietà** dal menu Visualizza **per** visualizzare le proprietà del file XML.

5. Nella finestra **Proprietà** fare clic sul **pulsante Sfoglia** nella **proprietà** Schemi.

6. Nell'elenco degli schemi XSD selezionare lo schema *vsct.xsd.* Se non è presente nell'elenco, fare clic **su Aggiungi** e quindi trovare il file in un'unità locale. Al termine, fare clic su **OK.**

7. Nel file XML digitare<*CommandTable* e quindi premere **TAB.** Chiudere il tag digitando *>* .

    Questa azione crea un file *con estensione vsct di base.*

8. Compilare gli elementi del file XML da aggiungere, in base al riferimento allo [schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md). Per altre informazioni, vedere [Creare file con estensione vsct.](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: Creare un file con estensione vsct da un file con estensione ctc esistente

È possibile creare un file con estensione *vsct* basato su XML da un file di origine con estensione *ctc della* tabella dei comandi esistente. In questo modo, si può sfruttare il nuovo formato basato su XML del compilatore della tabella comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC

1. Ottenere una copia del linguaggio Perl.

2. Ottenere una copia dello script Perl *ConvertCTCToVSCT.pl*, in genere nella *\<Visual Studio SDK installation path> cartella \VisualStudioIntegration\Tools\bin.*

3. Ottenere una copia del file di origine *con estensione ctc* da convertire.

4. Inserire i file nella stessa directory.

5. Nella finestra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del prompt dei comandi passare alla directory .

6. Tipo

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    dove *PkgCmd.ctc* è il nome del file con estensione *ctc* e *PkgCmd.vsct* è il nome del file *vsct* che si vuole creare.

    Questa azione crea un nuovo file di origine della tabella dei comandi XML con estensione *vsct.* È possibile compilare il file usando *Vsct.exe*, il compilatore VSCT, come qualsiasi altro file con estensione *vsct.*

   > [!NOTE]
   > È possibile migliorare la leggibilità del file *con estensione vsct* riformattando i commenti XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: Creare un file con estensione vsct da un file con estensione cto esistente

È possibile creare un file con estensione *vsct* basato su XML da un file *binario esistente con estensione cto.* Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il file *con estensione cto* è stato compilato da un file *con estensione ctc.* È possibile modificare e compilare il file *con estensione vsct* in un altro file con estensione cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO

1. Ottenere copie del file *con estensione cto* e del file con estensione *ctsym* corrispondente.

2. Inserire i file nella stessa directory del compilatore *vsct.exe* locale.

3. Al prompt Visual Studio comando passare alla directory che contiene i file con estensione *cto* e *ctsym.*

4. Tipo

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     dove è il nome del file con estensione cto, è il nome del file vsct che si vuole creare e è il nome del file con estensione \<ctofilename\>  \<vsctfilename\>  \<symfilename\> *ctsym.*

     Questo processo crea un nuovo file del compilatore della tabella dei comandi XML con estensione *vsct.* È possibile modificare e compilare il file *convsct.exe*, il compilatore vsct, come qualsiasi altro file con estensione *vsct.*

## <a name="compile-the-code"></a>Compilare il codice
 La semplice aggiunta di un file *vsct* a un progetto non ne determina la compilazione. È necessario incorporarlo nel processo di compilazione.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file vsct alla compilazione del progetto

1. Aprire il file di progetto nell'editor. Se il progetto viene caricato, è prima necessario scaricarlo.

2. Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) contenente un `VSCTCompile` elemento , come illustrato nell'esempio seguente.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName`L'elemento deve sempre essere impostato su `Menus.ctmenu` .

3. Se il progetto contiene un file *con estensione resx,* aggiungere un elemento che contiene `EmbeddedResource` un elemento , come illustrato `MergeWithCTO` nell'esempio seguente:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Questo markup deve essere inserito `ItemGroup` nell'elemento che contiene risorse incorporate.

4. Aprire il file del pacchetto, in genere *\<ProjectName\> denominato Package.cs* *\<ProjectName\> o Package.vb,* nell'editor.

5. Aggiungere un `ProvideMenuResource` attributo alla classe del pacchetto, come illustrato nell'esempio seguente.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Il primo valore del parametro deve corrispondere al valore `ResourceName` dell'attributo definito nel file di progetto.

## <a name="see-also"></a>Vedi anche
- [Creare file con estensione vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Informazioni di riferimento sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
