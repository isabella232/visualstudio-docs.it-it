---
title: 'Procedura: creare un file . File Di Vsct Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3155ff69db461e652b11ff6e8ec6d405000244f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303169"
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: creare un file vsctHow to: Create a .vsct file

Esistono diversi modi per creare un file di configurazione della tabella dei comandi di Visual Studio basato su XML (*.vsct*).

- È possibile creare un nuovo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage nel modello di pacchetto.

- È possibile utilizzare il compilatore di configurazione della tabella dei comandi basata su XML, *Vsct.exe*, per generare un file da un file *ctc* esistente.

- È possibile utilizzare *Vsct.exe* per generare un file *vsct* da un file *con estensione cto* esistente.

- È possibile creare manualmente un nuovo file *vsct.*

  In questo articolo viene illustrato come creare manualmente un nuovo file *vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file vsct

1. Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.

3. Nel riquadro **Modelli** fare clic su **File XML** e quindi su **Apri**.

4. Scegliere **Proprietà** dal menu **Visualizza** per visualizzare le proprietà del file XML.

5. Nella finestra **Proprietà** fare clic sul pulsante **Sfoglia** della proprietà **Schemi.**

6. Nell'elenco degli schemi XSD selezionare lo schema *vsct.xsd.* Se non è presente nell'elenco, fare clic su **Aggiungi** e quindi individuare il file in un'unità locale. Al termine, fare clic **su OK.**

7. Nel file XML digitare *<tabella Comandi* e quindi premere **TAB.** Chiudere il tag *>* digitando .

    Questa azione crea un file *vsct* di base.

8. Compilare gli elementi del file XML che si desidera aggiungere, in base al riferimento allo [schema XML VSCT.](../../extensibility/vsct-xml-schema-reference.md) Per ulteriori informazioni, consultate [Creare file con estensione vsct.](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: creare un file vsct da un file con estensione ctc esistenteHow to: Create a .vsct File from an existing .ctc file

È possibile creare un file *vsct* basato su XML da un file di origine *ctc* della tabella dei comandi esistente. In questo modo, si può sfruttare il nuovo formato basato su XML del compilatore della tabella comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC

1. Ottenere una copia del linguaggio Perl.

2. Ottenere una copia dello script Perl *ConvertCTCToVSCT.pl*, in genere che si trova nella cartella del percorso di installazione di * \<Visual Studio SDK>.*

3. Ottenere una copia del file di origine *.ctc* che si desidera convertire.

4. Inserire i file nella stessa directory.

5. Nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra del prompt dei comandi passare alla directory.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    dove *PkgCmd.ctc* è il nome del file *.ctc* e *PkgCmd.vsct* è il nome del file *vsct* che si desidera creare.

    Questa azione crea un nuovo file di origine della tabella dei comandi XML *con estensione vsct.* È possibile compilare il file utilizzando *Vsct.exe*, il compilatore VSCT, come si farebbe con qualsiasi altro file *vsct.*

   > [!NOTE]
   > È possibile migliorare la leggibilità del file *vsct* riformattando i commenti XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: creare un file vsct da un file con estensione cto esistenteHow to: Create a .vsct file from an existing .cto file

È possibile creare un file *vsct* basato su XML da un file con *estensione cto* binario esistente. Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il file *.cto* è stato compilato da un file *.ctc.* È possibile modificare e compilare il file *vsct* in un altro file .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO

1. Ottenere copie del file *cto* e del file *.ctsym* corrispondente.

2. Inserire i file nella stessa directory del compilatore *vsct.exe.*

3. Al prompt dei comandi di Visual Studio passare alla directory che contiene i file *cto* e *ctsym.*

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     dove \<\> nomefile-cto è il nome \<del file\> con *estensione cto,* vsctfilename è \<il\> nome del file *vsct* che si desidera creare e symnomenè il nome del file *con estensione ctsym.*

     Questo processo crea un nuovo file del compilatore della tabella dei comandi XML *con estensione vsct.* È possibile modificare e compilare il file con *vsct.exe*, il compilatore vsct, come si farebbe con qualsiasi altro file *vsct.*

## <a name="compile-the-code"></a>Compilare il codice
 La semplice aggiunta di un file *con estensione vsct* a un progetto non ne determina la compilazione. È necessario incorporarlo nel processo di compilazione.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file con estensione vsct alla compilazione del progettoTo add a .vsct file to project compilation

1. Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario prima scaricarlo.

2. Aggiungere un [Elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un `VSCTCompile` elemento, come illustrato nell'esempio seguente.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     L'elemento `ResourceName` deve essere `Menus.ctmenu`sempre impostato su .

3. Se il progetto contiene un file RESX, `MergeWithCTO` aggiungere un elemento che contiene un elemento, come illustrato nell'esempio seguente:If your project contains a *.resx* file, add an `EmbeddedResource` element that contains a element, as shown in the following example:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Questo markup deve `ItemGroup` passare all'interno dell'elemento che contiene risorse incorporate.

4. Aprire il file del pacchetto, in genere denominato * \<NomeProgetto\>Package.cs* o * \<ProjectName\>Package.vb*, nell'editor.

5. Aggiungere `ProvideMenuResource` un attributo alla classe del pacchetto, come illustrato nell'esempio seguente.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Il primo valore di parametro `ResourceName` deve corrispondere al valore dell'attributo definito nel file di progetto.

## <a name="see-also"></a>Vedere anche
- [Creare file vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimento allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)