---
title: Editor colori VSIX - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704036"
---
# <a name="vsix-color-editor"></a>Editor dei colori VSIX
Lo strumento Visual Studio Extension Color Editor può creare e modificare colori personalizzati per Visual Studio.The Visual Studio Extension Color Editor tool can create and edit custom colors for Visual Studio. Lo strumento può anche generare chiavi di risorsa del tema in modo che i colori possono essere utilizzati nel codice. Questo strumento è utile per creare colori per un'estensione di Visual Studio che supporta i temati. Questo strumento può aprire file con estensione pkgdef e xml. I temi di Visual Studio (file con estensione vstheme) possono essere utilizzati con l'Editor colori estensione di Visual Studio modificando l'estensione del file in XML. Inoltre, i file con estensione vstheme possono essere importati in un file XML corrente.

 ![Immagine principale dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Immagine principale dell'editor dei colori VSIX")

 **File di definizione del pacchetto**

 I file di definizione del pacchetto (con estensione pkgdef) sono i file che definiscono i temi. I colori stessi vengono memorizzati nei file .xml dei colori del tema, che vengono compilati in un file .pkgdef. I file con estensione pkgdef vengono distribuiti in percorsi ricercabili di Visual Studio, elaborati in fase di esecuzione e uniti per definire i temi.

 **Token di colore**

 Un token di colore è costituito da quattro elementi:A color token is made up of four elements:

- **Nome categoria:** Raggruppamento logico per un set di colori. Usa un nome di categoria esistente se sono già presenti colori specifici per l'elemento dell'interfaccia utente desiderato o un gruppo di elementi dell'interfaccia utente.

- **Nome token:** Nome descrittivo per il token di colore e i set di token. I set includono i nomi dei token di sfondo e di primo piano (testo), nonché tutti i relativi stati, che devono essere denominati in modo che sia facile identificare le coppie e gli stati a cui si applicano.

- Valori di **colore (o tonalità):** Necessario per ogni tema colorato. Crea sempre i valori di colore dello sfondo e del testo in coppia. I colori vengono associati per lo sfondo/primo piano in modo che il colore del testo (primo piano) sia sempre leggibile rispetto al colore di sfondo su cui viene disegnato. Questi colori sono collegati e verranno utilizzati insieme nell'interfaccia utente. Se lo sfondo non è destinato all'uso con il testo, non definire un colore di primo piano.

- **Nome colore di sistema:** Per l'uso in schermi ad alto contrasto.

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 Per quanto possibile e, se necessario, i colori di Visual Studio esistenti devono essere riutilizzati invece di crearne di nuovi. Tuttavia, per i casi in cui non sono definiti colori appropriati, i colori personalizzati devono essere creati per mantenere compatibile un tema di estensione.

 **Creazione di nuovi token di colore**

 Per creare colori personalizzati utilizzando l'Editor colori estensione di Visual Studio, attenersi alla seguente procedura:

1. Determinare i nomi di categoria e token per i nuovi token di colore.

2. Scegli le tonalità che l'elemento dell'interfaccia utente utilizzerà per ogni tema e il colore di sistema per Contrasto elevato.

3. Utilizzare l'editor dei colori per creare nuovi token di colore.

4. Usare i colori in un'estensione di Visual Studio.Use the colors in a Visual Studio extension.

5. Testare le modifiche in Visual Studio.Test the changes in Visual Studio.

   **Passaggio 1: Determinare i nomi di categoria e token per i nuovi token di colore.**

   Lo schema di denominazione preferito per un VSColor è **[Category] [tipo di interfaccia utente] [State]**. Non utilizzare la parola "colore" nei nomi VSColor, in quanto è ridondante.

   I nomi delle categorie forniscono raggruppamenti logici e devono essere definiti nel modo più ristretto possibile. Ad esempio, il nome di una singola finestra degli strumenti potrebbe essere un nome di categoria, ma non il nome di un'intera Business Unit o di un team di progetto. Il raggruppamento delle voci in categorie consente di evitare confusione tra colori con lo stesso nome.

   Un nome di token deve indicare chiaramente il tipo di elemento e le situazioni, o "stato", per cui verrà applicato il colore. Ad esempio, un suggerimento dati attivo **[tipo interfaccia utente]** potrebbe essere denominato "**Suggerimento dati**" e **[Stato]** potrebbe essere denominato **"Active**", risultante in un nome di colore di "**DataTipActive**". Poiché i suggerimenti dati conto di testo, è necessario definire sia un colore di primo piano che un colore di sfondo. Utilizzando un'associazione di sfondo/primo piano, l'editor dei colori creerà automaticamente i colori "**DataTipActive**" per lo sfondo e "**DataTipActiveText**" per il primo piano.

   Se la parte dell'interfaccia utente ha un solo stato, la parte **[State]** del nome può essere omessa. Ad esempio, se una casella di ricerca ha un bordo e non viene apportata alcuna modifica di stato che influirebbe sul colore del bordo, il nome del token di colore del bordo può essere semplicemente chiamato "**SearchBoxBorder**".

   Alcuni nomi di stato comuni includono:Some common state names include:

- Attivo

- Inactive

- MouseOver

- Mousedown

- Selezionato

- Con stato attivo

  Esempi di alcuni nomi di token per parti di un controllo voce di elenco:Examples of a few token names for parts of a list item control:

- ListItem

- ListItemBorder

- ListItemMouseOver (Informazioni in base a ListItemMouseOver)

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabilitato

- ListItemDisabledBorder

  **Passo 2: Scegli le tonalità che l'elemento dell'interfaccia utente utilizzerà per ogni tema e il colore di sistema per Contrasto elevato.**

  Quando scegli colori personalizzati per l'interfaccia utente, seleziona un elemento dell'interfaccia utente esistente simile e usa i colori come base. I colori per gli elementi dell'interfaccia utente in-the-box sono stati sottoposti a revisione e test, in modo che avranno un aspetto appropriato e si comporterà correttamente in tutti i temi.

  **Passo 3: Utilizzare l'editor dei colori per creare nuovi token di colore.**

  Avviare l'editor colori e aprire o creare un nuovo file XML dei colori del tema personalizzato. Selezionare **Modifica > Nuovo colore** dal menu. Si apre una finestra di dialogo per specificare la categoria e uno o più nomi per le voci di colore all'interno di tale categoria:

  ![Nuovo colore dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Nuovo colore dell'editor dei colori VSIX")

  Selezionare una categoria esistente o selezionare **Nuova categoria** per creare una nuova categoria. Si aprirà un'altra finestra di dialogo, creando un nuovo nome di categoria:

  ![Nuova categoria dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nuova categoria dell'editor dei colori VSIX")

  La nuova categoria sarà quindi disponibile nel menu a discesa **Nuova categoria colore.** Dopo aver scelto una categoria, inserisci un nome per riga per ogni nuovo token di colore e seleziona "Crea" al termine:

  ![Nuovo colore riempito dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nuovo colore riempito dell'editor dei colori VSIX")

  I valori di colore vengono visualizzati in coppie di sfondo/primo piano, con "Nessuno" che indica che il colore non è stato definito. Nota: se un colore non ha una coppia colore/colore di sfondo del testo, è necessario definire solo lo sfondo.

  ![Valori di colore dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valori di colore dell'editor dei colori VSIX")

  Per modificare un token di colore, selezionare una voce di colore per il tema (colonna) di tale token. Aggiungere il valore del colore digitando un valore di colore esadecimale in formato ARGB a 8 cifre, immettendo un nome di colore di sistema nella cella o utilizzando il menu a discesa per selezionare il colore desiderato tramite un set di cursori di colore o un elenco di colori di sistema.

  ![Modifica del colore dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Modifica del colore dell'editor dei colori VSIX")

  ![Sfondo dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Sfondo dell'editor dei colori VSIX")

  Per i componenti che non devono visualizzare testo, immettere un solo valore di colore: il colore di sfondo. In caso contrario, immettere i valori per il colore dello sfondo e del testo, separati da una barra.

  Quando si immettono valori per Contrasto elevato, immettere nomi di colori di sistema di Windows validi. Non immettere valori ARGB hardcoded. È possibile visualizzare un elenco di nomi di colori di sistema validi selezionando "Sfondo: Sistema" o "Primo piano: Sistema" dai menu a discesa dei valori di colore. Quando si creano elementi con componenti di testo, utilizzare la coppia di colori di sistema di sfondo/testo corretta o il testo potrebbe essere illeggibile.

  Al termine della creazione, dell'impostazione e della modifica dei token di colore, salvarli nel formato xml o pkgdef desiderato. I token di colore che non hanno né uno sfondo né un set in primo piano verranno salvati come colori vuoti in formato .xml, ma eliminati in formato .pkgdef. Una finestra di dialogo ti avviserà di una potenziale perdita di colore se tenti di salvare i colori vuoti in un file .pkgdef.

  **Passaggio 4: Usare i colori in un'estensione di Visual Studio.Step 4: Use the colors in a Visual Studio extension.**

  Dopo aver definito i nuovi token di colore, includere il file con estensione pkgdef nel file di progetto con "Azione di compilazione" impostata su "Contenuto" e "Includi in VSIX" impostato su "True".

  ![File pkgdef dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "File pkgdef dell'editor dei colori VSIX")

  Nell'Editor colori estensione di Visual Studio scegliere File > Visualizza codice risorsa per visualizzare il codice utilizzato per accedere ai colori personalizzati nell'interfaccia utente basata su WPF.

  ![Visualizzatore del codice delle risorse dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Visualizzatore del codice delle risorse dell'editor dei colori VSIX")

  Includere questo codice in una classe statica nel progetto. Un riferimento a **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** deve essere aggiunto al progetto per utilizzare il tipo **ThemeResourceKey.**

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Ciò consente l'accesso ai colori nel codice XAML e consente all'interfaccia utente di rispondere alle modifiche del tema.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Passaggio 5: Testare le modifiche in Visual Studio.Step 5: Test the changes in Visual Studio.**

 L'editor dei colori può applicare temporaneamente i token di colore alle istanze in esecuzione di Visual Studio per visualizzare le modifiche in tempo reale ai colori senza ricostruire il pacchetto di estensione. A tale scopo, fare clic sul pulsante "Applica questo tema all'esecuzione di finestre di Visual Studio" che si trova nell'intestazione di ogni colonna del tema. Questo tema temporaneo andrà via quando l'Editor colori VSIX viene chiuso.

 ![Applicazione dell'editor dei colori VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Applicazione dell'editor dei colori VSIX")

 Per rendere permanenti le modifiche, ricompilare e ridistribuire l'estensione di Visual Studio dopo aver aggiunto i nuovi colori al file con estensione pkgdef e aver scritto il codice che utilizzerà tali colori. La ricompilazione dell'estensione di Visual Studio unirà i valori del Registro di sistema per i nuovi colori nel resto dei temi. Quindi riavviare Visual Studio, visualizzare l'interfaccia utente e verificare che i nuovi colori vengano visualizzati come previsto.

## <a name="notes"></a>Note
 Questo strumento è destinato a essere utilizzato per la creazione di colori personalizzati per i temi di Visual Studio preesistenti o per la modifica dei colori di un tema di Visual Studio personalizzato. Per creare temi di Visual Studio personalizzati completi, scaricare l'estensione Editor tema di colore di Visual Studio dalla raccolta di estensioni di Visual Studio.To create complete custom Visual Studio themes, download [the Visual Studio Color Theme Editor extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) from the Visual Studio Extensions Gallery.

## <a name="sample-output"></a>Output di esempio
 **Output del colore XML**

 Il file .xml generato dallo strumento sarà simile al seguente:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **Uscita colore PKGDEF**

 Il file .pkgdef generato dallo strumento sarà simile al seguente:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Wrapper per le chiavi di risorsa di C**

 Le chiavi delle risorse colore generate dallo strumento saranno simili alle seguente:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **Wrapper del dizionario risorse WPFWPF resource dictionary wrapper**

 Il colore ResourceDictionary chiavi generate dallo strumento sarà simile al seguente:The color **ResourceDictionary** keys generated by the tool will be similar to this:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
