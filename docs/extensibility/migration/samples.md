---
title: Esempio ImageOptimizer per l'aggiornamento Visual Studio estensioni
description: Seguire un esempio per informazioni su come aggiornare un'estensione Visual Studio per usare Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: c309b6c27750d727abfccbaa9061e823aebc16ca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086469"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer - Aggiornare un'estensione Visual Studio passaggio per passaggio

[!INCLUDE [preview-note](../includes/preview-note.md)]

Questa guida illustra tutti i passaggi necessari per aggiungere il supporto di Visual Studio 2022 mantenendo il supporto di Visual Studio 2019 usando l'estensione Di ottimizzazione immagini come case study.  
Si tratta di una guida completa con collegamenti di commit Git a ogni passaggio, ma è possibile vedere la richiesta pull finalizzata qui: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) .

Alla fine [di questa guida sono](#other-samples) disponibili anche altri esempi.

## <a name="step-1---modernize-the-project"></a>Passaggio 1: Modernizzare il progetto

Vedere [Modernizzare il progetto.](update-visual-studio-extension.md#modernize-your-vsix-project)

[git commit e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

Prima di tutto è necessario eseguire l'unit test VSIX e il progetto a .NET 4.7.2 nella pagina delle proprietà dei progetti:

   ![Aggiornamento della versione del framework](media/samples/framework-bump.png)

Image Optimizer fa riferimento ad alcuni pacchetti 14.* e 15.* personalizzati. Verrà invece installato il pacchetto [ `Microsoft.VisualStudio.Sdk` NuGet che](https://www.nuget.org/packages/microsoft.visualstudio.sdk) consolida tutti i riferimenti necessari.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

La compilazione del progetto ha esito positivo e vengono visualizzati alcuni avvisi di threading. Per correggere questi avvisi, fare clic `ctrl` su e e usare `.` IntelliSense per aggiungere le righe mancanti per il cambio di thread.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>Passaggio 2 - Eseguire il refactoring del codice sorgente in un progetto condiviso

Vedere [Progetti condivisi.](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting)

Per supportare Visual Studio 2022 è necessario aggiungere un nuovo progetto condiviso che conterrà il codice sorgente dell'estensione che verrà condiviso tra i progetti VSIX Visual Studio 2019 e Visual Studio 2022.

1. Aggiungere un nuovo progetto condiviso alla soluzione

   [git commit abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Aggiungere un progetto condiviso](media/samples/add-shared-project.png)

1. Aggiungere un riferimento al progetto condiviso al progetto VSIX.

   [git commit e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Aggiungere un riferimento al progetto condiviso" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Spostare i file di codice sorgente (cs, xaml, resx) nel nuovo progetto **condiviso, ad** eccezione dei seguenti:
    - `source.extension.vsixmanifest`
    - File di metadati dell'estensione (icone, licenze, note sulla versione e così via)
    - File VSCT
    - File collegati
    - Strumenti o librerie esterni che devono essere inclusi in VSIX

   [git commit f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Spostare file in un progetto condiviso](media/samples/move-to-shared-project.png)

1. Spostare ora tutti i metadati, i file VSCT, i file collegati e gli strumenti/librerie esterni in un percorso condiviso e aggiungerli nuovamente come elementi collegati al progetto VSIX. **Non rimuovere** `source.extension.vsixmanifest` .

   [Git commit 73ba920 - Spostamento di file](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git commit d5e36b2 - Aggiunta di strumenti/librerie esterni](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Per questo progetto è necessario spostare l'icona dell'estensione, il file VSCT e gli strumenti esterni nella nuova cartella `ImageOptimizer\Resources` . Copiarli nella cartella condivisa e rimuoverli dal progetto VSIX.
   1. Sono stati aggiunti nuovamente come elementi collegati e se gli elementi sono già collegati possono rimanere così come sono (ad esempio, una licenza).
   1. Verificare che l'azione di compilazione e altre proprietà siano impostate correttamente nei file collegati aggiunti selezionando ognuna di queste e controllando la finestra degli strumenti delle proprietà. Per il progetto è stato necessario impostare quanto segue:
       - Impostare `icon.png` Azione di compilazione su e `Content` contrassegnato come Includi in VSIX su `true`
       - Impostare `ImageOptimizer.vsct` Azione di compilazione su e Includi in `VSCTComplile` VSIX su `false`
       - Impostare tutte le azioni di compilazione dei file in `Resources\Tools` su `Content` e contrassegnate come Includi in VSIX su `true`

           ![Aggiungere file collegati al progetto VSIX](media/samples/add-linked-files.png)

       - Inoltre, è una dipendenza di , per questo è necessario aggiungere manualmente questa dipendenza `ImageOptimizer.cs` `ImageOptimizer.vsct` al file csproj:

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Se la finestra degli strumenti delle proprietà impedisce di impostare un'azione di compilazione specifica, è possibile modificare manualmente il file csproj come indicato in precedenza e impostare l'azione di compilazione in base alle esigenze.

1. Compilare il progetto per convalidare le modifiche e correggere eventuali errori/problemi. Per problemi [comuni, vedere](update-visual-studio-extension.md#q--a) la sezione Domande frequenti.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>Passaggio 3- Aggiungere un progetto VSIX Visual Studio 2022

Vedere [Add Visual Studio 2022 target (Aggiungere una destinazione 2022).](update-visual-studio-extension.md#add-a-visual-studio-2022-target)

1. Aggiungere un nuovo progetto VSIX alla soluzione.
1. Rimuovere eventuale codice sorgente aggiuntivo nel nuovo progetto, ad eccezione di `source.extension.vsixmanifest.`

   ![Creare un nuovo progetto VSIX](media/samples/visual-studio-2022-vsix-initial.png)

1. Aggiungere un riferimento al progetto condiviso.

   [git commit dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Aggiungere un riferimento al progetto condiviso" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Aggiungere i file collegati dal progetto VSIX Visual Studio 2019 e verificare che le relative proprietà "Azione di compilazione" e "Includi in VSIX" corrispondano. Copiare anche il file, che verrà modificato in un secondo momento per supportare `source.extension.vsixmanifest` Visual Studio 2022.

   [Git commit 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![Aggiungere file collegati al progetto VSIX](media/samples/visual-studio-2022-add-linked-files.png)

1. Un tentativo di compilazione mostra che manca un riferimento a `System.Windows.Forms` . È sufficiente aggiungerlo al progetto Visual Studio 2022 e ricompilare.

   [git commit de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. Aggiornare `Microsoft.VisualStudio.SDK` e creare pacchetti di riferimento alle Visual Studio `Microsoft.VSSDK.BuildTools` 2022.

   [git commit d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Queste sono le versioni più recenti disponibili al momento della creazione di questa guida. È consigliabile ottenere le versioni più recenti disponibili.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Modificare il `source.extension.vsixmanifest` file in modo da riflettere la destinazione Visual Studio 2022.

   [git commit 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Impostare il `<InstallationTarget>` tag in modo che Visual Studio 2022 e indichi un payload amd64:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Modificare il prerequisito in modo da includere solo Visual Studio 2022 e successive:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

E abbiamo finito!

Con questa operazione, la compilazione ora produce Visual Studio 2019 e Visual Studio 2022 VSIX.

## <a name="other-samples"></a>Altri esempi

- [ProPower Tools](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Consente di visualizzare in anteprima un Web browser con informazioni della Guida sulla classe o sull'oggetto selezionato.
  - FixMixedTabs
    - Analizza i documenti e sostituisce le tabulazioni con spazi o viceversa

## <a name="next-steps"></a>Passaggi successivi

Preparare l'aggiornamento dell'estensione leggendo [questa guida di base.](update-visual-studio-extension.md)
